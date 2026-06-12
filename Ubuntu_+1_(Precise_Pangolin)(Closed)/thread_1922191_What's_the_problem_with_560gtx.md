---
title: "What's the problem with 560gtx?"
date: 2012-02-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sonnet on 2012-02-08
I downloaded the latest build this morning of the server 64bit to install  a command line system.
Installation proceeded smoothly.
After I reboot, though and the system load, the screen get pixellated (generally whit pixel, but also some line of green and red pixels),

I do not despair. Knowing the commands to install kde-plasma-desktop I login and install everything (including nvidia drivers and nvidia-xconfig command).
From the activity of the pixels I suppose I did everything right.
Indeed when I rebooted, I get the command-line login (though I was supposed to get the kde desktop).

I check with apt-get get amd kde is installed. I checked nvidia-drivers with xconfig and the configuration should be setup.
Still startx doesn't work to launch the graphical environment.
Error messages when launching startx are:
*_Nvidia: this server has an unsupported input driver ABI version (have 16.0 need <14.0)_*


Does anybody understand what's my problem?
My vga is a 560gtx club3d and the cpu a phenom x6 with a asrock mainboard with 970 chipset.

The hardware isn't really the newest, maybe only the chipset is quite recent.


Added xorg-edgers adn updated (and ran again nvidia-config) hoping it could solve the issue, but nothing changed.
Error message: Nvidia could not open the device file /dev/nvidia0

---

### Post by dino99 on 2012-02-08
inside your xorg.conf file, add:

Section "ServerFlags"
               Option   "IgnoreABI"    "True"
EndSection

---

### Post by sonnet on 2012-02-08
Are there any downsides doing that?

---

### Post by dino99 on 2012-02-08
> **sonnet said:**
> Are there any downsides doing that?

not worst than actual :)

---

### Post by sonnet on 2012-02-08
I'm considering if installing at this point 11.10.
My idea was to install cl system and bare kde on top of it with the applications I need.
For that reason, I was not too much worried about ubuntu 12.04 still being in alpha stage.
In my trials on vm, 12.04 seemed to be faster than 11.10 even though they both had installed kde 4.8.

For that reason I wanted 12.04, considering also is newer and a lts. I don't like the idea to install 11.10 and later upgrade to 12.04, as many people reported slowed system when they did not make clean install.

But this issue with xorg is really preventing me from install 12.04. If this code you posted solve the issues, then I'll be happy to reinstall 12.04, but if that will make work my system but not in a stable way, then I don't know..
That's why I'm asking to you if there are downsides or the problem get really solved .


Edit: [B]I read here and there, and using the xorg-edgers should have solved the issue(I mean the ABI version conflict).
Why do I still have the issue instead?[/B]

---

### Post by Vadi on 2012-03-24
Tried to install 12.04 and got a blank screen on gtx560 - apparently using nomodeset in the installer ought to do it.

---

### Post by dino99 on 2012-03-24
the latest 295.33 now works well with that card (see xorg-edgers ppa), you'll be asked to install xserver 1.12 too, thats ok.

note: remove xorg.conf now (useless & often disturb the kernel default settings)

---

