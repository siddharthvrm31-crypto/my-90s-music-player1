<!DOCTYPE html>
<html>
<head>

    <title>My 90s Music Player</title>

    <style>

        body {
            margin: 0;
            background: #17112b;
            color: white;
            text-align: center;
            font-family: Arial, sans-serif;
            padding-top: 50px;
        }

        .player {
            width: 520px;
            max-width: 85%;
            margin: auto;
            padding: 35px 25px;
            background: #2a2044;
            border: 4px solid #8d6bb3;
            border-radius: 25px;
            box-shadow: 0 0 25px #000;
        }

        h1 {
            font-size: 34px;
            margin-bottom: 5px;
        }

        .subtitle {
            color: #c9b8dd;
            font-size: 14px;
            margin-bottom: 30px;
        }

        .cassette {
            width: 300px;
            height: 170px;
            margin: 20px auto;
            background: #555;
            border-radius: 15px;
            border: 5px solid #888;
            position: relative;
        }

        .label {
            position: absolute;
            left: 35px;
            right: 35px;
            top: 25px;
            height: 80px;
            background: #ddd;
            color: #222;
            border-radius: 5px;
            padding-top: 10px;
            font-weight: bold;
        }

        .reel {
            position: absolute;
            width: 45px;
            height: 45px;
            background: #222;
            border: 7px solid #aaa;
            border-radius: 50%;
            bottom: 20px;
        }

        .left-reel {
            left: 50px;
        }

        .right-reel {
            right: 50px;
        }

        #songName {
            font-size: 25px;
            font-weight: bold;
            margin: 25px;
        }

        audio {
            width: 280px;
        }

        button {
            background: #eee;
            color: #17112b;
            border: none;
            border-radius: 50px;
            font-size: 18px;
            padding: 14px 20px;
            margin: 5px;
            cursor: pointer;
            font-weight: bold;
        }

        button:hover {
            transform: scale(1.08);
        }

        .footer {
            margin-top: 25px;
            color: #a99ab8;
            font-size: 12px;
        }

    </style>

</head>

<body>

<div class="player">

    <h1>📻 My 90s Music Player</h1>

    <div class="subtitle">
        OLD SONGS • GOOD MEMORIES
    </div>

    <div class="cassette">

        <div class="label">
            🎵 MY 90s MIX 🎵
        </div>

        <div class="reel left-reel"></div>

        <div class="reel right-reel"></div>

    </div>

    <p id="songName">🎵 Haule Haule</p>


    <audio id="song1" controls>
        <source src="songs/song1.mp3.mp3" type="audio/mpeg">
    </audio>


    <audio id="song2" controls style="display:none;">
        <source src="songs/song2.mp3.mp3" type="audio/mpeg">
    </audio>


    <audio id="song3" controls style="display:none;">
        <source src="songs/song3.mp3.mp3" type="audio/mpeg">
    </audio>


    <br><br>


    <button onclick="back()">⏮️ Back</button>

    <button onclick="playPause()">▶️ Play / Pause</button>

    <button onclick="forward()">⏭️ Forward</button>


    <div class="footer">
        🎶 Playing memories, one song at a time 🎶
    </div>

</div>


<script>

    var currentSong = 1;


    function getPlayer() {
        return document.getElementById("song" + currentSong);
    }


    function playPause() {

        var player = getPlayer();

        if (player.paused) {
            player.play();
        } else {
            player.pause();
        }

    }


    function showSong(number) {

        document.getElementById("song1").style.display = "none";
        document.getElementById("song2").style.display = "none";
        document.getElementById("song3").style.display = "none";

        document.getElementById("song" + number).style.display = "inline";


        var names = [
            "",
            "🎵 Haule Haule",
            "🎵 Sanam Teri Kasam",
            "🎵 Ek Number"
        ];


        document.getElementById("songName").innerHTML =
            names[number];

    }


    function forward() {

        getPlayer().pause();

        currentSong++;

        if (currentSong > 3) {
            currentSong = 1;
        }

        showSong(currentSong);

        getPlayer().currentTime = 0;

        getPlayer().play();

    }


    function back() {

        getPlayer().pause();

        currentSong--;

        if (currentSong < 1) {
            currentSong = 3;
        }

        showSong(currentSong);

        getPlayer().currentTime = 0;

        getPlayer().play();

    }


    document.getElementById("song1").onended = function() {
        forward();
    };


    document.getElementById("song2").onended = function() {
        forward();
    };


    document.getElementById("song3").onended = function() {
        forward();
    };

</script>

</body>
</html>
