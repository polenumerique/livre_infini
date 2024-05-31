<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Histoire Aléatoire</title>
</head>
<body>
    <h1>Générateur d'Histoire Aléatoire</h1>
    <button onclick="generateStory()">Générer une Histoire</button>
    <div id="story"></div>

    <script>
        async function fetchFileContent(file) {
            const response = await fetch(file);
            const text = await response.text();
            return text.split('\n').filter(line => line.trim() !== '');
        }

        function getRandomSentence(sentences) {
            const randomIndex = Math.floor(Math.random() * sentences.length);
            return sentences[randomIndex];
        }

        async function generateStory() {
            const files = ['file1.txt', 'file2.txt', 'file3.txt'];
            let story = '';

            for (const file of files) {
                const sentences = await fetchFileContent(file);
                const randomSentence = getRandomSentence(sentences);
                story += randomSentence + ' ';
            }

            document.getElementById('story').innerText = story.trim();
        }
    </script>
</body>
</html>
