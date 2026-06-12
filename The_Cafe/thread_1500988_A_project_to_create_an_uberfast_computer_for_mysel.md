---
title: "A project to create an uberfast computer for myself"
date: 2010-06-03
forum: The Cafe
---

### Post by Dustin2128 on 2010-06-03
I recently acquired yet another laptop (windows performance decay is my best friend :D) with 2Gb of ram, a 180Gb hard drive, AMD 64 bit processor and an ATI radeon. I just had a thought that it'd be a nice project (read: fun waste of time) to create one of those computers that goes from off to ready to run apps in 10 seconds>, any thoughts on distros/bios changes? Kinda leaning towards a damn small linux hard disk install or scrapping the hard drive for my spare 8gb flash drive or something a little bigger. Nothing special I was planning to use it for except for some web browsing. Thoughts, ideas, existing projects?

---

### Post by dragos240 on 2010-06-03
You can use ubuntu, just configure the daemons to a minimum. My laptop used to boot up in about a minute. I edited the daemons. It's now about 12 seconds. Also, try using a less ram hungry window manager, such as icewm or fluxbox. I use <100mb of ram on average on my netbook. It has 1gb of ram. You should boot in about 6 seconds with the daemons set to a minimum.

---

### Post by cfalzone on 2010-06-03
Well, if you're looking for a quick and easy fix you could try out Hexxeh's Chromium OS builds... a quick search for "Hexxeh" should get you what you need.  These Chromium OS builds really only support certain hardware.

If you want to get into a world of pain you could try out the Coreboot project wiki <http://en.wikipedia.org/wiki/Coreboot> and see if you can build your own firmware to flash.  On top of the coreboot firmware you could place your favorite distro and I'm pretty sure it'd be way fast at booting even with a vanilla installation.

---

### Post by Joe of loath on 2010-06-03
Damn small Linux will boot in no time on that hardware, it's just limited in functionality. As said above, tweak ubuntu and you'll be there. My dell starts up in under 30 seconds, and that's with an out of the box install!

---

### Post by Brent0 on 2010-06-03
(Good)SSDs dramatically decrease boot time and application load times.

---

### Post by Dustin2128 on 2010-06-03
Alright, thanks for the help. I'm going to test this for myself on my current ubuntu system and post feedback after I'm done. Anyone have the record for fastest linux boot out of sheer curiosity?

---

### Post by libssd on 2010-06-03
> **dragos240 said:**
> You can use ubuntu, just configure the daemons to a minimum. My laptop used to boot up in about a minute. I edited the daemons. It's now about 12 seconds. Also, try using a less ram hungry window manager, such as icewm or fluxbox. I use <100mb of ram on average on my netbook. It has 1gb of ram. You should boot in about 6 seconds with the daemons set to a minimum.
Could you be more specific about which daemons?

OP: You can get a tremendous speed hit by replacing the HDD with a fast SSD (OCZ or Intel). I picked up a 30gb OCZ Vertex last week for $96 (after rebate). Intel 40 GB X25-V is currently going for around $125.

---

### Post by NightwishFan on 2010-06-03
Puppy Linux is amazingly fast and functional. It should do what you want.

---

### Post by dragos240 on 2010-06-03
OP. I suggest installing rcconf. Great tool. There is quite a bit of "fluff" you can remove. I can tell you the daemons you can remove without loosing functionality a bit later. You can also remove HAL, but you will need to put all the devices in xorg.conf. However it only frees 1-2 seconds, so if you want the trouble, be my guest.

---

### Post by Dustin2128 on 2010-06-03
> **libssd said:**
>  You can get a tremendous speed hit by replacing the HDD with a fast SSD (OCZ or Intel). I picked up a 30gb OCZ Vertex last week for $96 (after rebate). Intel 40 GB X25-V is currently going for around $125.
Yes but with the problem of wear I'll stick with HDDs for now. Oh and thanks for rcconf, it is a great tool but I'd like you to be rather specific about which daemons I can uninstall without compromising the system.

---

### Post by Shining Arcanine on 2010-06-03
> **Dustin2128 said:**
> I recently acquired yet another laptop (windows performance decay is my best friend :D) with 2Gb of ram, a 180Gb hard drive, AMD 64 bit processor and an ATI radeon. I just had a thought that it'd be a nice project (read: fun waste of time) to create one of those computers that goes from off to ready to run apps in 10 seconds>, any thoughts on distros/bios changes? Kinda leaning towards a damn small linux hard disk install or scrapping the hard drive for my spare 8gb flash drive or something a little bigger. Nothing special I was planning to use it for except for some web browsing. Thoughts, ideas, existing projects?

Try a Gentoo Linux ~amd64 system. Those boot and run things very fast. If you customize the kernel to put all non-essential things into modules, the boot times will become even faster, because the kernel will be forced to start userland before it finishes initializing, allowing for a more parallel boot.

---

### Post by dragos240 on 2010-06-03
> **Dustin2128 said:**
> Yes but with the problem of wear I'll stick with HDDs for now. Oh and thanks for rcconf, it is a great tool but I'd like you to be rather specific about which daemons I can uninstall without compromising the system.
Right. You can generally remove most of it. Just keep the following:
Avahi-daemon
console-setup (if you have a non qwerty keyboard)
dbus (You REALLY need to keep this one if you plan on doing anything with an non-root user.)
network-manager (I think it's called Network-Manager in ubuntu, this helps connect you to a wireless network, with nm-applet, automatically. You actually can connect to a network using iwconfig, but that takes time, and it's even more of a pain if you use WPA. While you can remove this, I don't recommend it.)
udev (This is the sole thing you CANNOT remove, if you decide to ditch everything, keep this. Without it, you will not be able to mount any devices, and most likely, you won't even boot correctly. This populates /dev, where your devices are.)

Alsa-utils doesn't seem to do much, dispite it's name, I can still play audio.

Anything containing "cron" you may consider keeping, it logs what you do if there is any error.

HAL - if you use X, keep this.
GDM - if you're a noob, keep this.
Pulseaudio - ditch this

There are a few more, but I need to get some Zs'.

Oyasumi nasai!

---

### Post by WinterRain on 2010-06-03
> **nightwishfan said:**
> puppy linux is amazingly fast and functional. It should do what you want.

+1

---

