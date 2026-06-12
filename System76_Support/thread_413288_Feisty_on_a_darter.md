---
title: "Feisty on a darter"
date: 2007-04-19
forum: System76 Support
---

### Post by Rotarychainsaw on 2007-04-19
It works! Upgraded from edgy tonight, and everything went well. Upon reboot, sound worked and all that. Now wireless can work after suspend by flicking the switch, so thats a step in the right direction. 

Now for the problem. The computer seems to be waiting for the hard drive once in a while. I haven't got to experiment with it too much yet, but it seems like the HD shuts off after a time of no use, and won't come on until like 30 seconds after something is requested. I'll be searching to fix it, but if you all got any ideas as to where to start, I'm all ears.

---

### Post by Liff on 2007-04-19
Yep, running pretty good here too, Except for a problem similar to the one you are mentioning. I hadn't connected the problem to the hard drive, but you're probably right. It just kind of randomly decides that it wants to sit there in a semi-hung state for 30 seconds or so instead of working... I thought at first that the problem may be connected to the nightly build I installed (I think it was Monday's). I'm actually in the process of downloading the final release right now because I didn't want to ask for troubleshooting help for a nightly.

On a semi-related note, I absolutely love my new darter :)

---

### Post by thomasaaron on 2007-04-19
For now, you can work around the problem by leaving a CD in your CD-ROM drive.
The real fix is in the works with Canonical.

Best,
Tom

---

### Post by Rotarychainsaw on 2007-04-19
Really? haha thats weird. I'll try it when I get near a CD. 

edit, Nevermind, still does it on battery.

---

### Post by Rotarychainsaw on 2007-04-19
SO the CD thing does seem to work. Very odd. Is there a bug report on this? I'm curious.

---

### Post by crichell on 2007-04-19
Yes there is a bug report located here:

VERY IMPORTANT: The workaround at the bottom of the report is only for NEW INSTALLATIONS.  If the work around is used on an existing install your system will not boot!

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603)

---

### Post by Rotarychainsaw on 2007-04-19
Hmm, so whats that mean? New ata drivers in the new kernels are a little messed up?

---

### Post by crichell on 2007-04-20
> New ata drivers in the new kernels are a little messed up?

Yeah, the switch to the new drivers are causing the problem - although ultimately it's going to be better.  The problem boils down to the CD-ROM and Hard drive working off of the same channel.

The folks at Canonical have made some great suggestions.  We're working on a quick fix to send down to customers - should be early next week.

---

### Post by Rotarychainsaw on 2007-04-20
sweet.

---

