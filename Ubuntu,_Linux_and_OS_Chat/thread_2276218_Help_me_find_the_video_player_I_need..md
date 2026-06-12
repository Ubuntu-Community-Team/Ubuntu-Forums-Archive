---
title: "Help me find the video player I need."
date: 2015-05-01
forum: Ubuntu, Linux and OS Chat
---

### Post by DanielWEWO on 2015-05-01
Hey guys. I need a video player that allows me to create a playlist of videos, and create a bookmark in that playlist, so that I can jump to the right video at the right time. If it jumps to the place I was when I close the program, that is fine. If it allows me to create custom bookmarks, open the playlist, and jump to that spot, that is also fine. I have tried Gnome videos(the default for Ubuntu 14.04), VLC (there is a bookmark option, but apparently it is broken :/), banshee, and kaffeine. I may not have actually found out how to do it in banshee or kaffeine, but I could not figure out how. If you guys have a recommendation it would be awesome!

---

### Post by Quarkrad on 2015-05-01
I find SMPlayer a very good player, it also has a Favorites icon - download it and see how near it meets your needs.

---

### Post by DanielWEWO on 2015-05-05
I tried out SMPlayer and its definitely a step in the right direction! If I open up the same video it remembers my position in the video. Unfortunately, it doesn't seem to remember position or video when I have a playlist of videos. So, I have switched over to SMPlayer until I find something that does what I need. I've always wanted to write my own media player to do exactly what I want. I am a pretty decent Python coder, but I've never looked into writing something like that, I'm guessing it is quite an involved process.

---

### Post by Bucky Ball on 2015-05-05
Well, it is open-source software. There is nothing stopping you from downloading the code of an existing player and tweaking with that until you get what you want ... :-k ;)

---

### Post by DanielWEWO on 2015-05-05
Also possible. I wonder if I could figure something like that out. I'll have to give it a shot in my free time.

---

### Post by SeijiSensei on 2015-05-06
You'd have to save the information in a file separate from the playlist, since I don't see anything in the [m3u playlist format]("http://en.wikipedia.org/wiki/M3U") that lets you specify positions.  It's basically just a list of files.

---

### Post by DanielWEWO on 2015-05-11
And that makes sense as to why most players don't implement it. There are a lot of other playlist formats too. I'm not sure if those allow for something like that. I think SMPlayer is going to suffice for now. Thanks for helping me out guys!

---

### Post by Bucky Ball on 2015-05-12
Please mark the thread as solved if you're satisfied. This won't close the thread, discussion can continue, but it will help future travelers. ;)

Please see the second link in my signature for how. Good luck.

---

### Post by mastablasta on 2015-05-12
well the one in Kodi (aka XBMC, aka OpeneELEC) definitely has a resume option. not sure when it is triggered, but I know sometimes we would see a movie only to find out we are sleepy. turn it off and resume the next day (it asks you if you want to start from beginning or resume). I also has playlists, bookmarks, but so far I haven't had any use for those.

---

### Post by Bucky Ball on 2015-05-12
> **mastablasta said:**
> well the one in Kodi (aka XBMC, aka OpeneELEC) definitely has a resume option. not sure when it is triggered, but I know sometimes we would see a movie only to find out we are sleepy. turn it off and resume the next day (it asks you if you want to start from beginning or resume). I also has playlists, bookmarks, but so far I haven't had any use for those.

Yep, Kodi resumes from where I left off for me too, as did Xbmc prior to that.

---

### Post by DanielWEWO on 2015-05-14
> **Bucky Ball said:**
> Please mark the thread as solved if you're satisfied. This won't close the thread, discussion can continue, but it will help future travelers. ;)

Please see the second link in my signature for how. Good luck.


Hmm, well I attempted to do that, unfortunately I'm not able to. I don't know if Ubuntuforums has changed things lately, but I've attached a screenshot showing that I am logged in, and I do not have the option to mark the thread as solved :([ATTACH=CONFIG]261967[/ATTACH]

---

### Post by benrob0329 on 2015-05-15
you could create a front end for Mplayer, or VLC using the VLC Python bindings.

[https://wiki.videolan.org/Python_bindings/](https://wiki.videolan.org/Python_bindings/)

---

### Post by Bucky Ball on 2015-05-16
> **DanielWEWO said:**
> Hmm, well I attempted to do that, unfortunately I'm not able to. I don't know if Ubuntuforums has changed things lately, but I've attached a screenshot showing that I am logged in, and I do not have the option to mark the thread as solved :([ATTACH=CONFIG]261967[/ATTACH]

Odd. May be my mistake. As this is in a chat/non-support section of the forum, perhaps there is no 'solved' option as a chat can't really be 'solved'. Just a theory, but I'll look into it. Thanks for pointing that out. ;)

* Update: Yep, that's it. Just checked in a support area and nothing wrong with the 'Solved' function. Must be because it is here, so disregard, as you were and carry on. ;)

---

### Post by DanielWEWO on 2015-05-18
That definitely makes sense Bucky. benrob nice find! I didn't know VLC had a native python version with the full API available! This is probably what I'll end up doing.

---

