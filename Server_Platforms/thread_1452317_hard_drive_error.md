---
title: "hard drive error?"
date: 2010-04-11
forum: Server Platforms
---

### Post by nipsy on 2010-04-11
Still trying to set up everything in my server tower. I have one drive formatted and ready to go. The other one was giving me issues, so I ran a disk verify and then formatted. The format took 2 hours and this is the box that popped up:

UNEXPECTED SCSI COMMAND FAILURE

TARGET SCSI ID: 0

SCSI CDB SENT: 03 00 00 00 0E 00

HOST ADAPTER STATUS: 00h - NO HOST ADAPTER ERROR

TARGET STATUS: 02h - CHECK CONDITION

SENSE KEY: 04h - HARDWARE ERROR

+SENSE CODE: 02h
+SENSE CODE QUALIFIER: 00h

Can anyone break it down for me and tell me what this means, what I can do to fix it?? I've googled to my little hearts content and I find too many different items that I'm going around my elbow to get to my a**hole..

Running Ubuntu 8.04

Thanks in advance again!

---

### Post by fang0654 on 2010-04-11
Sounds like a drive error, although I'm not 100% on that.

Download and burn:

[Ultimate BootCD]("http://www.ultimatebootcd.com/download.html")

Use it to check the physical hard drive for problems (Do a surface check, etc).  This will tell you whether it's a config issue or drive issue.

Is the working drive on the same controller as the nonworking drive?

---

### Post by nipsy on 2010-04-12
Thanks fang, I'll try that one. Yes the working drive is on the same controller.

---

### Post by fang0654 on 2010-04-12
Ok, that rules out controller error :)

If you get drive errors with the testing, try different cables as well.  I've had a bad SATA cable or two that gave intermittent errors on the drive.

---

### Post by nipsy on 2010-04-23
To solve this one, we booted hard drive on a second computer, tweaked it and put it back in server tower and it runs perfect.

By the by, we have noticed that SCSI IBM hard drives DO NOT like Ubuntu, they get the initrd error. In other words they can't read the cache on the disk. Good thing we have 6 or more hard drives laying around.

Thanks for the help!

---

