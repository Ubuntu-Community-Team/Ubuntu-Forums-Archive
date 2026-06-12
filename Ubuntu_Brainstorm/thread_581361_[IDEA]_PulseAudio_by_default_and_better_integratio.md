---
title: "[IDEA] PulseAudio by default and better integration for USB audio devices"
date: 2007-10-19
forum: Ubuntu Brainstorm
---

### Post by groggyboy on 2007-10-19
Okay, so this is actually two ideas, but they are related.  First, i think that ubuntu should replace ESD with PA.  it's a far superior sound system, albeit with some issues at the moment.

second, and this is even more important if ubuntu doesn't move to PulseAudio: ubuntu needs to put some work in to how it handles usb audio devices.  it would be nice if i could just plug my speakers in and have them automatically used by the system.  right now, i have to go in to sound preferences and set them as default, and even then some programs won't use them.  not only that, but the volume control applet has to be changed by hand as well.  the multimedia keys don't work at all with my external speakers, and i can't find a way to fix that to my satisfaction.  these problems are present in gutsy, and have been around since edgy (and maybe earlier - but i think dapper may have handled audio better).

i think ubuntu should put some serious effort in to how it handles sound and sound devices in this next release.  anyone else with me?

---

### Post by Corbelius on 2007-10-19
+1 to Pulseaudio.

---

### Post by aamukahvi on 2007-10-20
I'm with PulseAudio.

---

### Post by fnjordy on 2007-10-20
Pulse 0.9.7 with the result of the work of Fedora Core 8 is going to be the big change here.

There's an Ars article on the topic too:

[http://arstechnica.com/journals/linux.ars/2007/10/17/pulseaudio-to-bring-earcandy-to-linux](http://arstechnica.com/journals/linux.ars/2007/10/17/pulseaudio-to-bring-earcandy-to-linux)

---

### Post by Zdravko on 2007-10-20
+1.

---

### Post by amano on 2007-10-28
Hmm. There seems to be a blueprint for hardy already: [https://blueprints.launchpad.net/ubuntu/+spec/pulseaudioserver](https://blueprints.launchpad.net/ubuntu/+spec/pulseaudioserver)

---

### Post by booljayj on 2007-10-31
I tried Pulse Audio in the past and it was too buggy, but if it were better integrated this would totally be the way to go. It's got my support, that's for sure.

---

### Post by lariamat on 2007-11-01
PulseAudio is the future. 
I already use pulseaudio in Gutsy (from the regular repository) every day. I only had a flash problem in the beginning that I was able to fix with libflashsupport.
Great application!

---

### Post by pay on 2007-11-02
Will pulseaudio integrate with kde? Also I think that I read that Gnome will eventually crossover to pulseaudio...

---

### Post by 23meg on 2007-11-02
PulseAudio is very likely to be used in Hardy.

[https://lists.ubuntu.com/archives/ub...er/002169.html](https://lists.ubuntu.com/archives/ub...er/002169.html)

---

### Post by shad0w_walker on 2007-11-02
I can only but agree with pulse audio as the default. But first, it has to be very carefully tested. I have tried about 4 times now to get it installed and working, every time the biggest hurdle was Amarok.

I installed pulse, even got flash working but when i played in Amarok and tried pausing or unpausing the track every thing would pretty much freeze solid and take about 7-8 seconds for it to response.

---

### Post by Centx on 2007-11-05
+1 for pulseaudio any day, just tested 0.9.6 from repos, and that went surprisingly well. Only thing was that it crashed Enemy Territory: Quake Wars demo =/

---

### Post by hanzomon4 on 2007-11-13
+1 for pulseaudio, it kicks *** on fedora 8. I finally got a master channel for my M-Audio Delta 66(ice1712), one for playback and capture. It just works and I love it :-D

---

### Post by j_g on 2007-11-14
I vote thumbs down for Pulse Audio. I have some basic, important reservations about the stability and usability of Pulse Audio which I detail in this thread:

[http://ubuntuforums.org/showthread.php?t=612606](http://ubuntuforums.org/showthread.php?t=612606)

---

### Post by qamelian on 2007-11-15
> **j_g said:**
> I vote thumbs down for Pulse Audio. I have some basic, important reservations about the stability and usability of Pulse Audio which I detail in this thread:

[http://ubuntuforums.org/showthread.php?t=612606](http://ubuntuforums.org/showthread.php?t=612606)

It's coming sooner or later whether you want it or not. The Gnome devs already have a plan in place to completely replace esd with Pulse Audio. The only issue I have with it right now is that you need to do a lot of tweaking to get it working everywhere. Once it becomes a standard part of the distro though, all of that tweaking will be done in advance.

Personally, I love it. It offers a much more powerful and flexible audio environment than esd.

---

### Post by amano on 2007-11-16
ESD must die. I welcome any alternative. Thus :thumbs up:

---

### Post by zolookas on 2007-11-17
+1

---

### Post by amano on 2007-11-17
It seems that pulseaudio 0.9.7 hit main now: [https://lists.ubuntu.com/archives/hardy-changes/2007-November/001738.html](https://lists.ubuntu.com/archives/hardy-changes/2007-November/001738.html)

---

### Post by Gorbayov on 2007-11-23
pulseuaudio is very good...
i just have a little delay when starting some audio( i cant hear the first half second or something like that)
part from that i like it alot..


the one with the problem with Amarok, i had the same problem
try to config amarok to use alsa
and set alsa device to pulse instead of default or hw:0 or what ever
this works for me, no problem with amarok

and the one that asked if PA works in KDE, yes it does work very well (just turn off arts)

---

### Post by boteeka on 2007-11-23
+1 to Pulseaudio.

I have installed from the repo (0.9.6) and I'm using it actively but not without problems. Every time I boot up Gutsy I need to kill pulsaudio and restart it manually. If I don't do that the pitch (tempo?, speed?) of my sound is  screwed up.

Anyway, 0.9.8 is out now, anyone aware of a gutsy package of this release? I would love to try it out, maybe it solves my problems.

---

### Post by Ekeluo on 2007-11-24
I had pulse audio installed some time ago but that killed alsa and oss and I saw NO way of enabling them anywhere. If you guys can fix it and really believe it's better, cool. Otherwise having to install esd plugins for all my media players (vlc, amarok?) is kind of a bother.

---

