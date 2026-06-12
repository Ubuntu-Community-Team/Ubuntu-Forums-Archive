---
title: "Partitioning (160gb+80gb,raid0); Radeon x1600; Optimizing for Media Server"
date: 2013-09-19
forum: Server Platforms
---

### Post by georges-langlois on 2013-09-19
Hello, 

I have an old pc configuration here which I've been trying to get the maximum of it to run as a media server (and maybe for web development server)

The config is the following:
Pentium 4 2.53GHz
2,5 GB Ram
ATI Radeon x1600 256gb
HD Maxtor (very old) 7200rpm 160gb
HD Samsung 7200rpm 80gb

I don't know if it possible to play 1080p movies without stuttering with this config. At the moment, I have installed Ubuntu 12.04. with a crazy partition configuration, running ATI opensource drivers. I've tested PS3 Media server, Universal Media Server and Serviio. 
For some reason I couldn't make Serviio work properly... I can't see the video files or any file on the DLNA device (Panasonic TV). PMS and UMS works, but 1080p is suttering a lot and 720p is stuttering a little. Already tested different codecs.
[COLOR=#000080]**So, I'd like to ask what would be the best media server option for this configuration? I could run movies on the fly but my main concerning is subtitles. I'm in a infinite research for the best way of playing 3D movies with subtitles (heard about 3D subtitle and Wild Media Server but didnt test yet). So, for using subtitles I think I'll need some transcoding, is that correct?**[/COLOR]

I've used Ubuntu 12.04 Alternative install in order to set raid drives as I've seen in some tutorials. So, I didn't know very well what to do because they've always used identical HDs so I've set like this:
From Samsung I've reserved 79gb for raid0 and 1gb for swap
From Maxtor I've reserved 79gb for raid0 and 1gb for swap and formated as ext4 the rest of it.
It's a mess, I know.. But i've done just for a test since I've read raid need identical sizes and I didnt want to loose the rest of 80gb in Maxtor. 
In a first moment, when I was reading about raid0 , I couldn't make it work  by hardware with my Asus p4s8x-x, but both HDs are connected in a dedicated IDE plug yet (not sure if it helps). I've done ubuntu benchmark tests in each of the drivers:
[SIZE=1]Maxtor - Average Read: 61,4Mb/s ; Average Access Time: 15,4m/s
Samsung - Average Read: 49,8Mb/s ; Average Access Time: 13,2m/s
RAID - Average Read: 92,4Mb/s ; Average Access Time: 12,5m/s[/SIZE]
[COLOR=#000080]**So my second question regards the HDs configuration. What would be the best partitioning config? I don't care about redundancy. I'd like to have all merged (as one HD but one partition for SO and another for files) and with maximum perfomance.**[/COLOR]

I didn't know that alternate install would provide a desktop installation. At least, it came with gnome.
[COLOR=#000080]**So my third  question regards the optimization of ubuntu for media servers. I've already disabled several services from init but I'd like to know everything I can disable or do in the system to improve perfomance, including disabling gnome and let it boot in console.**[/COLOR]
Also, all those updates appearing for me (79), should I install all of them?

With some research I realized that I'd have to [downgrade the ubuntu version to xorg 1.12 if I want to install the ATI driver provided in their website]("http://www.ubuntugeek.com/how-to-install-amd-catalyst-legacy-drivers-in-ubuntu-12-10-quantal.html"). [B][COLOR=#000080]
But, I'd like to know if I loose perfomance using only the opensource driver since my main goal is the Media Server.[/COLOR][/B]


I really thank you in advance if you can provide some light to my doubts.

---

### Post by whitesmith on 2013-09-19
I'm a little confused by your post. For example, you state "With some research I realized that I'd have to downgrade the ubuntu version to xorg 1.12 if I want to install the ATI driver provided in their website." But xorg 1.12 is not an Ubuntu version. Are you trying to wipe your PC and reinstall Ubuntu for maximum performance? Without knowing things like this I can't help you.

---

### Post by Bucky Ball on 2013-09-19
*Thread moved to **Server Platforms.***

Welcome. Your post might more productive if you split the three questions into three separate threads as each question doesn't have much to do with the others.

Wondering why you didn't install Ubuntu Server Edition ... depending on how you're communicating with the server, if remotely, you won't need the ATI driver anyway as you'll have no monitor attached. :-k

---

### Post by georges-langlois on 2013-09-19
> **whitesmith said:**
> Are you trying to wipe your PC and reinstall Ubuntu for maximum performance? Without knowing things like this I can't help you.

Yes, I want to go with a clean installation and I don't care wiping. THe pc has no data.

> **Bucky Ball said:**
> *Thread moved to **Server Platforms.***

Welcome. Your post might more productive if you split the three questions into three separate threads as each question doesn't have much to do with the others.

Wondering why you didn't install Ubuntu Server Edition ... depending on how you're communicating with the server, if remotely, you won't need the ATI driver anyway as you'll have no monitor attached. :-k

Yes, no problem. I was thinking on moving the graphics card and media server questions to *[Multimedia & Video]("http://ubuntuforums.org/forumdisplay.php?f=334"), *HD questions to *Hardware* and optimization question to *[COLOR=#4E4E4E] [/COLOR][Installation & Upgrades]("http://ubuntuforums.org/forumdisplay.php?f=333")*?
May I ask to delete this post after I do this?

Yeah I thought on server edition, but at first I burnt the desktop edition and then with the tutorials for Raid0 I've burnt the alternative edition thinking I could have something similar to the server and more customizable. Then I've been reading it was easy to "transform" desktop into server edition managing the packages since they're pretty much the same.

---

### Post by Bucky Ball on 2013-09-19
No need to delete this one. You could edit down this one to be about your main questions, copy/paste two of the questions into new threads and I can change the name of this one if you like. Post a couple of new name suggestions if you want it changed.

---

### Post by georges-langlois on 2013-09-26
> **Bucky Ball said:**
> No need to delete this one. You could edit down this one to be about your main questions, copy/paste two of the questions into new threads and I can change the name of this one if you like. Post a couple of new name suggestions if you want it changed.

I've created two other threads

[Optimization for Media Server]("http://ubuntuforums.org/showthread.php?t=2176927")

[Partitioning (160gb+80gb,raid0)]("http://ubuntuforums.org/showthread.php?t=2176928")

You can delete this one if you be so kind

Thanks!

---

### Post by Bucky Ball on 2013-09-26
Your thread here:

[http://ubuntuforums.org/showthread.php?t=2176927](http://ubuntuforums.org/showthread.php?t=2176927)

... has been closed by another mod as it is a duplicate of this one. I will leave this one open.

---

