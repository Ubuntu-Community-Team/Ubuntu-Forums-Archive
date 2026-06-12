---
title: "Linux Hardware Test Live CD."
date: 2007-01-07
forum: The Cafe
---

### Post by Sunnz on 2007-01-07
Allow me to just quote myself:> **Sunnz said:**
> [QUOTE=Phosphoric;1958064]I would be careful about using the Live CD to verify hardware compatablity.  On my PC the Live CD worked perfectly with my Ethernet and Sound card, the installed version did not and the only way I can use Ubuntu is to replace both cards.:(
Maybe it would be possible to create a Live CD specifically to test hardware support, not just for Ubuntu, but Linux with free drivers in general?

It should include a bunch of tools to inspect, probe, and test hardwares specifically, it should includes the latest database of what's available, and should new types of hardware is encountered, it can save this new hardware's information to an USB stick.

Maybe it could be a CD that can boot kernel and load modules, drivers, etc; from a USB stick, so that when new kernel comes out, you don't need to burn a new CD, but simply update what's on the USB stick.[/QUOTE]It seems a few people liked the idea, great!!!

So it must be started somewhere... so I guess I'll just ahead make this thread.

I guess first we need to document what we want in the Live CD and what we need to accomplish it.

First, we need to detect hardwares on the computer, some example tools suggested by encompass are:
lspci
lsusb

I guess we can look at how the Ubuntu hardware detection works as well...

Finally, may I just suggest a mission statement of the Live CD:

At the most basic level, this live cd shall be 386 compatible, be able to boot up in a live environment with or without X.

Once booted up, the Live CD has a set of tools to detect available hardware components, and reports available free drivers, available non-free drivers, and their level of support of the driver offers to the hardware component.

A database of known drivers may be optionally loaded and saved to a USD stick.

---

### Post by maniacmusician on 2007-01-07
you may have to write some of the software yourself or get someone to write it for you, as I don't think there will be anything with specifically what you're looking for; especially regarding the part about available free/non-free drivers. It'd be a good idea to get a hold of ubuntu/linux's hardware detection system. as that will at least try to "choose" a driver for each piece of hardware. and you can modify it to, at the same time, print selective parts of the output to a text file. That's all just theory though, and it could just be far fetched. 

I hope you can code though, because you need very specific applications that may not exist. Good luck nevertheless, its an awesome initiative.

---

### Post by Sunnz on 2007-01-07
Yes, I can code, and I know what you mean... however, I need time...

Hopefully I am not the only one on this!!! Or maybe my initial idea isn't that good and needs refining?

---

### Post by migla on 2007-01-07
Not exactly what you're talking about, but to check for hardware compatibility with only open source drivers and stuff, there's [gNewSense]("http://www.gnewsense.org/"): 
> A GNU/Linux project, to take all the binary blobs out of a rather popular distribution and make it all free.

---

### Post by vjones777 on 2007-12-25
I like the idea of a tool (in the form of a live CD or whatever) that will test the hardware and report on it's compatibility with linux.

A couple of points:
[LIST]
[*]Open source
Is there any real need to restrict the drivers to open source?  I suspect that most potential linux users that can access a device just want to know if it can be used or not, regardless of the politics. e.g if you have a friend that wants to try linux on their laptop, do you tell them "sorry, theres no open source solution" ?   (However, I feel strongly that if you are going to order hardware, its good to do so from manufacturers that actively support linux).
If such a project were launched, it would be an idea to include both closed and open source drivers, and let the tester choose if they want to filter the results.

[*]Ubuntu liveCD
> **Sunnz said:**
> 
 Originally Posted by Phosphoric  [View Post]("http://ubuntuforums.org/showthread.php?p=1958064#post1958064")
I would be careful about using the Live CD to verify hardware compatablity. On my PC the Live CD worked perfectly with my Ethernet and Sound card, the installed version did not and the only way I can use Ubuntu is to replace both cards.
I think that if the live CD can use hardware, then the install to hard drive must be missing something.  There are reports of this happening (I quote an example below), but if this is the case there is probably something wrong with one of the configuration files (which one will depend on the hardware and the desktop - eg in gnome it could be in gconf.  I don't know about KDE.
[/LIST]

The following is lifted from [Linux Format magazine]("http://www.linuxformat.co.uk") (a good mag BTW, well worth a look -*I'm not affiliated etc*.)  
> 
I have Ubuntu 7.04 Feisty Fawn installed on a Sony VAIO VGN-FJ250P laptop. I'm satisfied with almost all aspects of this distro, with just one or two niggling problems. The one I've been putting the most effort into recently regards OpenGL. It seems not to work on this Linux system. I know that it's supported by the Intel video chipset, because I dual boot with Windows XP Pro, and OpenGL applications run fine there.

One of the affected applications is Planet Penguin Racer, which ran fine on the Live CD but doesn't run when installed on the hard drive. Attempting to run it from the menu produces nothing, while attempting to run it from the command line in a terminal produces the following error message:

    *** ppracer error: Couldn't initialize
    video: Couldn't find matching GLX
    visual (Success)
    Segmentation fault (core dumped)

Jim Smith

The good news is that OpenGL works on your hardware with the Live CD, so the hardware is supported and the software present on the CD. This is a configuration problem, almost certainly in xorg.conf, caused by the installer not setting up your graphics card correctly.

Boot from the Live CD, mount one of your hard disk partitions or a USB pen drive, and copy /etc/X11/xorg.conf to it. Now boot from your hard disk and compare its copy of xorg.conf with the one you just saved.

The most likely cause is that your hard disk version of the file is either using the wrong driver (the Driver line in the Device section of the file) or that the GLX module isn't being loaded. Before you make any changes to this file, save a backup copy: you don't want to make things worse.

The correct driver for your hardware should be i810, although using whatever is in the Live CD version of the file will work. The GLX module is loaded by including this line in the module section of xorg.conf:

Load "glx"

If both of these are set correctly and OpenGL doesn't work, you could work through the two files, looking for differences and trying to identify which one is the cause. Or you could simply replace the installed file with the Live CD version, knowing it will work. NV

---

### Post by GreyCat on 2008-12-24
Well, it's a pretty old thread, but I just wanted to reply with one possible solution here: [Inquisitor]("http://www.inquisitor.ru/"), a linux hardware stress testing platform, has separate Live CD version. It sports more than 25 tests and could be useful to test a machine without OS.

---

### Post by MaxIBoy on 2008-12-24
If you want a good distro to use as a basis, Knoppix is legendary for its hardware detection.

---

