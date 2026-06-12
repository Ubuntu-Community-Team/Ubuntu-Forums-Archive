---
title: "MP3 player with no GUI ?"
date: 2009-06-08
forum: Server Platforms
---

### Post by uge on 2009-06-08
Hi guys !!

I've got Ubuntu Server LTS 8.04, 64 bits architecture, without (of course) any GUI.

I'm looking for an MP3 player that does not have a GUI either.

So you know what I'm trying to do, here's the context :
My server (running Ubuntu) is installed in a room, just next to the telephone system.
There's an audio jack from the telephone system that can be connected to anything to play music so people hear that music while "on hold".
Right now it's plugged in a MP3 player that I need to recharge sometimes... I figured I could plug it in the audio card of the server !!! 

So that's why I need a really, really simple, lightweight, MP3 player that would auto start when the server boots, and simply play in loop files in a directory for exemple...

So whenever I reboot, the player autoloads and autoplays...
And so I can just dump MP3s in a folder, and they will play eventually.


Any idea of a software that could do that for me ?



PS : I'm still a newbie in linux so don't get too complicated with me #-o

---

### Post by boof1988 on 2009-06-08
One choice would be...

```
mplayer-nogui
```

I think that it could do what you want.  But it may take some creation/?editing? of some config files.

I have used it to just play some music located on the server as well as play some streaming-radio.

There are other players that are audio only players.  But I like the way mplayer-nogui performs while playing audio files and streaming audio.  It gives a lot of feedback so that I can see what is going on.

Hope this helps you a bit.

References:
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=mplayer-nogui](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=mplayer-nogui)
[http://linuxappfinder.com/package/mplayer-nogui](http://linuxappfinder.com/package/mplayer-nogui)
[http://debian-multimedia.org/dists/testing/main/binary-ia64/package/mplayer-nogui.php](http://debian-multimedia.org/dists/testing/main/binary-ia64/package/mplayer-nogui.php)

---

### Post by meho_r on 2009-06-08
Xmms2?

---

### Post by TwiceOver on 2009-06-08
You are looking for MPD.  There are also some PHP frontends for it that will allow you to create play lists and change songs from a browser (assuming you have Apache+PHP installed).

I do something similar for a radio transmitter I have in the house.

---

### Post by tgalati4 on 2009-06-08
moc

---

### Post by Villiam on 2009-06-08
Vlc media player is cool. All you have to do is just install it with sudo apt-get install vlc then run it with vlc -I ncurse.

[ubuntu]("http://www.linux-archive.org/ubuntu-user/")

---

### Post by cariboo on 2009-06-08
I use a combination of mpg321 and randomplay in my shop on an old AST Bravo connected to a Harmon Kardon amplifier to play tunes. I have a little over 10,000 mp3's, and I hate hearing repeats so I have setup randomplay not to repeat anything for 30 days. Mpg321 and randomplay are in the repositories.

---

### Post by bear24rw on 2009-06-08
if you install vlc you can also use cvlc which is the command line version

---

### Post by glotz on 2009-06-08
[quote=twiceover]mpd[/quote]

[quote=tgalati4]moc[/quote]

[quote=cariboo907]mpg321 and randomplay[/quote]

+1

---

