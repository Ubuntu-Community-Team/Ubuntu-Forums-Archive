---
title: "Gnump3d and video (.avi)"
date: 2010-02-08
forum: Ubuntu Studio
---

### Post by LiquiD_85 on 2010-02-08
Hi to all,

first of all i don't know if i'm in the right section :D sorry in advance :D

I've a problem with gnump3d, it's work like a sharm with mp3s files but it ask me to download .avi files instead streaming theese!!
I'm using ubuntu server 8.04.3 LTS and gnump3d 3.0 (from repository)!
Someone can help me?

Thanks!

---

### Post by tgalati4 on 2010-02-08
If you are using Firefox, then you might need a multimedia player extension.  Firefox doesn't know how to handle *.avi unless you tell it what player to use.

Search for mediaplayer or mediaplayerconnectivity in Firefox-->tools-->Add-ons-->Get Add-ons

Install vlc if you haven't already.

---

### Post by LiquiD_85 on 2010-02-09
Hi tgalati4,

thank you for your answer; mediaplayer connectivity allow me to play only songs!!!
When i browse gnump3d with firefox it ask me to download .avi files, if i browse with IE it open Windows Media Player but it starts to buffer the file (i see the progress bar filling) and i have to wait about 2 minutes (in LAN).
Seems media player are downloading the entire file!!
My question is, clients have to download only the .m3u file also with movies files??
I've to install some codec in ubuntu server or other software e.g. ffmpeg???
Thank you!!!

---

### Post by LiquiD_85 on 2010-02-09
*UPDATE*

I've inserted some .mpg .mov and .wmv (about 2-300 kb each) and with IE the streaming is working, it open windows media player and starts to playing movie, i see the progress bar filling but also the "time bar" is scrolling and movies are played!!!

Why with video .avi (about 500-100 MB) don't work?

Thanks!

Correction: .mpg starts and end immediatelly!!! :(

***UPDATE***

I understand that only .wmv are really streaming other will be downloaded first!

---

### Post by LiquiD_85 on 2010-02-09
I discover a strong but good thing ... if i click on the "info" link near the movie and a click on the "Play Track" link it download the .m3u file and i can STREAM ALL type of movies (avi wmv mov mpeg) with ALL player and browser i want (IE Firefox with WMP or vlc)
It's normal???

---

### Post by tgalati4 on 2010-02-09
The *.m3u file is a playlist file.  When you play that in the various linux players, they know how to handle the content--and it streams as predicted.

When you click on the actual *.avi file, firefox and the other players seem to want to download it completely versus buffer and play.  I don't know why.  Search launchpad.net for bugs against the different players that you are using and see if others are having the same problem.  

I use gnump3 extensively, but only for audio files.  I haven't experienced your issue.  Sorry I can't help any more than that.

---

### Post by LiquiD_85 on 2010-02-10
Thank you for your help, for now seems to work just click on "info" link of the interested movie and then "Play Track", in windows and linux!!!

thank you!

---

