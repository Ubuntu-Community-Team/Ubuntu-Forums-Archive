---
title: "Elementary OS: Screen Resolution Changing"
date: 2014-08-05
forum: Ubuntu/Debian BASED
---

### Post by derklempner2 on 2014-08-05
I have Elementary OS Luna (based on Ubuntu 12.04), and am having some problems with the display resolution randomly changing from 1920x1080 to 640x480.

I use the computer as a media PC running XBMC, and if I have XBMC running then the resolution never changes. However, if XBMC isn't running the display resolution will change basically at random. I'm using Nvidia's proprietary driver for my video card, but even opening Nvidia Settings doesn't allow me to change the resolution to anything other than 800x600 (or keep it at 640x480).

Has anyone else had this problem, or can anyone tell me if this is a known issue? Hours of Googling for somebody with a similar problem only uncovered one post to these forums (from December 2013), but without a concrete answer of how to fix the issue.

---

### Post by Stinger on 2014-08-08
Hi derklempner2, welcome to the Ubuntu forums.
I'll try my best to help you out.
First I need to know a bit more about your hardware, what pc you have, what graphics card your using etc. all the specs you can provide.
My best guess is that it's some kinda graphics issue, new card and old driver maybe.

---

### Post by MeadeBaron on 2014-10-24
I have the same problem with Luna 32-bit. How do you change the screen res in this crazy biotch? I have a GeForce 9600 graphics card. I'm running the 176 NVidia driver, I believe...

               ):P                                                                                                                              :guitar:   I just want to know how to change the resolution!

---

### Post by Stinger on 2014-10-25
It would seem that you are using an old driver from nvidia, your driver should be of the 300 series instead ( nvidia current ).  
Se if you can find it in the additional drivers utility ( jockey ) or in the software center.
Ps.
You'll need to install the nvidia-settings package too, to control the display settings:
There is a question at ask ubuntu which covers the issue:
[how to get an nvidia control panel?]("http://askubuntu.com/questions/302518/how-to-get-an-nvidia-control-panel")

---

