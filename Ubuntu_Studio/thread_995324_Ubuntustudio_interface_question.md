---
title: "Ubuntustudio interface question"
date: 2008-11-27
forum: Ubuntu Studio
---

### Post by dawiba on 2008-11-27
I intended to install the Studio version, but thought I'd try Ubuntu on it's own first. So, I downloaded Ubuntu a couple of days ago, I've been messing around with it and everything is fine so far.

I've been reading the various threads about upgrading to the Studio version and I'm happy enough with that.

The issues seem to be with sound cards, specifically firewire cards. I have a Focusrite Saffire LE, which appears to be supported under ffado, but not under freebob. It also appears to me (as a newbie) that ffado isn't in a finished form just now, so that probably means I won't get to use the Saffire LE for a while.

However, I do have a Tascam US 122 and a Mackie XD-2 (Spike) lying in a cupboard just now. I see the Tascam is supported under ALSA, but the Mackie isn't mentioned. However, it claims to be standards compliant, which means it should work.

I was wondering if anyone was using these sound cards successfully.

---

### Post by dawiba on 2008-11-28
Just to answer my own post!

I got the Mackie to work and was able to do a short test recording and playback in Ardour.

I had a problem with xruns which left the audio glitchy. I guess I'll need to spend a bit of time reading and tweaking :)

---

### Post by jazzman on 2008-11-29
I have the US122 and it works very well. Here's a link the tutorial:
[http://alsa.opensrc.org/Tascam_US-122](http://alsa.opensrc.org/Tascam_US-122)

Here's what I did:

Open A Terminal

1. Enter   sudo apt-get update
2. Enter   sudo apt-get install fxload alsa-firmware-loaders
3. Download firmware [ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.17.tar.bz2](ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.17.tar.bz2) using browser
4. Extract file (I used the archiver and extracted to the Desktop)
5. Enter in terminal    cd ./Desktop
6. Enter    sudo cp -r ./usx2yloader /lib/firmware/
7. Open Text editor and name it   55-tascam.rules
8. Enter/copy this text:

 BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8006", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/sbin/fxload -D %N -s /lib/firmware/usx2yloader/tascam_loader.ihx -I /lib/firmware/usx2yloader/us122fw.ihx'"
 BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8007", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/usr/bin/usx2yloader'"

9. Save file to desktop
10. In terminal enter   sudo cp ./55-tascam.rules /etc/udev/rules.d/
11. Now plug in the US122 and the green light should come on.

Good luck!

Jazz

---

### Post by dawiba on 2008-11-29
That's great jazzman, thanks :)

This is where I have to confess that I had forgotten that I'd let someone borrow the US 122 to use to record vinyl onto their computer. That's why I tried the Mackie unit first. I should have it back again at the start of next week and I'll follow your guide then.

I managed to reduce the xruns so that I only get the occasional one now, but it doesn't cause any glitches when I record some audio. Midi is another matter :(. I can get a couple of the soft synths to play using my keyboard but that's all. 

I'm used to making music on a Mac using Tracktion, which deals with audio and midi in the one application. I got a little confused at first with Jack, but persevered and I kind of know what I'm doing to change settings now. I know you can use Jack on a Mac, but I hadn't before now. SEQ24 is a bit of a mystery to me yet, but I'll work it all out I'm sure. Jack just seems an unnecessary added layer to me at the moment, although I can see the advantage of being able to route pretty much what you want where you want and I'm sure that once I'm used to it I'll not want to be without it

The next objective is to record just midi, synced to audio in Ardour, and use this to trigger sounds in my keyboard as this is my normal method of working.

Anyway, I'm having fun, Ubuntu is great, Ardour is great, these forums are excellent (especially the Absolute Beginners, i.e. me!) and sorry for the long winded reply :oops:

---

### Post by dawiba on 2008-12-01
I got the US122 back this morning and have followed your instructions, but get stuck at this point

6. Enter sudo cp -r ./usx2yloader /lib/firmware/

When I type this in I get this

cp: cannot stat `./usx2yloader': No such file or directory

Any ideas?

---

### Post by claudioaudio on 2009-06-18
> **jazzman said:**
> I have the US122 and it works very well. Here's a link the tutorial:
[http://alsa.opensrc.org/Tascam_US-122](http://alsa.opensrc.org/Tascam_US-122)


Open A Terminal

1. Enter   sudo apt-get update
2. Enter   sudo apt-get install fxload alsa-firmware-loaders
3. Download firmware [ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.17.tar.bz2](ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.17.tar.bz2) using browser
4. Extract file (I used the archiver and extracted to the Desktop)
5. Enter in terminal    cd ./Desktop
6. Enter    sudo cp -r ./usx2yloader /lib/firmware/
7. Open Text editor and name it   55-tascam.rules
8. Enter/copy this text:

 BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8006", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/sbin/fxload -D %N -s /lib/firmware/usx2yloader/tascam_loader.ihx -I /lib/firmware/usx2yloader/us122fw.ihx'"
 BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8007", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/usr/bin/usx2yloader'"

9. Save file to desktop
10. In terminal enter   sudo cp ./55-tascam.rules /etc/udev/rules.d/
11. Now plug in the US122 and the green light should come on.

Good luck!

Jazz

 im still having trouble. Im have Jaunty Jackle. COuld someone please post a video showing step by step what to do. It would be greatly appreciated. Thanks in advance

---

