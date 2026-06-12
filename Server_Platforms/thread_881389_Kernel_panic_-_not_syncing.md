---
title: "Kernel panic - not syncing ???"
date: 2008-08-05
forum: Server Platforms
---

### Post by javagamer on 2008-08-05
Hi,
   I recently got a server and quickly installed Ubuntu Server 8.04 on it.  I've set up apache and postfix, but because my ISP currently blocks those ports it has been sitting around idle, occasionally serving pages to computers on my lan.  I routinely pull up the site it's hosting to check that everything's alright.
   Twice it has crashed in less than a week.  The first time I couldn't figure out what happened, so I made sure to leave a monitor attached to the server and I had it watch (w/ less) apache's error.log to see if I could trace down what happened.  Just recently I discovered my site had become unresponsive again, as soon as I turned the monitor on I could see a kernel panic.
   Printed right after less's "Waiting for data..." message was```
[100415.510674] BUG: workqueue leaked lock or atomic: events/1/0x000000b4/10
[100415.510724]     last function: vmstat_update+0x0/0x30
[100415.510952] BUG: scheduling while atomic: events/1/10/0x000000b4
[100415.729770] Kernel panic - not syncing: Fatal exception in interrupt068:f707
```
   Can anyone tell me what this means?  I got the server second-hand, so none of it is brand new.  It's a Dell Poweredge 420sc with 4GB RAM, 80 GB HDD, and a Pentium 4 2.8 Ghz processor.  I don't believe I installed anything unusual, the most obscure thing I have is Django, but that wasn't running (I believe mod_python for apache was though).  Does anyone know what's causing my problems and how I could fix it?
   Any help is appreciated.  Thanks in advance.

---

### Post by javagamer on 2008-08-06
Update: I found some posts online which suggested disabling everything I'm not using in the BIOS.  As soon as I tried starting it up it made several beeps, the light on my monitor went red (it's an old CRT monitor, not sure what the light meant), and the fans turned on way high.  This looks more serious than I thought.

New Update: After unplugging everything, opening it up, and replugging everything I still got the same problem.  But, once I unplugged the HDD and CD/DVD drives I was able to boot into BIOS.  (In BIOS the only errors reported from all the beeping were keyboard errors and I think some post errors, nothing with much information)
I just reconnected the CD/DVD drives and I'm running the memtest from the Ubuntu Server CD.  Afterwards I'll try replugging to hard drive.

---

### Post by javagamer on 2008-08-12
Update: 48+ hours later memtest still had no errors so I decided to restart it with the hard drive attached.  Everything seemed fine for a while and it just worked.  A few days later it froze up again (probably within hours of closing the case a little more, maybe it overheated), something from the kernel about ending an idle task or something (I forgot to write it down before shutting it off).  Now it continues to just lie dead on my floor beeping.  Can anyone help me revive it?  And, if I manage to get it to boot into the OS (it currently won't even get to the BIOS) are there logs somewhere that would be useful?

---

