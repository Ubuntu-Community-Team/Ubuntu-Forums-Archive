---
title: "flaky DVD playback"
date: 2008-07-19
forum: System76 Support
---

### Post by eyecreate on 2008-07-19
I have been trying to play a DVD in VLC on my serp4 laptop. I am able to play it in VLC on my desktop(32 bit ubuntu) but not my laptop. It will not read the DVD menu, but will play the main disk for about 5mins before stopping. VLC's output is:
> VLC media player 0.8.6e Janus
[00000306] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
[00000300] dvdread demuxer error: read failed for 3/4 blocks at 0x5dc72
[00000289] main playlist: nothing to play

Totem and other players will either not play or will have the same/similar behavior. (depends if it reads the menu or not)

---

### Post by SunnyRabbiera on 2008-07-19
What other DVD apps have you tried?
and are you sure you got all the plugins?
I know that some DVD's have issues, but its not linux to blame.

---

### Post by eyecreate on 2008-07-19
So far, all other DVD's i've played(I think only 2) have played on my laptop fine. I have tried totem, mplayer, gxine, vlc. I should have everything installed, as I went through thre process of enabling DVD playback. I just don't know why it won't work on my laptop.

---

### Post by thomasaaron on 2008-07-21
OK, Here is how I just got perfect DVD playback. This is on a fresh install of Hardy 64-bit, on a GazV5. Run these commands from a terminal.

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/ap/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

sudo apt-get install vlc libdvdcss2 ubuntu-restricted-extras w64codecs

sudo apt-get install totem-xine

sudo update-alternatives --config totem
```

choose 2 for xine-totem

---

### Post by jack8888 on 2009-07-13
I'm a novice and therefore not sure, but this doesn't seem to solve my problem. I'm not trying to burn anything. What I want to do is copy (rip?) DVDs to a remote hard disk, and play them from *there*.  My problem is that I can't find anything that will play them from hard disk.  [plus size lingerie](http://www.pamperedpassions.com/plus_size_lingerie_55_ctg.html) [guitar lesson dvd review](http://www.bestguitardvds.com) Having said all that, I'm unsure if my problem is due to 123 COPY not producing playable files, or due to the fact that none of the players I've tried thus far are capable of playing what it's produced.

---

### Post by thomasaaron on 2009-07-13
You can burn them to your hard disk as an .iso file. Then you can install VLC media player, which can play an .iso file.

---

