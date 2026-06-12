---
title: "Dream Studio script hosed my system"
date: 2011-12-06
forum: Ubuntu Studio
---

### Post by lavadisco on 2011-12-06
On advice from somebody at the Ardour forums, I ran this script which supposedly would optimize my Ubuntu Natty install into a Dream Studio audio system:

[http://sourceforge.net/projects/dreamstudio/files/Dream%20Studio%20for%20Ubuntu/](http://sourceforge.net/projects/dreamstudio/files/Dream%20Studio%20for%20Ubuntu/)

Before I ran it, I thought to myself "this seems like something that could break my system", and lo and behold it did. Now when I boot up, it doesn't matter which version of Ubuntu I choose (low latency, recovery, older versions, etc), it only gets back to the boot screen, flashes a few times and then just sits there without going any further. Luckily I had the sense to back up my files on an external HD. Does anybody know what I can do to fix this aside from reinstalling? I'm writing to you from my Win 7 partition right now (Grrr...)

---

### Post by sgx on 2011-12-06
Make a new install with a separate /home partition, for future easy
reinstalls, and also use installs on  external devices for experiments. For now, using a live cd/dvd, try renaming your .folders in /home/username, without the dot, and reboot. Mainly the ones related to gnome, kde, gtk, window managers/graphics etc. This may inspire new .dot folders to be written based on the update.

look for /etc/X11/xorg.conf.old or similar, in case the update wrote
a new bogus one, and rename it xorg.conf, after renaming the other one
to xorg.maybe or something. This link may have good detail:

[http://www.backtrack-linux.org/wiki/index.php/Basic_Usage](http://www.backtrack-linux.org/wiki/index.php/Basic_Usage)

Good luck

---

### Post by mattzab on 2011-12-06
I use 11.04 and I installed that same script.
Now when I log in I can't see my Cairo Dock (nor will it start at all) and even though none of my settings have changed in compiz config settings manager, none of the effects are working. Its like they are all disabled.
Also, I have a program called shutter that takes screen shots of the desktop any time I hit a hotkey, but now it only works if i click the icon in the notification panel prior to hitting that hotkey, where before i could hit the hotkey any time i wanted and it would work.
 
I haven't been able to try renaming xorg.conf or any of my .folders since I'm working crazy hours but I'll try that when I get home.
EDIT: I just checked to rename xorg.conf and that file isn't present at all.
 
Based on my symptoms, can anyone guess as to what the problem might be? Is there anything I can configure or check on? I tried uninstalling the package that script installed and it wasn't effective.
 
Thanks.

---

### Post by mattzab on 2011-12-09
Ok, I tried running Cairo Dock in terminal and here's what I got.

```
root@matts-i5:/home/matt# cairo-dock
Xlib:  extension "GLX" missing on display ":0.0".

(cairo-dock:2806): GdkGLExt-WARNING **: Window system doesn't support OpenGL.

```

Cairo Dock doesnt work, Compiz doesn't work, my screenshot utility works kinda, but not as well as it used to, and some stuff renders weird.

How can I fix this? I think I'm over complicating it. How do I get GLX back?

---

### Post by jejeman on 2011-12-09
Give us output from
```
lspci -knn|grep VGA -A 5
```

---

### Post by mattzab on 2011-12-09
[SOLVED]

Ok, for my problem I booted into a Live CD, mounted the file system and uninstalled nvidia-current. (from [_this_]("http://www.warp1337.com/content/ubuntu-1104-blackblank-screen-nvidia-geforce-natty-narwhal-doesnt-start") guide) Then I was getting a blank screen, so I loaded up recovery mode and selected graphics failsafe mode.
I told it to generate a new config file for my system, then rebooted and it worked right off the bat.

---

### Post by collisionystm on 2011-12-09
> #!/bin/bash
echo 'Downloading the Dream Studio software sources package...'
wget [http://dream.dickmacinnis.com/pool/main/d/dreamstudio-software-sources/dreamstudio-software-sources_2.5_all.deb](http://dream.dickmacinnis.com/pool/main/d/dreamstudio-software-sources/dreamstudio-software-sources_2.5_all.deb)
echo 'Installing the Dream Studio software sources...'
sudo dpkg -i dreamstudio-software-sources_2.5_all.deb
sudo sed -i 's/# deb/deb/g' /etc/apt/sources.list
echo 'Updating your software sources...'
sudo apt-get update
echo 'Installing Dream Studio...'
sudo apt-get -y install dreamstudio-audio-effects dreamstudio-audio-recording dreamstudio-desktop dreamstudio-dj-tools dreamstudio-graphic-design dreamstudio-headers dreamstudio-instruments dreamstudio-photography dreamstudio-video linux-lowlatency linux-headers-lowlatency
echo 'Adding Dream Studio tweaks for the current user. Run this program again for every existing user you wish to optimize. All new users will automatically be optimized...'
#adding current user to extra groups
sudo usermod -aG dialout $(whoami)
sudo usermod -aG cdrom $(whoami)
sudo usermod -aG floppy $(whoami)
sudo usermod -aG audio $(whoami)
sudo usermod -aG video $(whoami)
sudo usermod -aG plugdev $(whoami)
sudo usermod -aG users $(whoami)
#adding default pulseaudio and qjackctl configurations to current user
#this enables pulseaudio -> JACK integration
cp -r /etc/skel/.config ~/
cp -r /etc/skel/.pulse ~/
echo 'Cleaning up...'
rm dreamstudio-software-sources_2.5_all.deb
echo 'Done!'



I cant say I see anything that would break your system. Sure it wasn't something else?

---

