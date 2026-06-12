---
title: "optimize windows vista"
date: 2008-04-06
forum: Windows
---

### Post by motoperpetuo on 2008-04-06
my wife has a year-old acer laptop (1.60ghz processory, 2GB RAM) with windows vista home premium preloaded (from one of those ridiculous "restore partitions" they're putting on windows computers nowadays). it's always been sluggish and, until recently, had a lot of trouble properly initializing USB devices. 

vista SP1 took care of the USB problems, but the general sluggishness remains. granted, i think a lot of the problem is her tendency to download sketchy file sharing programs like bearshare (which spybot picks up as malware) and a "mail agent" application that runs in the background and tells her when she's got mail. i'm trying to talk her into NOT installing things like that, but i wonder if there are also some quick, easy tips for getting vista to run a little better. unnecessary services to remove, applications to uninstall, maybe some eye candy that can be switched off to save resources, that sort of thing.

i'm hoping to at least set her up to dual boot with linux mint sometime in the future, but i need to find the time to do the troubleshooting that normally comes with trying to set up linux on a new system first, not to mention the time to do troubleshooting and training as she tries to learn a new OS.

---

### Post by NightwishFan on 2008-04-06
First things to do is to download ccleaner and auslogics disk defrag both fast and free utilities. Run them and then schedule a disk check on reboot. After you reboot type "msconfig" in the search box. Look for starup programs (not services) and disable all the ones you do not need (all of them for me). Then go to advanced system under control panel. Then you can be sure to set the perfomance to best performance then restore the Windows Vista Classic theme.  Now on to the advanced part.

Type services in the search bar. You can disable many but I will cover the basic ones. If you do not use aero disable the "Desktop Window Manager" service. If you have 1gb of ram or less disable the indexing and superfetch services. (Unless you want them.) If you do choose to disable superfetch delete the _contents_ of C:/Windows/Prefetch. All three of these can be safely re-enabled. Then reboot.

Vista should use only about 400mb ram and run much faster.

---

### Post by motoperpetuo on 2008-04-07
i haven't even gotten around to the second paragraph of your advice yet, but my wife says her laptop is running much better now. thanks very much.

it's weird that there's a choice between optimizing appearance or optimizing performance there in system properties. i've never been much of an eye candy guy, so i always turn all that stuff off, but it's bizarre to see that you pretty much have a choice between one or the other in vista.

---

### Post by NightwishFan on 2008-04-07
Indeed. Please do not hesitate to ask if you have any questions, and good luck! :KS

The main killer for Vista is Superfetch/Indexing/DWM. If you do not use them and disable them correctly you should notice a great improvment. They are good features if you make use of them, but if you hardly need them they really drag down performance.

Also you can try enabling advanced performance on your harddrive under the device manager.

---

### Post by sayakb on 2008-04-10
You might try "ccleaner" and "Speed up my pc 3.0". Keep the registry clean, and the file system defragmented. Thats all you could do to make it faster..

---

### Post by timzak on 2008-04-10
> **NightwishFan said:**
> 

Vista should use only about 400mb ram and run much faster.

:shock:

Wow, I've never tried Vista and had no idea how much ram it required, even when pared down!  

My Win2k machines use between 90MB and 150MB (antivirus is basically the difference between 90 and 150).

My WinXP machines at work use between 180MB and 250MB.

My Gutsy machines use between 110MB and 150MB.

All these are ram usage after a fresh reboot.

---

### Post by SEMW on 2008-04-10
> **NightwishFan said:**
> The main killer for Vista is Superfetch ... If you do not use them and disable them correctly you should notice a great improvment. They are good features if you make use of them, but if you hardly need them they really drag down performance..
Are you serious?  Superfetch is the Vista prefetcher.  It's first, last, and only reason for existence is to improve performance.  Disabling it in an attempt to improve performance is lunacy.

---

### Post by IsawSp4rks on 2008-04-10
It's not lunacy.  Superfetch and prefetching algorithms like it (Ubuntu has preload) use system monitoring (metrics) to improve performance by analysing regularly loaded applications and precaching them, on systems lacking in RAM and/or CPU resources this system monitoring aspect can really drag down performance quite dramatically as the machine struggles to balance the load of monitoring, precaching and actually running apps and services that are already putting a strain on limited resources.  Some vendors have been known to ship Vista Basic loaded budget laptops and low voltage CPU limited UMPCs with Superfetch disabled. There's a lot more to knowledge of OS optimisation than taking the vendor's word for it.

---

### Post by Chiko2008 on 2008-04-10
Wow! I didn't know that! o_O

[Ubuntu]("http://www.linux-archive.org/ubuntu/")

---

### Post by Exershio on 2008-04-10
[http://www.speedyvista.com/](http://www.speedyvista.com/)

---

### Post by NightwishFan on 2008-04-10
My Battle for Middle Earth II game always locked up the moment I got in a match when I disabled Superfetch and deleted prefetch performance was increased, and it did not lock up. That is because I only have 895mb ram.

---

### Post by SEMW on 2008-04-10
> **IsawSp4rks said:**
> Superfetch and prefetching algorithms like it (Ubuntu has preload) use system monitoring (metrics) to improve performance by analysing regularly loaded applications and precaching them, on systems lacking in RAM and/or CPU resources this system monitoring aspect can really drag down performance quite dramatically as the machine struggles to balance the load of monitoring, precaching and actually running apps and services that are already putting a strain on limited resources.
All modern OSes have a concept of CPU or I/O 'priority' whereby a background process can run as low priority and thus cede control of the CPU etc. if a process running as higher priority requests it.  I believe the superfetch process runs as 'low' or 'very low' (can't remember which, it's been a while since I've used Vista) for both CPU and I/O priority.  Interestingly, previous versions of Windows lacked I/O prioritising -- all I/O requests were treat equally -- and IIRC, it was introduced into Vista precisely for that reason: to allow the Superfetch process to run as low I/O priority and prevent any such slowdown.

---

### Post by NightwishFan on 2008-04-10
It has its uses but I recommend anyone with less that 1gb of ram to disable unless you run multiple light apps, and not things like games. It will lock up processes that take a lot of ram. Actually I am going to play around with my Vista right now.

---

### Post by IsawSp4rks on 2008-04-11
> **SEMW said:**
> All modern OSes have a concept of CPU or I/O 'priority' whereby a background process can run as low priority and thus cede control of the CPU etc. if a process running as higher priority requests it.  I believe the superfetch process runs as 'low' or 'very low' (can't remember which, it's been a while since I've used Vista) for both CPU and I/O priority.  Interestingly, previous versions of Windows lacked I/O prioritising -- all I/O requests were treat equally -- and IIRC, it was introduced into Vista precisely for that reason: to allow the Superfetch process to run as low I/O priority and prevent any such slowdown.

Scheduling and Dynamic Precaching are not the same the same thing.  All OSes schedule I/O requests (ring prioritization in Windows NT et al is not only for security ya know) and yes Vista's I/O scheduling has improved over XP, though this is derived from 2k3's I/O improvements.  SuperFetch is about preloading RAM with regularly used apps and dlls.  If CPU and RAM resources are low then SuperFetch can and will slow system performance overall.

---

