---
title: "Headless Server Won't Detect Monitor"
date: 2010-08-29
forum: Server Platforms
---

### Post by SoulMazer on 2010-08-29
Hi, I've got a headless server (32 bit 9.04/9.10, can't remember) that started refusing SSH and HTTP connections a few days ago, and I'm just getting around to hopefully fixing it.

The problem is that I can't even connect to the darn thing. I've plugged in a mouse, keyboard, and monitor, but the monitor tells me that it has no signal. I know the monitor works with the computer, as I used the same one to set up the server.

Just for kicks, I even tried to put in a live CD, but that didn't help.

Any ideas on how I can connect to this thing?

Thanks in advance.

EDIT: Okay, I'm connected. After trying a few different cables and lots of button-mashing, I'm in. Now, I have a new problem. The reason it wasn't booting before was because it failed when running an automatic disk check. I tried re-running it "fsck" and I get a lot of errors and exceptions.

EDIT2: I've wiped the machine and installed 10.04, but when I try to update the computer, I get the following error:
> ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
ata1.00: BMDMA stat 0x24
ata1.00: failed command: READ DMA
ata1.00: cmd x8/00:08:80:cb:0b/00:00:00:00:00/e0 tag 0 dma 4096 in
         res 51/40:00:80:cb:0b/00:00:00:00:00/e0 Emask0x9 (media error)
ata1.00: status: { DRDY ERR }
ata1.00: error: { UNC }

I've done some searching and found the bug on launchpad.net here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/569680]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/569680")
I tried uploading my own debug information, but I encountered ANOTHER bug, this time with Launchpad's login service ([link)]("https://bugs.launchpad.net/launchpad-foundations/+bug/556927"). The proposed fix for the login bug requires that I install elinks, which brings me back to my disk error. The errors have officially gone full-circle.

Since reinstalling the OS didn't seem to help, I guess my disk went faulty. It's strange because I've been using this computer for eight or so years.

Let me know if anybody has some ideas about this.

---

### Post by TwoEars on 2010-08-29
Your hard drive is corrupt, you need a new one.

---

### Post by SoulMazer on 2010-09-09
Sorry for the late reply, but I didn't want to respond prematurely. I ordered a new hard drive, and upon its arrival, I figured out my computer (due to its age) only supports IDE hard drives. After I got the correct hard drive, I installed a fresh install of 10.04 Server and it now works like a charm.

Problem solved.

---

