---
title: "Open-source multiplatform &quot;Just Dance&quot; game clone"
date: 2014-11-16
forum: Ubuntu Application Development
---

### Post by davidedepau1996 on 2014-11-16
Hello,
I'm looking for some people to help me develop a new project. As I said in the title it would be a "Just Dance" (by Ubisoft) clone.

For those who don't know what Just Dance is, it's a game where you have to dance while holding a controller in your right hand (e.g. a Wii remote, an Android/iOS application, I believe there's also an xbox version with Kinect support). You have to follow the dancer on the screen and mirror the movements. The game will then tell you how well you danced and give you a score based on the detected movements. You get stars based on your score (up to 5 I believe). There are also some "special"/golden movements that give you more points.
You can dance to popular songs included in the game, buy more online or use "music training", which is a long (up to 45 minutes) dancing session made up of chunks of other songs.
Up to 4 players can play at the same time: some songs have only one dancer so everybody has to follow the same dancer; some songs have multiple dancers so the player can pick one.

I think we can make a clone easily enough. This is my basic idea of the program's structure, including only the main parts:

Core:

[LIST]
[*]Interface
[*]Component that matches movement info in the song with the info received from the controllers and gives a score based on the match.
[*]Plug-in engine:
[LIST]
[*]Controller plug-ins:
[LIST]
[*]Dummy controller (for development, returns the maximum score)
[*]Wii remote (there are many libraries to manage them)
[*]Android application
[/LIST]

[*]Song repository plug-ins
[/LIST]
[/LIST]

However, in order to play the game we need the songs and the dancer's picture. Somebody will have to record a video of themselves while dancing to the song, tweak it so that it looks nice and you can't recognize who they are, then sync it to the song.
Then they'll import it to our "song developer" program which will connect to one of the previously mentioned controller plug-ins and record the movements to a file. The developer will then eventually add the lyrics and edit the metadata, pack everything up and publish it.

There is another problem, however: copyright. People will not want to dance only to open-source songs, they'll want to dance to popular songs too. That's why we need streaming support. We can implement it in two ways:
- We stream the official song from YouTube and play a local dancer video
- The song developer adds the song to the dancer video and uploads it to youtube with a standard youtube license; youtube will recognize the copyrighted song and add a "Buy this on iTunes" button somewhere in the website (that's what they call fair use). We'll stream that video.

Now the technical part: we can use Python + Cython as programming languages to develop the games. Python for the main parts and Cython for the things that require speed (the matching engine, the video player). This gives us better pluggability and multiplatform support. As UI framework we can use Kivy: it's easy to use, expandable, fast and *very* multiplatform (it supports GNU/Linux, Windows and Mac but also Android and iOS). However it lacks keyboard navigation support, which can however be added as it has keyboard handlers that I regularly use to manage the back button on my android apps.

What do you think? Let me know your opinions and if you want to help me. I don't want to start it alone because it's a very big project and I can't do it alone.
I'll be really glad however to work on it with a small community :)

---

