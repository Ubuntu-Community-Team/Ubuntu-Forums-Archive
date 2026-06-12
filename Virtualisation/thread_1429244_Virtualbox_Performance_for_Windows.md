---
title: "Virtualbox Performance for Windows"
date: 2010-03-13
forum: Virtualisation
---

### Post by areteichi on 2010-03-13
Hello everyone!
I've been testing and playing around with Virtualbox for the past few days and I have to say, I'm a bit disappointed so far with its performance in Karmic. I am thus wondering if you guys are having the same experience as me with using Virtualbox.

1. Windows XP runs much SLOWER when I enable two cores and VT-x/AMD-V option. In other words, XP runs much quicker and snappier if I just set the number of CPU to 1 and disable VT-x/AMD-V.
First of all, I tried disabling these options after reading this thread:
[http://forums.virtualbox.org/viewtopic.php?f=2&t=13720&start=15](http://forums.virtualbox.org/viewtopic.php?f=2&t=13720&start=15)
where some people make the following comments.
> I was correct in my thinking that disabling VT-x/AMD-V on my X2 5400+ sped up the guest by about 300% when doing anything that required processing power even if it was opening up a second browser window.
> I can confirm this. Using VirtualBox 2.2.2, deactivating VT-X/AMD-V increases performance in my XP guest dramatically.
While these comments are made in regards to the older versions of Virtualbox, they well describe my experience with Virtualbox thus far so I'm curious to hear what you guys' experience is with Virtualbox and Windows XP as guest OS.

2. I gave a try at Windows 7 in Virtualbox since I was disappointed with the performance of XP, and Windows 7 seems to run quite smoothly with two CPUs enabled and the VT-x/AMD-V option turned on. Although it is much more memory intensive, I was surprised to find that I found the performance of Windows 7 in Virtualbox about the same as Windows XP. I would have thought that Windows 7 wouldn't run as well given that it's is more newer and thus 'heavier' and more hardware-intensive.

Are these common experiences with Windows 7? Is there a way to improve performance (XP or Win 7)?

---

### Post by hantms on 2010-03-18
XP runs just fine, and requires much fewer resources for both memory and disk.  I run an XP VM so I can run Outlook, MS Project, Visio and streaming TV.

I gave it 512 MB memory which I never use up, even when working on heavy Word files with Outlook open.  Looking at the list of services with a critical eye means the memory used on startup is around 70MB only.

You won't hit those numbers with Windows 7. :) To be honest Windows 7 doesn't add much that isn't either in XP SP3 or Ubuntu or both. (Ok, elevating to Admin is smoother on Win7, but I can work around that.)

SP3 is also quite secure if you run as a restricted user, install patches monthly and do a weekly virus scan just in case.  And of course you do any recreational web browsing safely in Ubuntu but that almost goes without saying. ;)

---

### Post by hantms on 2010-03-18
By the way: Most performance improvements you can achieve are just regular Windows XP tips & tricks.  

Specifically, things like:

 - Be critical of any anti virus scanner you use. Some are incredible resource hogs, like AVG for example. Decide if you even need real-time monitoring; in my opinion you can go without it if you generally practice safe computing. (not running as Administrator or a power user, applying patches, only use your web browser for trusted sites.) Then I run Trend Housecall once a week. Never found anything untoward yet.

 - Windows update service: You don't really need to run this all the time. I run it manually after Patch Tuesday, and of course you hear about anything urgent anyway.

 - Windows Search : This really isn't pretty the amount of resources this uses.  Sadly, having proper search in Outlook depends on this.  Best workaround that I found is to get rid of Windows search and use the excellent (and free) 'Xobni' plug in for Outlook instead.

 - Turn off anything else that wants to run all the time but that you don't need all the time. It's amazing how many software vendors believe that you want to run their stuff all the time, or stay in the system tray to save half a second in start-up time, or be informed of updates the second they release them. ;)

I still dual boot into Windows 7 (company supplied so I need to keep it around) and a lean, mean XP SP3 install under virtual box is SO much faster than Windows 7 native you won't believe it.

---

### Post by mcooke1 on 2010-03-19
I have a virtual XP in 9.10 64 bit and during installation I just went with all the default settings and it performs better than I have ever seen XP perform on the the older Laptop it was installed on before. I have installed windows media player 11 and IE8 and the performance has amazed me. Everything works well downloads and updates etc.

---

### Post by TheFu on 2010-03-19
You realize that WinXP requires a re-installation to switch from 1 CPU (or 1 core) to 2 cores. The HAL installed is different. There is a guide someplace that describes how to swap the HAL post-install. I never tried it. [http://support.microsoft.com/kb/896256](http://support.microsoft.com/kb/896256) That article also says SP2 is required for multi-CPU systems.

IME, disk performance mattered the most for how much WinXP performed. It was never "speedy", but it **felt** just as fast as a 3yr old PentiumM 1.6GHz laptop w/ 1.5GB RAM did natively. It was very acceptable for running MS-Office and Visio apps.  I've never used vbox with Linux as the host, but I have used it with both Vista and Win7x64 as hosts. I wouldn't call either hosts "stable" since a weekly reboot was needed before the entire system would lock up.

Other settings for performance (personal choices):
- ICH6 disk controller
- Intel PRO/1000 MT for every NIC
- 128MB Video RAM
- 1GB+ of RAM for the VM

---

