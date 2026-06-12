---
title: "avg for linux"
date: 2009-11-24
forum: Security
---

### Post by stp1974 on 2009-11-24
hi everyone....

i am a complete new linux user as of today.  absolutely no experience!!!

i just installed avg anti virus for linux.... i think.  i downloaded and clicked to install, but i cant find it anywhere.  it is not showing up on my desktop, or in any of my folders.  when i went to install again, i was told that it was already there.  

how am i supposed to use it or run it, if i cant find it???

maybe this is a very dumb question, but i have used windows now for years and i am stumped.

thanks.

---

### Post by lisati on 2009-11-24
The latest version of AVG for Linux that I've looked at is command-line only. Try this in Applications->accesories->terminal for more information (press "q" to quit):
```
man avgscan
```

---

### Post by aust77 on 2009-11-24
Hello stp1974:

Welcome to Linux! I am glad you chose Ubuntu, as it is definitely a great software distribution. We have all been new at some point, so do not feel embarrassed at anything, you will learn in time. 

Your problem is very simple. Although this is not a direct solution to your problem, it should help you solve it and many others. 

Solution: TERMINAL
The terminal is a great place to be in Ubuntu. A lot of key commands and actions are run from there. In Windows, it is more self-explanatory, but in the end using a terminal will get things done faster and easier. In order to solve countless problems, you need to become acquainted with basic actions for now, such as locating a file, running a file, or making a file executable (e.g. .bin). The Ubuntu Guide for using a terminal is found here: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

In direct relation to your problem, you need to be more specific. What type of file is the installer? If I know that I might be able to provide a more clear solution.

---

### Post by steve161 on 2009-11-24
Besides the inevitable question as to why you need an antivirus, you could probably create a custom launcher for the application on your desktop or panel.  Right click on panel, add to panel,  custom  application launcher, add.  I'm not sure of this, but the command may be /usr/bin/avggui.  Also check your menu under applications and see whether it is listed under accessories.

---

### Post by lisati on 2009-11-24
I just remembered another discussion about AVG earlier this year. The stuff starting at page 37 of said discussion might be of interest:
[http://ubuntuforums.org/showthread.php?t=136064&page=37](http://ubuntuforums.org/showthread.php?t=136064&page=37)

---

### Post by stp1974 on 2009-11-24
thank you for your help... i found the terminal... however it is going to take some time to learn how to use this.  it does not seem that AVG for linux is doing a constant (real time) scan of your system while you are browsing.

do either of you know of one that does.  maybe one that has gui too it so it feels more like a windows application.  at least i can use that while i learn how to use the terminal.

another question... how do i uninstall the AVG???? :(

---

### Post by stp1974 on 2009-11-24
i dont need an anti virus scanner???? isnt that rule one while online??

---

### Post by Wiebelhaus on 2009-11-24
Sorry but AVG sucks , Try [Bit defender for Unices]("http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html") Much better , much easier to use and just an all around better offering , it's free for home use with registration , I use it for Server , Work Stations and on personal PC's.

Cheers.

---

### Post by steve161 on 2009-11-24
No, you really do not.  There are a couple of good stickies in the security section of the forums, courtesy of bodhi.zazen and aysiu.  You certainly do not need real-time protection to eat up memory and cpu.  I am not sure one even exists for linux desktops.

---

### Post by stp1974 on 2009-11-24
> **Wiebelhaus said:**
> Sorry but AVG sucks , Try [Bit defender for Unices]("http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html") Much better , much easier to use and just an all around better offering , it's free for home use with registration , I use it for Server , Work Stations and on personal PC's.

Cheers.
thanks for the hint.  how about un installing avg.  i cant have two running.  do i have to use the terminal to un install??

---

### Post by Wiebelhaus on 2009-11-24
> **stp1974 said:**
> i dont need an anti virus scanner???? isnt that rule one while online??

It's very sensible to proactively protect against malware , even if it can't damage ***_your_*** system you could potentially help propagate the malware by inadvertently moving it via removable media or online sharing to someone not as well protected as yourself.

But as others will try to convince you , no it's not a necessity.

[Check this out:]("http://www.hbclinux.net.nz/HBCLUG/osc-tut/osc-sec.pdf")

---

### Post by stp1974 on 2009-11-24
> **Wiebelhaus said:**
> Sorry but AVG sucks , Try [Bit defender for Unices]("http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html") Much better , much easier to use and just an all around better offering , it's free for home use with registration , I use it for Server , Work Stations and on personal PC's.

Cheers.
i went to bit defender website and took a look.  maybe you can help me with this.  i dont see Ubuntu as one of the supported linux distributions.  are you using this software on Ubuntu??

**Supported Distributions: **
RedHat Enterprise Linux 3 or newer 
SuSE Linux Enterprise Server 9 or newer 
Fedora Core 1 or newer 
Debian GNU/Linux 3.1 or newer 
Slackware 9.x or newer 
Mandrake/Mandriva 9.1 or newer 
FreeBSD 5.4 or newer

---

### Post by Thaery on 2009-12-13
The Debian version should work as Ubuntu is based on Debian

---

