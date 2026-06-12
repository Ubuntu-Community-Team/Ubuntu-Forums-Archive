---
title: "Could OHPHONE replace SKYPE for Linux?"
date: 2009-11-22
forum: The Cafe
---

### Post by frenchn00b on 2009-11-22
OHPHONE is a backend for VOIP. It has good quality sound.
(requires libpt-plugins-oss )


**Hence could OHPHONE replace on day SKYPE for Linux?**
OHPHONE is LINUX GNU, free.

---

### Post by Psumi on 2009-11-22
That is like saying HTML5 will replace flash, and we know that will not happen.

---

### Post by frenchn00b on 2009-11-22
> **Psumi said:**
> That is like saying HTML5 will replace flash, and we know that will not happen.

I do not think so. Linux do not like SKYPE, because it is not GNU, no source code. 
A backend for VOIP, I am sure that lot of Linux - fans would like it. ;)

---

### Post by NoaHall on 2009-11-22
I have one word for you. ekiga.

---

### Post by frenchn00b on 2009-11-22
> **NoaHall said:**
> I have one word for you. ekiga.

Ekiga is medium to good. The echo is terrific, and the ekiga program has no backend. But well ... :( ohphone would be more the future. You could even tunnel via SSH your talkign ;)

---

### Post by Psumi on 2009-11-22
> **frenchn00b said:**
> I do not think so. Linux do not like SKYPE, because it is not GNU, no source code. 
A backend for VOIP, I am sure that lot of Linux - fans would like it. ;)

flash is closed source too and not GNU.

---

### Post by frenchn00b on 2009-11-22
Sorry it is in german. 
it means taht it is the command
```
ohphone –aln
```
and for video:
```
ohphone –aln –-videotransmit –-videodevice
/dev/video –-videoinput 1
```

```
6.4.4 OHphone Command-Line Argumente
Hier einige Beispiele wie man OHphone mit den entsprechenden Optionen
startet:
1. Nur Audio Unterstützung
#> ohphone –aln
a: Auto answer; l: Listen; n: No gatekeeper
2. Audio und Video (auf dem Testsystem)
#> ohphone –aln –-videotransmit –-videodevice
/dev/video –-videoinput 1
--videotransmit; Videosignal soll übertragen warden
--videodevice; Spezifiziert das Videoinput – Gerät
--videoinput; Spezifiziert den Videoeingang (Capture 1)
des Videoinput - Gerätes
3. Video auf dem embedded Board
#> ohphone –aln –-videotransmit –-videodevice
/dev/video –-videoinput 1 –-videoformat NTSC
-- videoformat NTSC; Verwendet NTSC, leider ist dies auf
dem embedded System nötig. Dadurch kann kein farbiges
Bild generiert werden.
6.4.5
```

source:
[https://prof.hti.bfh.ch/myf1/www/projects/ponchoplus/www/files/docs/Konzept.pdf](https://prof.hti.bfh.ch/myf1/www/projects/ponchoplus/www/files/docs/Konzept.pdf)

---

### Post by ssam on 2009-11-22
both ohphone and ekiga use open standards. you can call from one to the other. same with empathy, and loads of others.

---

### Post by murderslastcrow on 2009-11-22
I like Skypu. ^o^ *Japanesey*

Skype is open-sourcing the Linux client, all but the parts that would make it easy to make free calls to landlines and mobiles. So I don't think there's really a need to replace it. Many people (myself included) have paid for a few years subscription to their service. If they want to play nice with the Linux open source community in particular while preventing anyone from corrupting their franchise and bankrupting them, I think they're fine the way they are.

They're giving us as much as they can without going out of business.

But yeah, if you only use VOIP to VOIP, not for landlines, I don't see why it wouldn't be easy for us to use any other clients for the same task. It's just a nice, integrated solution for video, voice, text, and connecting to the already prevalent networks for vocal communication.

---

### Post by frenchn00b on 2009-11-24
IS skypiax interesting for voip you think?

[http://wiki.freeswitch.org/wiki/Skypiax](http://wiki.freeswitch.org/wiki/Skypiax)

---

### Post by Tibuda on 2009-11-24
> **frenchn00b said:**
> I do not think so. Linux do not like SKYPE, because it is not GNU, no source code. 
A backend for VOIP, I am sure that lot of Linux - fans would like it. ;)

How Linux do not like Skype? Linux don't have feelings, it is only a bunch of binary code.  Software don't need to be open source to run on Linux! Skype has a Linux version. Why do you think Linux-fans are GNU/FOSS extremists? Some are, but I'm not. I'm sure most Linux users are not, and use Adobe Flash instead of Gnash, Nvidia drivers instead of the open drivers, Nero instead of Brasero/K3B (I don't think most use Nero because it is not free-as-beer, but some do).

---

### Post by NoaHall on 2009-11-24
> **danielrmt said:**
> How Linux do not like Skype? Software don't need to be open source to run on Linux! Skype has a Linux version. Why do you think Linux-fans are FOSS extremists? Some are, but I'm not.

Skype doesn't work that well on Linux.

---

### Post by Tibuda on 2009-11-24
> **NoaHall said:**
> Skype doesn't work that well on Linux.

Just edited my reply.

True, but this is not my point.

---

### Post by frenchn00b on 2009-11-25
**[COLOR="Magenta"] to run skype headless,	Do I need to install XORG and x windows system core to do that ? [/COLOR]**

Here please find teh code.

```

#!/bin/sh


killall -e skype

killall -e skype Xvfb

 Xvfb :2 &

 DISPLAY=:2 ; export DISPLAY ; skype &


while [ 1 ] ; do sleep 1h  ;  amixer -c 1 set 'Mic',0 100 ; done




```

**[COLOR="Magenta"] 	Do I need to install XORG and x windows system core to do that, by using xfvb ? [/COLOR]**



   --- - - -

---

