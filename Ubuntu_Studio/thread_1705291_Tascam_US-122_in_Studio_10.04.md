---
title: "Tascam US-122 in Studio 10.04"
date: 2011-03-12
forum: Ubuntu Studio
---

### Post by _DRoboto on 2011-03-12
I just took my first bold (and nearly blind) steps into Linux and away from windows.  I converted my gaming / audio laptop from win7 to Ubuntu studio 10.04.

The trickiest part was getting my old us-122 to play nice with my new linux there were a couple pretty good tutorials, but as this is seriously old hardware none of these were quite up to date with the newer distros and packages.  So I thought I'd compress my efforts into a couple handy tips and tricks for anyone else out there trying to get an old Tascam to work with a new version of Linux.

1.  the older versions of alsa firmware required a second .tar be downloaded and installed, but with newer versions of the alsa firmware that is no longer required.  the older file ezusb.ihx has been since replaced with us122fw.ihx as of now  the current fw is alsa-firmware-1.0.24.1

2.  after the firmware package is installed a reconfiguration of the alsa-base package with the us-122 plugged into the computer is required.  just make sure the interface is plugged in, open up a terminal window and run "sudo dpkg-reconfigure alsa-base"

3.  the us-122 won't initialize unless there is and input of some kind plugged into the interface 1/4 in. or XLR doesn't matter (this applies to # 2 as well)

hope this allows someone out there to save some time.

mark

---

### Post by biotob on 2011-06-02
This issue (Tascam US-122) and WoW not working properly were the only two things keeping me from switching over.

I'm currently using 10.10 and I got WoW working thanks to the amazing people the frequent these forums (thank you all). I'm still having issues with this interface, but I'll try these steps when i get home today. :)

BTW...if it's not obvious yet, I'm a complete n00blet when it comes to Linux.  

PS: I've tried practically everything from the official Ubuntu Help pages to [This]("http://ubuntuforums.org/showthread.php?t=1692289&highlight=tascam+us-122") without []("http://ubuntuforums.org/showthread.php?t=1692289&highlight=tascam+us-122")success :/

---

### Post by biotob on 2011-06-03
I hope this isn't a "derpa-durp" discovery. But I realized that if you have your tascam installed and you get lights but no sound, you might want to check that ur USB is plugged directly into your PC and not int a USB HUB of some sort. 
I "discovered" this yesterday as I had my Tascam US-122 plugged into the back of My Apple Cinema Display (which has USB ports) and I had no sound. As soon as i switched it to the PC i heard the glorious sounds of "The Black Dahlia Murder" and my life was  complete :).

---

### Post by wbm on 2011-06-14
> **_DRoboto said:**
> I just took my first bold (and nearly blind) steps into Linux and away from windows.  I converted my gaming / audio laptop from win7 to Ubuntu studio 10.04.

The trickiest part was getting my old us-122 to play nice with my new linux there were a couple pretty good tutorials, but as this is seriously old hardware none of these were quite up to date with the newer distros and packages.  So I thought I'd compress my efforts into a couple handy tips and tricks for anyone else out there trying to get an old Tascam to work with a new version of Linux.

1.  the older versions of alsa firmware required a second .tar be downloaded and installed, but with newer versions of the alsa firmware that is no longer required.  the older file ezusb.ihx has been since replaced with us122fw.ihx as of now  the current fw is alsa-firmware-1.0.24.1

2.  after the firmware package is installed a reconfiguration of the alsa-base package with the us-122 plugged into the computer is required.  just make sure the interface is plugged in, open up a terminal window and run "sudo dpkg-reconfigure alsa-base"

3.  the us-122 won't initialize unless there is and input of some kind plugged into the interface 1/4 in. or XLR doesn't matter (this applies to # 2 as well)

hope this allows someone out there to save some time.

mark

I have the Tascam US122 and it has worked flawless in Ubuntu Studio 9, 10, 11 and now KXStudio 11.04

Option 1:
Shutdown computer
Unplug Tascam USB device
Reboot and log in
Plug Tascam USB device back into your computer and see if it is now detected
If not, unplug and replug in one more time for good measure while logged in.

Option 2:
Maybe you don't have all needed software yet.
In Synaptic search for Tascam.
It should list 3 Alsa items related to Tascam hardware.
Install those.
Unplug Tascam USB device
Reboot
When logged in plug Tascam USB device back in.

The key in all this is that you must plug the device in while logged in after you have all drivers installed.
On KDE you get to do that after each reboot 

In Sound Settings select the Tascam US 122 as your Output device
That should do it.

---

### Post by deoanam2002 on 2012-01-10
Your post helped me a lot. I've documented the steps I took to get the US-122 working under Ubuntu Studio 10.10 here (perhaps this will help someone else):
[http://resteasy.info/index.php/2-installing-tascam-us-122-on-ubuntu-1010-maverick](http://resteasy.info/index.php/2-installing-tascam-us-122-on-ubuntu-1010-maverick)
You'll notice that it's similar to the instructions on the Ubuntu wiki, except for the ihx replacements you mention. Thanks!

---

### Post by wbm on 2012-01-10
> **deoanam2002 said:**
> Your post helped me a lot. I've documented the steps I took to get the US-122 working under Ubuntu Studio 10.10 here (perhaps this will help someone else):
[http://resteasy.info/index.php/2-installing-tascam-us-122-on-ubuntu-1010-maverick](http://resteasy.info/index.php/2-installing-tascam-us-122-on-ubuntu-1010-maverick)
You'll notice that it's similar to the instructions on the Ubuntu wiki, except for the ihx replacements you mention. Thanks!

Sounds complicated :)

I just went into Software Center, typed in Tascam, which gives two results.  I then installed the second one, the "ALSA software loaders for specific hardware". Those include usx2yloader and the firmware loader for Tascam USX2Y USB soundcards.
Reboot, log in, plug the Tascam in and it works.
My only issue, and only in the newer Ubuntu versions was that sometimes after logging out and logging back in, I had to unplug and replug the Tascam USB cable to have "the lights" come on.

---

### Post by deoanam2002 on 2012-01-10
Hm. That's strange. I tried the easy way and for some reason it didn't work for me. What version of Ubuntu are you running? 
Edit:
Ah, I see that you've tried it on a bunch of different versions. hm.

> **wbm said:**
> Sounds complicated :)

I just went into Software Center, typed in Tascam, which gives two results.  I then installed the second one, the "ALSA software loaders for specific hardware". Those include usx2yloader and the firmware loader for Tascam USX2Y USB soundcards.
Reboot, log in, plug the Tascam in and it works.
My only issue, and only in the newer Ubuntu versions was that sometimes after logging out and logging back in, I had to unplug and replug the Tascam USB cable to have "the lights" come on.

---

