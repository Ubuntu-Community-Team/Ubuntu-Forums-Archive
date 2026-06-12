---
title: "VLC Streaming to website (Possibly the wrong section)"
date: 2011-06-15
forum: Server Platforms
---

### Post by TechSupportx86 on 2011-06-15
This may be the wrong section, it either goes here, or in multimedia (but here seemed right to me)

Ok so what i am trying to do is setup a website on my NAS i can access from outside the house with links that will open up FireFTP, FireSSH, Maybe a photo stream, time/temp, ect... but that's not the problem, that's going fine and dandy. 

[COLOR=Red]The problem[/COLOR] i am having is getting VLC to stream to the main page. What i want is 2 webcams (Logitech C200 USB Webcams) To stream at a low FPS (2?) to the main page (for now, so just index.html). 

I have tried following a guide here: [http://forum.videolan.org/viewtopic.php?f=13&t=39050](http://forum.videolan.org/viewtopic.php?f=13&t=39050)

But it's outdated and doesn't seem to work, So i think i just need an updated version of this guide, or someone who knows what they're doing when it comes to VLC (i clearly don't).

This is really just a project, i mean if you have 5 minutes to share any knowledge on the matter please do. The server's local IP is 192.168.1.3, I am running Ubuntu 10.10 x86, VLC v1.1.4, Webcam is on /dev/video0 and it does work, i tested it with a capture command via SSH and a photo showed up where i told it to. Even running:

```
cvlc v4l2:///dev/video0
```Shows me my room in PuTTY, so the webcam IS working without a doubt, i just can't get the thing to stream to my page >:/

Any input is MUCH appreciated ;)

---

### Post by TechSupportx86 on 2011-06-17
One bump for the weekend

also, it doesn't NEED to be VLC. if someone out there knows how to stream a webcam to a web page using a different program that's fine. Just keep in-mind that i am on 10.10, webcam is on dev/vide0, and let's keep the FPS under 5.

---

