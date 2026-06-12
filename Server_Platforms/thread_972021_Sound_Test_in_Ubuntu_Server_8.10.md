---
title: "Sound Test in Ubuntu Server 8.10"
date: 2008-11-05
forum: Server Platforms
---

### Post by AngelBreath on 2008-11-05
Hi everyone,

I setup an ubuntu server 8.10 for my business needs and i can tell that i m very happy that everything works perfect with the first try. Files are shared with Windows XP, Apache,MySQL , everything works perfect. I installed webmin that is a fantastic tool to work with.
 As i m new in Linux the only problem i have is that i want my server playing music.Nothing special, just play mp3 to have music in my business.
 And here is the part i get lost...:) How can i test if my sound card is installed, and what program should i install as mp3 player?

 Thanks in advance for the help.

---

### Post by baudday on 2008-11-05
Why don't you just let people stream the music to their computers instead of playing it from the server?

---

### Post by AngelBreath on 2008-11-06
Good point, but imagine that its a retail store.So i want the music for the customers..:) Nothing special at all , 50 songs playing shuffle all day. In Server 2003 i used winamp for this. I want something similar, but first i want to check IF i have a sound card properly installed.

---

### Post by AngelBreath on 2008-11-06
Actually i installed mplayer and i can play mp3 songs from terminal. The only problem now is that i dont have sound, so i need to see if my sound card is installed and how to work with volume.
 lspci  give me  :AC '97 sound controler (rev a0). Not sure if that means it is installed. And how to volume up and down with no GUI?

---

### Post by AngelBreath on 2008-11-06
I managed everything to work ok. So to be fair i ll post here the solution.

 ```
lspci
```

My sound card was there so i guessed that Ubuntu had installed it.

```
sudo apt-get install alsa-utils
```

This installed ALSA utils.

```
alsamixer
```

This started a small gui that can volume adjust ,check channels, check card etc.

```
~/mplayer *.mp3
```

Music from my server to the speakers...:)

---

