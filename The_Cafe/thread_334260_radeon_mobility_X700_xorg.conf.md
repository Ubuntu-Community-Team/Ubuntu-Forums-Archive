---
title: "radeon mobility X700 xorg.conf"
date: 2007-01-08
forum: The Cafe
---

### Post by nisbus on 2007-01-08
Hi,

I know this is a tired subject because I've seen it all over this forum and on other distros forums.

This is the sum of the problem:

Most people who have the ATI Radeon Mobility X700 display card on a laptop seem to be running into the same problem:

Upon boot they get a splash screen, the splash freezes and the display turns off. Ubuntu starts up successfully and people hear drumming.

After that results vary, some people manage to get to command line by using CTRL+ALT+F1 while others get garbled screen output when trying to access the command line (yup, that's me).

Now from what I've read people have been fixing boot problem by adding 
Option "MonitorLayout" "LVDS,AUTO" to either their Device or Monitor section, posts vary on this one making it harder to figure out for the new guy (me again :))

So to my particular problem:

I have an ASUS W1Vc laptop with the ATI Radeon Mobility X700 card and thus this problem.

I managed to create a bootable Ubuntu 6.10 2GB USB memory stick which runs on every computer I've tried except my own :(. (Thanks to Kolo on the LiveCDPersistence post)

I'm running windows XP pro on my laptop but I put up a VMWare virtual machine of Ubuntu so that I can access my memory stick partition and make changes to the config files needed.

I've tried changing the xorg.conf file several times but everytime I come back to it after a boot it seems to have reverted back to the way it was and I have a new file named xorg.conf.xxxxxxxxxxxx (where x is an integer number) that holds my previous changes.

So has anyone come up with a solution to this problem and wouldn't mind writing a detailed how to?

Keep in mind that those who most frequently have this problem (and are unable to fix it) are newbies to linux like me and most likely have a hard time finding the terminal :).

So if YOU want to write a how to for this problem, please be specific and explain why I'm supposed to add a line to the xorg.config and exactly where.

Thank you all for a great forum and the best looking linux distro I've seen so far (I got sucked into Ubuntu because of the colors :).

---

### Post by nisbus on 2007-01-11
Ok, I managed to get this thing working.

First off, take out the splash in the boot (I also added 3 for the runlevel but that shouldn't be neccessary).

Taking out the splash enabled me to get to console and from there edit my xorg.conf file with Ubuntu running and thus it didn't overwrite my xorg.conf file when I started X.

I downloaded fglrx trough apt-get and used that as the driver in my xorg file.
I also added my resolution 1680x1050 to the file and finally added 

Option "MonitorLayout" "LVDS,SVT" to the device section.

Now when I started X everything went fine.

Of course since I'm running a persistant LiveCD from a USB stick I knew that as soon as I rebooted my settings would get overwritten (this is of course due to the nature of the LiveCD since it's meant to be able to run on various computers with various hardware, so it needs to read the settings on each boot).

I did a little search on the internet and found a linux command crtt which makes the file immune to changes even if you're root.

so I wrote:
  sudo crtt +i /etc/X11/xorg.conf 

also did the same thing with my network/interfaces file so that the wireless network at my home would be fixed to this installation.

Lo and behold when I restarted my computer all of my settings were as I last left them so now my laptop can run Ubuntu at last.
Of course there is a downside, when I plugged my USB stick into my computer at work (a generic desktop machine not using ATI x700) Ubuntu crashed on boot.
I could use the XforceVesa option there but of course my settings weren't there and it's not persistant (I plan to add persistance to my syslinux.cfg for that option too)

Success for a complete newbie who is now thinking of erasing winXP from my computer.

Now I only have to figure out how to keep on programming .NET applications using Delphi on Ubuntu ;)

---

