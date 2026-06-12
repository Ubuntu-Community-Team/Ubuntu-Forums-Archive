---
title: "Magic camera and wine"
date: 2011-05-09
forum: Wine
---

### Post by magodiafano on 2011-05-09
Hello I would like to use magic camera on ubuntu because I don't like some things in webcamstudio.

I installed magic camera using wine, but the problem is in the fact that the other programs don't see the "virtual camera"... and "magic camera" don't see the real webcam installed on the computer. Is there away to fix this problem?

---

### Post by magodiafano on 2011-05-10
could someone help me?? I need this help!!

---

### Post by bobwyajnr on 2011-05-10
Hi **magodiafano**

I have only used [Cheese]("https://help.ubuntu.com/community/Webcam") with my laptop's builtin webcam - in Ubuntu. You sure no native (GNU/Linux) applications can meet your needs? (E.g. by sticking *webcam* in the search box in **Synaptic** package manager or looking over in the [Ubuntu PPA's]("https://launchpad.net/ubuntu/+ppas").)

To my knowledge (limited) WINE only passes through certain Linux system API's to the Windows application you are trying to run. Sound (via ALSA, OSS, etc.), graphics hardware (via OpenGL/GTK calls), your mounted filesystems/optical drives and networking. I don't believe WINE talks to any other Linux hardware system API's?? I know USB passthrough support (e.g. to get iTunes working with your iPod ala Virtual Box) is slated for version 1.4...

I would also recommend cross-posting this question on the [Wine HQ forums]("http://forum.winehq.org/")... Just be prepared to be shot down in flames by the developers (no code of conduct over there - just tumbleweed :o:roll::shock: ).


Sorry I can't be more helpful!

Bob

---

