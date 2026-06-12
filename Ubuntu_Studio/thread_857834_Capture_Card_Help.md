---
title: "Capture Card Help"
date: 2008-07-12
forum: Ubuntu Studio
---

### Post by strat1227 on 2008-07-12
Hey guys, I have a Pinnacle Dazzle DVC 100 Capture device, it came with software to use to record from it, but it doesn't work for Linux (obviously) ... I was wondering if anyone knows of any software that can do the same thing. I'm trying to record things from my computer from a VHS tape (home videos) ... It plugs into the usb port and streams the video, the Windows Movie Maker for XP had an option to import from stream or camera or whatever,  and it could record ... but I don't know of any Linux programs that do that ... any help would be appreciated.

---

### Post by rushikesh988 on 2008-07-13
I can tell you some applications  that  will work  with capture card to record n view ..
1)VLC MEDIA PLAYER  
2)zapping TV viewer
3)MYTH TV Elisa media center
4)dvr recorder


you can try  GEEXBOX LINUX which is useful  TO VIEW TV 


                 --R!$H!

---

### Post by jerrylamos on 2010-02-13
I'm having some good luck with tv-viewer from sourceforge.net and even mplayer from synaptic on ubuntu 9.10 with capture card HVR-1950.

Installed the driver for the card into /lib/firmware then used synaptic to load ivtv-utils and mplayer.

ivtv-tune -c 4 --device=/dev/video0
mplayer -vf pp=lb /dev/video0

tv-viewer can watch and also record, and play the file while recording.  

Jerry

---

