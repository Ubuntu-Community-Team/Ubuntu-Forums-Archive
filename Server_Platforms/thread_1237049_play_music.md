---
title: "play music"
date: 2009-08-10
forum: Server Platforms
---

### Post by uge on 2009-08-10
Hi guys,

I run Ubuntu Server 64, 8.04 LTS.

My server has an audio card. I plugged the audio out jack into my phone system, so i can play music on my phone system (and so people hear music when on hold).

So I installed MPG123 and put files in a folder.

I figured if I start a SCREEN with MPG123 on loop, it would play endlessly.

In SCREEN, I issue the command
mpg123 --loop -1 -m *

but it only loops the first song !!

how can I loop the whole directory ?

any other app you might suggest that would let me do that ?

basically, i need a mp3 player with NO GUI, that consumes as few ressources as possible, and who will let me loop the content of a folder for infinity


thanks !!

---

### Post by cariboo on 2009-08-10
Randomplay works well for what you want to do. It is in the repositories, or just click the apt-url link.

[apt://randomplay](apt://randomplay)

---

### Post by uge on 2009-08-13
> **cariboo907 said:**
> Randomplay works well for what you want to do. It is in the repositories, or just click the apt-url link.

[apt://randomplay](apt://randomplay)

It does work but it won't loop !!!!

Let's say I have 10 MP3s in a dir.
I want a soft that will play the 10 songs in a loop forever !

If I just start a screen, load it there, and detach the screen, I want the songs to play forever and ever ;)

Can randomplay do that for me ? I couldn't find the options for that :S

---

### Post by uge on 2009-08-13
no one ?!?!?

there must be a lightweight no-GUI MP3 player for Ubuntu Server that allows to play a playlist in loop ?!?

PLEASE HELP !!

---

### Post by cariboo on 2009-08-14
You have to setup randomplayrc just copy it from /usr/share/randomplay to your home directory:

```
cp /usr/share/radomplay/randomplayrc /home/<user>/.randomplayrc
```

Then edit the file to tell it how mnany songs you want it to play and what to do once it has played all the songs.

---

### Post by uge on 2009-08-14
> **cariboo907 said:**
> You have to setup randomplayrc just copy it from /usr/share/randomplay to your home directory:

```
cp /usr/share/radomplay/randomplayrc /home/<user>/.randomplayrc
```Then edit the file to tell it how mnany songs you want it to play and what to do once it has played all the songs.

Nice ! but why copy it to my home directory ?

And also, I run it in screen mode from root, does that change anything?


Thanks !

---

### Post by uge on 2009-08-14
> **cariboo907 said:**
> You have to setup randomplayrc just copy it from /usr/share/randomplay to your home directory:

```
cp /usr/share/radomplay/randomplayrc /home/<user>/.randomplayrc
```Then edit the file to tell it how mnany songs you want it to play and what to do once it has played all the songs.


hmmm there's no "randomplay" subdir in my /usr/share/ :confused:

---

### Post by TwiceOver on 2009-08-14
Look up mpd (media player daemon).  That should be enough for what you want to do.  

If your server has apache installed, also look up phpmpd, a web front end for mpd that will allow you to change songs, volume, playlist, and other settings from a nice web interface.

---

