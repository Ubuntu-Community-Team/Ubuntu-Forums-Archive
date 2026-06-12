---
title: "Ubuntu installation experience"
date: 2008-03-02
forum: Testimonials &amp; Experiences
---

### Post by mental_gnome on 2008-03-02
I though i'd share my ubuntu dual boot installation experience here.
It's ubuntu 7.10 Gutsy Gibbon.
I'm pretty new to whole linux thing(i need it for my CS course, so i've got to go through this)

I've got three hard drives installed, all with ntfs partitions.
So i freed a 25gigs on one of the drives beforehand.
Booted from live cd just fine. (although takes forever to boot)
Ran gparted (it takes like 10 minutes to launch, what the hell).
Scheduled ntfs partition resize, creation of root partition, swap partition, etc. Ran it. Well after a few seconds it crashed. Nice work guys! Making a release with buggy partition editor! Well i'm not risking my data - i thought.
Found a dusty old 60gig harddrive connected it via usb, now i'm trying to partition it. Turns out that gparted crashes after each operation - and after each operation you can go and have a dinner.

And it's not only the partition editor which is flawed.

Default installer on livecd is very cumbersome:
Prepare you disk space - all the partitions are numbered, no names or anything. Now, you've got to figure out somehow which partition the installer is referring to. (or run gparted to see them + have a dinner while it's launching)

So basically - if you're not devoting your whole harddrive to this "thing", you're going to have problems. 

Plus, by default livecd doesnt detect video card(or have proper drivers) and screen's all blurry.

But i've got to keep going, it's fun.
If it was working flawlesly it would be no fun, right? RIGHT?

---

### Post by freebeer on 2008-03-02
I'd have to say that your experience is definitely different from mine.  I recently set up a dual boot on a new machine.  Ubuntu was up and running (including using gparted to create and format 3 80gig (total) partitions) in about 30 minutes... and that included installing the restricted drivers, etc.  Windows, on the other hand, was a 12 hour affair of frustration which didn't include working sound.

---

### Post by ajgreeny on 2008-03-02
I think you must have hardware that just is not to ubuntu's liking.  The live CD should only take about 2 -3 mins at the most to boot to a desktop, and gparted should only be about a few seconds to launch.

What specs do you have as it may be possible to get things running better than you are seeing at present.

Just to give you an example, the last time I did a clean update/install from feisty 7.04 to gutsy 7.10 it took all of 30 mins from doing the backup of home using grsync to a usb external disk, booting to the liveCD and then installing to the hard disk.  Restoring home and the updating that always happens on install took not very much time and there was a need to reinstall all the apps which I use but are not on the CD.  Overall it was the work of no more than 1 - 1.5 hrs, and there I was with a brand spanking new system.

---

### Post by mental_gnome on 2008-03-02
> **ajgreeny said:**
> I think you must have hardware that just is not to ubuntu's liking.  The live CD should only take about 2 -3 mins at the most to boot to a desktop, and gparted should only be about a few seconds to launch.

What specs do you have as it may be possible to get things running better than you are seeing at present.

Just to give you an example, the last time I did a clean update/install from feisty 7.04 to gutsy 7.10 it took all of 30 mins from doing the backup of home using grsync to a usb external disk, booting to the liveCD and then installing to the hard disk.  Restoring home and the updating that always happens on install took not very much time and there was a need to reinstall all the apps which I use but are not on the CD.  Overall it was the work of no more than 1 - 1.5 hrs, and there I was with a brand spanking new system.
CPU: c2d 6420
HDD:
2 ide hdd
1 sata hdd
1 usb-2 ide hdd(currently it's installed here, but before adding this hdd gparted acted the same way)
CD connected thru usb-2 too
Video: ATI x1950pro pci-ex x16 (two DVI monitors)
Gigabyte mobo
2 gigs of ram

Note:
* dual monitor setup doestn work
* 4 button mouse(forward/back works incorrectly)
* it seems somewhat slow(i'm used to "very fast" system)

---

### Post by hyper_ch on 2008-03-03
> **mental_gnome said:**
> Scheduled ntfs partition resize, creation of root partition, swap partition, etc. Ran it. Well after a few seconds it crashed.
Running Vista?

> **mental_gnome said:**
> Nice work guys! Making a release with buggy partition editor!
GParted has never crashed on me...

> **mental_gnome said:**
> Well i'm not risking my data - i thought.
Partitioning is always a risk. Best practice is to have a backup before partitioning and even better to make backups automatically once in a while.


> **mental_gnome said:**
> Default installer on livecd is very cumbersome:
For installation it is recommended to use the alternate install cd.

> **mental_gnome said:**
> Prepare you disk space - all the partitions are numbered, no names or anything. Now, you've got to figure out somehow which partition the installer is referring to. (or run gparted to see them + have a dinner while it's launching)
They are labelled... device name and partition on it... if you don't know what your setup is like then that is not the problem of the partitioner.

> **mental_gnome said:**
> So basically - if you're not devoting your whole harddrive to this "thing", you're going to have problems.
No, you're not... you just should inform yourself first what you're about to do...

> **mental_gnome said:**
> Plus, by default livecd doesnt detect video card(or have proper drivers) and screen's all blurry.
Windoze does detect by default the video card and use proper drivers? I don't think so... well, first I'd need to see a windoze LiveCD anyway...

> **mental_gnome said:**
> But i've got to keep going, it's fun.
If it was working flawlesly it would be no fun, right? RIGHT?
The first steps in unknown territory are always hard... it'll become easier... sooner than you might think you'll be recompiling your kernel to your liking ;)

---

### Post by ellalan on 2008-03-03
Hi
Ihave switched to Ubuntu from XP recently and I would like to share my experience with you. 
You might have heard people falling asleep listening to radio,watching TV,in a political party conference but have any of you heard of any one falling asleep in front of a PC. Yes...you guessed it right, I did fell asleep. It was dead boring working with windows, but with Ubuntu I found it is not computing it is a fantastic  experience.
With Ubuntu I do not need to replace any hardware, I simply select the utilities that work best with my system because Ubuntu provides a large collection of utilities and if I struggle with any issues I can always get help in this wonderful forum.
When I first saw the word "sudo" I thought it was a Japanese word, now you can understand when I say "If I can do it any one can".
All you need to operate Ubuntu is a little bit of determination,dedication and desire to learn. All the best.

---

### Post by Sturmeh on 2008-03-03
Last time I checked, Windows used a very unfriendly GUI ( apart from Vista ) that only lets you format and make partitions.

If you came to ubuntu the same way you came to Windows install, you would have NO problems what so ever.

So when I install my OS, i install Windows, leave a 20GB space for Linux, then install Linux no problems.

Use manual if you don't like teh defaults.

---

### Post by armandh on 2008-03-03
the partition editor[and Ubuntu] is not a happy camper below 256 meg memory.
I have tricked it by installing an old 200 meg [not gig] Hdd with a swap partition but find it much easier to use Gparted live disk first and select "use largest unpartitioned space" when installing. easier to get more memory.
but if you have enough memory....
as always I first suspect hardware problems.

---

### Post by mental_gnome on 2008-03-03
> **hyper_ch said:**
> Running Vista?
Running windows XP as dual boot.

> **hyper_ch said:**
> GParted has never crashed on me...
What matters is what it has crashed for a bunch of folks using ubuntu 7.10 livecd, including me. And it leaves a bad impression when a critical part like partitioner crashes in a major software release.

> **hyper_ch said:**
> They are labelled... device name and partition on it... if you don't know what your setup is like then that is not the problem of the partitioner.
I do know my setup. Installer was refering to partitions by a NUMBER, not by name.

> **hyper_ch said:**
> Windoze does detect by default the video card and use proper drivers? I don't think so... well, first I'd need to see a windoze LiveCD anyway...
Why do you have to bring up windows now?
It's not like i'm comparing. (like it's even possible)
Windows at least has drivers downloadable from ATI homepage which are officially supported and working without problems(including setting up dual monitors in no time).
> The latest version of the ATI Proprietary Linux Graphics Driver is designed to support the following Linux distributions: 
Red Hat Enterprise Linux suite 
Novell/SuSE product suite

Nice, huh. (hardware vendor is to blame, yeah)

And in order to setup dual monitors(which is my major concern right now), you've got to go and manually write some stuff in terminal, which may and may not work at all(as in my case, dual monitors working only "partially"). There's no definitive way to do it propertly. If the dual monitors are not working usually no one knows what's wrong. So you've got to risk screwing up X windows system by editing "something" in xorg.conf. It's really not even comparable.

It's not hard. I love terminal and new possibilities it opens.
But getting vital parts / hardware running for a linux newb is a chore.

---

### Post by LowSky on 2008-03-03
Well in my experience, ATI drivers have always sucked, even in Windows. Nvidia has always worked better with Linux.

But to help you get them working, have you tried a program called Envy to help install the ATI drivers.

I will admit that Gutsy's LiveCD version of Gparted does suck, and has ruined some data on my own hard drive, but it is also your own fault (as was it mine). Before you partition make sure to Defragment the hard drive under Windows, and also make a back up of all your data.

Also why complain about how the install partition editor reaeds the names. Understand it will think you might want to name it differnetly under a different operating system.

for example I have a partion named Ubuntu Media when operating Windows. It called Media in Ubuntu.

Next the "slowness" do you mean the LiveCD? what do you expect running it off a CDROM and RAM only, put the LiveCD on a flash drive annd its much faster. If you meant a full install, turn off some features, like indexing and harddrive mapping. both of which are useless to most users. Also try differnet programs... different programs might fetch differnet results

and as for the mouse you jst need to remap the buttons in you xorg.conf file.

open terminal
```


sudo gedit /etc/X11/xorg.conf
```
now find this part of the coding

```
Section "InputDevice"       
 Identifier      "Configured Mouse"        
Driver          "mouse"       
 Option          "CorePointer"       
 Option          "Device"                "/dev/input/mice"        
Option          "Protocol"              "ExplorerPS/2"        
Option          "Emulate3Buttons"       "true"
EndSection
```

 change it to this

```

Section "InputDevice"        
Identifier      "Configured Mouse"        
Driver          "mouse"        
Option          "CorePointer"        
Option          "Device"                "/dev/input/mice"        
Option          "Protocol"              "ExplorerPS/2"        
Option          "Buttons"               "7"        
Option          "ZAxisMapping"          "4 5"       
Option          "ButtonMapping"         "1 2 3 6 7"        
Option          "Emulate3Buttons"       "false"
EndSection

```

---

### Post by NiceGuy on 2008-03-03
Hurm, I've had a similar experiences with partitioning but in my case it was a bad cd burn/corrupt download (I didn't bother to find out which as I tried on a system known to work, found it didn't and re-downloaded and burned). Maybe run the cd-checker and md5 for the downloaded iso?

Other than that the only thing I can suggest is using the alternative install cd

As others have mentioned, the partitioner works fine for the majority of users so really, as annoying as it is to hear, it must be something to do with 'your end', be it a bad cd or some hardware incompatibility. Try not to look badly on the OS because of a few 'hiccups' on the way. It's the equivalent of blaming the OS for having faulty ram etc. (which seems to happen quite a lot with all OS's).

Keep with it and you'll probably learn a lot along the way!

---

### Post by acsworrell on 2008-03-03
It's actually laughable, the amount of time and effort everyone puts into trashing each other about Winsuck or Linux. Every install I've done with Ubuntu has been flawless. I've installed on a 1.2 Athlon to a 2.2 X64 dual core. All of my installs have gone fine. My partitioning of my Vista drive worked fine, with no crashing. I've operated Winsuck systems for years and just started Linux a month ago. It's been easier to understand and implement and I'm not going back. So you had problems, now either help to solve it, or cower and hide the dark ages.

---

### Post by NightwishFan on 2008-03-03
A couple of problems I had installing Linux.

Open Suse 10.3: Infinite update loop. :confused:
Kubuntu: Refuses to autoupdate, and when I reboot, says nothing to load.

I fixed first one by removing Open Suse. I fixed the second by updating from the terminal. :)

Linux rocks. Peace.

---

### Post by mental_gnome on 2008-03-03
Tee-hee.
Dual monitors are working now.
I can start working at last!

The issues remaining:
* Slow opera tab switching speeds (it has to be instant)

Things to do:
* And I need to start thinking about setting up soundcard drivers too! I've got creative x-fi. Hope wont run into problems there!
* Video codecs & mp3s

---

### Post by miamizsun on 2008-03-04
7.10 Gutsy Gibbon

Noobie here...

Have Windows Vista - used partition feature freed 50 gigs for Ubuntu and 2 gigs for the swap, got some great help from a couple of folks after posting in the Installation forum. After downloading ISO recorder and GG, it installed (dual boot setup) without any snags - whatsoever.

*I'm friggin stoked!*  :mrgreen:

---

