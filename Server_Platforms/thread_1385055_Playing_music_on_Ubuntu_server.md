---
title: "Playing music on Ubuntu server"
date: 2010-01-19
forum: Server Platforms
---

### Post by glethro on 2010-01-19
Currently I have ubuntu server 9.10 set up on a Shuttle Xpc hosting a small video on demand website so that the family can watch whatever from where ever. However, I would like to hook it up to the speaker system so that I can remotely control what music is being played.

I've tried googling around and reading how-to's but I can't seem to find how to set up audio playback on ubuntu server edition. 

**lspci | grep Audio**
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

```
**One error I get when using cmus to play a file is:**
```
Error: opening audio device: No such file or directory
```

---

### Post by Adina on 2010-01-19
you can try sudo apt-get install mp3blaster

There are many more music players for command line I'm sure.

---

### Post by gobbledigook on 2010-01-19
If you want the music to be streamed over your network then there is no need to work out how to get your sound working locally :)

If you want to play sound locally using say a laptop as the remote control or play using TV as an interface with sound going to a local amp / speakers then these are other issues. it would probably help to install the sound modules... plus then you will need alsa + alsa-mixer, however these didn't work for me! I run a local file-server using XBMC as a front-end for playing music and video though my telly/amp - so i had to use oss4 and set it to emulate pulse audio (XBMC uses pulse audio).

I know this sounds complicated... and it is! but that is because sound issues don't get a huge amount of attention over here, I mean why would you want to be able to play sound from you bank of servers?? its kinda set up for large installations not the home user. 

I posted here and on teh XBMC forums over sound issues and got little response.. but i have linked below my threads so you can glean what help you can from them :)

[http://ubuntuforums.org/showthread.php?t=1292977](http://ubuntuforums.org/showthread.php?t=1292977)

I'll have to do an edit when i get home as the xbmc forums are blocked from my office!!!

---

### Post by R.Bucky on 2010-01-21
I have used Jinzora in the past as a web-based streaming media server. Additionally, I ran a small headphone speaker wire through a custom wallplate, under my home, and input to my stereo. Options, options...

---

### Post by glethro on 2010-01-24
Streaming over the network is not the problem. Its playing the sounds locally on the server. I would like the sound to play through the speakers connected to the server. 

One solution i did find was to install OSS. However, i cant seem to set this as the system default so i have to manually configure applications like mplayer.

Is there some way to get alsa or pulse audio 2 work on a ubuntu server?

---

