---
title: "USB Audio Interfaces"
date: 2010-11-17
forum: Ubuntu Studio
---

### Post by nick7076 on 2010-11-17
Hi, I'm somewhat new to the world of Linux and Ubuntu. But I wont be going back to windows:)

I have two related questions.

Previously under windows I used a Zoom H4 digital recorder as a USB audio interface with Cubase. I can still access it as a drive to import files in Ardour but I would like to use it as an interface.
Is this possible?
I am a complete novice when it comes to settings, although I can follow instructions, I have no idea what it is I'm messing with!

If my H4 isn't compatible can anyone suggest a USB interface that will work? I would prefer not to have to follow lots of instructions that I don't really understand in order to get it to work.

Ideally I need 8 inputs and stereo out, but even just stereo in/out would be better than nothing.

I'm running a Compaq 6820s Laptop with 2Gb Ram and Intel Core2Duo T5870 @ 2.0GHz and UbuntuStudio 10.04

Many thanks Nick

---

### Post by cchhrriiss121212 on 2010-11-17
Hello and welcome to Ubuntu,
Looks like it works OK:
[http://ubuntuforums.org/showthread.php?t=1362010](http://ubuntuforums.org/showthread.php?t=1362010)

First you should check it shows up using "lsusb" and "aplay -l" in a terminal window (hopefully you are not terminal shy). Then type in alsamixer and set the input/output levels using the arrow keys (use f6 to select the H4 as I imagine you also have onboard sound). 

Open jack control and refer to post #5 in the thread above. For other settings here is a good starting point:
Frames: 512
Sample rate: 48000
Periods: 3
Timeout: 1000
Check realtime and softmode boxes
The rest should be fine as default

If these settings work for you then you can lower the latency by decreasing the frame rate. Check it runs nicely by pressing OK on the setup window and start on the main interface.

---

### Post by nick7076 on 2010-11-17
Many Many thanks.

A few simple instructions was all it took.

I don't know enough about terminal instructions to know what I did or what I changed in the settings but it worked.

Would this work for any USB audio device? I don't mind spending a lot of money on the right piece of equipment but I would hate to waste money on something that doesn't work.

---

### Post by cchhrriiss121212 on 2010-11-17
> **nick7076 said:**
> 
Would this work for any USB audio device?
Unfortunately not, some are fully supported and some are not. Generally speaking USB 1.1 devices will work and USB 2.0 will not. 

I don't know of many USB devices with 8+ inputs, most in that range seem to be either PCI or firewire based. After a quick search I found the Roland [UA-101]("http://www.roland.com/products/en/UA-101/index.html"), which is supposedly [working nicely]("http://www.spinics.net/lists/linux-audio-users/msg68704.html") with later versions of ALSA and newer kernels. May require fiddling with 10.04, I don't know.

Have a look around and see if you can test anything out before buying. To check what else is supported see here:
[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

---

