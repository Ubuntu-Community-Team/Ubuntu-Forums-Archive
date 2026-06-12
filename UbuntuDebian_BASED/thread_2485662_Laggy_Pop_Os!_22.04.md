---
title: "Laggy Pop_Os! 22.04"
date: 2023-04-05
forum: Ubuntu/Debian BASED
---

### Post by frenchynerd on 2023-04-05
I'm trying to identify if the system lag that I have on my Pop_Os! 22.04 machine is due to software, hardware or the Os itself.

Some times, it runs fine, other times, everything is slow, buttons are unresponsive, windows freeze, apps don't launch.

Intel Core i5-3550 16 Gb RAM 2 Tb SSD.

The PC is used as a media station for my television. I will watch videos online on it or play music. I will also access it via TeamViewer when I'm outside of home. Yesterday, when using TeamViewer, the whole system froze and I had to do a hard reset when I came back home. Before, though, the system did stay powered on for more than 20 days.

I also run a Plex server on it for my friends (reason why the machine is always on), it rarely happens that more than 2 people are connected to it at the same time. The files for the Plex are on an HDD that is connected with an USB docking station for hard drives. The files are also synced with Mega. 

I've tested the Ram with the memtester command line tool, everything was fine. The SMART self test for the SSD didn't show anything wrong.

I use the Vitals gnome extension to monitor the use of system resources at all time. CPU and RAM are always below 50%. 

I am willing to change Os for Ubuntu or Mint if really necessary, as I saw different people having lag issues on Pop_Os, but it would be a huge pain in the ass to reconfigure everything. Also, if it's due to software or hardware, changing Os won't solve the problem.

---

### Post by arius88 on 2023-04-09
I've also got Pop!_OS 22.04. It's running on an old machine and several times a day it just grinds to a halt. I can move the mouse around, but nothing responds. If I press Ctrl + T or Ctrl+Alt+Delete, it doesn't respond until the system unfreezes. Sometimes it freezes for 30 seconds, typically about 10 minutes, sometimes it freezes for so long I have to manually reboot my PC. It usually happens if I make a video fullscreen. Seems to get worse the longer the machine is up and running. I thought it was just my crappy HP computer that someone threw out, but if others are having the same issue, it might be Pop OS itself.

---

### Post by bbs-sysop on 2023-10-17
I am also on Pop!_OS 22.04 on a 3yo System76 Thelio Major. I noticed things would freeze up to the point I would have to reboot ~1 time every 2 months or so. I recently upgraded the RAM from 16GB to 128GB. Everything is running like new again. Not sure if you can add any more RAM but it seemed to help me.

---

### Post by guiverc on 2023-10-17
Have you explored hardware issues?, for example what types of drives are you using?

The *cheaper* drives such as WD Green (*spinning rust type*) came with a longer warranty intended for *light* use. To prevent warranty claims, the drives would retry for longer before reporting errors; which can cause the drive to *pause* during *retries* and often hangs the system (*as it has to wait for the drives to respond*). If you monitor the SMART you can usually detect when these issues will occur (*error counts increasing when compared with last check*), and replacing the *slowly dying* drive will resolve the situation. These drives were not intended for *constant* server type use where *performance* was intended. Drive issues such as this are hard to detect in system logs, as the drive performs normally (*it's just responding very slowly*).

If it's the system, clues should exist in log files, though if the issue is only specific apps; you may need to tell those apps to record log files, or start them in terminal & save the messages appearing on screen in a log yourself. eg. I've had an issue lately with `firefox` where it fails to respond on occasion or becomes super laggy.. I've run it from terminal which currently shows no messages as I use it normally; when the laggy problem occurs, within a few seconds *timeout* errors start appearing on that window showing a problem the app is having. In my case; I get the same here on Ubuntu, or on another box running Debian *trixie* too.

I'm only superficially aware of the many changes in Pop OS, so can't help there.

---

### Post by ajgreeny on 2023-10-19
With the hardware you show in your post I really don't think it is lack of RAM that is freezing your system; I have only 8G RAM and I run an Emby Mediaserver, similar in many ways to Plex and I never see any freezes in my Xubuntu 22.04.

What are you actually doing when it freezes? Is there any pattern that you can see?

---

### Post by bbs-sysop on 2023-10-19
Right after I posted saying I have had no issues with Pop_Os! 22.04, I started to use the Zoom Accessibility feature. Most things work fine but dragging and dropping and screen capture does lag. Disabling Zoom fixed the issue.
I don't expect that you are using any Accessibility features but just thought I would through that out there.

---

### Post by TenPlus1 on 2023-10-20
It could be a memory leak somewhere in the system which gradually fills up available ram, slows the system down when using virtual memory and eventually halts.

---

