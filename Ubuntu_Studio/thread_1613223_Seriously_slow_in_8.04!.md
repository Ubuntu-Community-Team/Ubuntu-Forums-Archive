---
title: "Seriously slow in 8.04!"
date: 2010-11-04
forum: Ubuntu Studio
---

### Post by Bi11yy on 2010-11-04
I inherited an old lappie from a friend and found it to be too slow for Windows Vista (dont have XP), and heard that Ubuntu is great for older hardware. Installed UbStu 10.10 on it and the thing was painful to operate. Simple tasks were mind numbingly sloooow. So figured I'd roll back to an older version, 8.04. Same thing! The lappies specs are a Celeron 2.8Ghz with 768 megs of ram and a 40 gig 4200rpm drive. I cant find a definitive Ubuntu 8.04 sys req, but I've seen people install on PII with 933mhz and 128 megs of ram!
 
 This thing has to work, it cant be that slow! Its a Toshiba Sattelite A45-121. Am I missing something? I'm not exactly proficient with Linux platforms but I've got loads of experience with many OSes (all windows, OSX). I'm no dummy!

 My example: on a fresh boot, it takes Firefox some 25+ seconds to load, 20+ to shut down. Ardour takes almost a minute to load fully! Is this right??? What can I use to monitor resources?

 I've finally found some info about 8.04's sys reqs. A PIII 800mhz with 512megs. Seriously. I should be able to do better than this.

---

### Post by yiannis66 on 2010-11-04
try puppy linux is very light
[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm")

---

### Post by Bi11yy on 2010-11-04
Ok, I've found System Monitor, and as the lappie is updating from the net(and thats the only thing running by me at least), this thing is at 98-100% cpu uasage. Memory is only 32%. Thats crazy! a 2.8GHz proc strains that much under UbStu 8.04??? How are all these other people running it on PII and what not?? Am I missing a processor driver or technique? Please help!

---

### Post by Bi11yy on 2010-11-04
> **yiannis66 said:**
> try puppy linux is very light
[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm")
I'm aware of it, but I want UbStu, I do music and would like to be able to do small stuff while at work and whatnot. Besides, I'm convinced it cant really be that slow. I'm doing something wrong, I just don't know what....

---

### Post by cchhrriiss121212 on 2010-11-04
100% cpu usage indicates that something is wrong there, check your applications tab in system monitor and post what is using the most cpu when nothing is running. It should not be like that all the time.
 
Unless it was the updates using the cpu which can cause temporary spikes even on my system (dual core Athlon 3.3GHz), which is due to unpacking I think.

8.04 is 2 years old now and will not have up to date software. What I recommend you use is a newer version with a lighter desktop environment. Lubuntu 10.04 would be perfect, and you can install all the same music packages individually or with the studio meta-package. Avoid new Ubuntu releases as they will always be buggy for several months after official launch. 

You can check [this page]("http://ubuntuforums.org/showthread.php?t=1350304") for PPAs full of useful up to date music software. Also you will be better off installing an rt or low latency kernel which will help your latency with audio work, these should be in the default repositories for 10.04. 

Bear in mind that as a new user it will take a while to just get your system set up to do any audio work, but once you know how, Linux is a very good audio platform.

---

### Post by trulan on 2010-11-04
I'll second the recommendation for Lubuntu 10.04 + the apps you want.  The repositories will be the same as what you get with Ubuntu Studio, you'll just have to choose the apps you want (or install the ubuntustudio-audio metapackage, as well as ubuntustudio-plugins, ubuntustudio-video and ubuntustudio-graphics if you want them.  Don't install ubuntustudio-desktop as that will pull all of gnome and you don't necessarily want that if you're using Lubuntu.

Also, on another note, with your current installation you could check your CPU scaling.  It might be clocking your CPU way back, resulting in everything being much slower than it should be.
[http://wlmtips.com/2008/06/13/enable-cpu-scaling-in-ubuntu-linux-friday/](http://wlmtips.com/2008/06/13/enable-cpu-scaling-in-ubuntu-linux-friday/)
Of course the specifics will vary from one release to another, this tutorial may not be the best one for you, and your CPU may not even support scaling so this may all be irrelevant.  But maybe it will help too, so there it is.

---

### Post by The Foz on 2010-11-04
It is very common for old laptops to have hardware faults. I have this problem with my own laptop.

Use the 'top' command in a terminal to find out what is using all your CPU cycles (the system monitor actually uses a lot of capacity on an underpowered system).

Also, use the 'dmesg' command to find out if there are problems loading drivers for some of the hardware (e.g. a built-in web-cam). If so, you can blacklist the driver (so it isn't loaded) in /etc/modprobe.d/blacklist.conf.

Another possibility is that you don't have the right driver for your graphics card/chip. If scrolling is slow and jumpy, this is the likely cause, and would mean that all the rendering is being done in software instead of using the hardware. Generally the 'top' command will show "Xorg" as the main user of CPU cycles if this is your problem. You can fix this by editing /etc/X11/xorg.conf, but make sure you save a backup copy of the file before you start messing with it.

---

### Post by sgx on 2010-11-04
> **Bi11yy said:**
> I'm aware of it, but I want UbStu, I do music and would like to be able to do small stuff while at work and whatnot. Besides, I'm convinced it cant really be that slow. I'm doing something wrong, I just don't know what....
This Puppy is a audio/media distro based on Lucid, can test as live CD, I just install on a usbstick.

[http://www.murga-linux.com/puppy/viewtopic.php?t=60483](http://www.murga-linux.com/puppy/viewtopic.php?t=60483)

---

### Post by Bi11yy on 2010-11-04
Wow, guys thanks so much for the help. Let show you what i got: I've searched the forums here and there are quite a few 2.8Ghz Celery users out there that seem to have the same problem as me with no noted fix, that could be a problem, something hardware native.
 Mind you I'm still new to this, and wasn't aware I could get the Studio packages separately for other version of Ubuntu! From what I can tell, PuppyStudio looks interesting. Im gonna give it a try, it seems easy to do right now. Im tired and I've been up all night trying to  figure something out. I'll let you guys know whats up ina few days.

---

### Post by Bi11yy on 2010-11-04
I gave up on UbuStu, but I'm running PupStu now. Its way better but still chunky and slow. I'll cover that in Puppy forums. thanks for the help!

---

