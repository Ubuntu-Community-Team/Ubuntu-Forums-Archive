---
title: "No installable kernel was found in the defined APT sources (Ubuntu Server 11.10)"
date: 2012-04-01
forum: Server Platforms
---

### Post by RopeNL on 2012-04-01
Hi Guys,

This question is related to this thread [http://ubuntuforums.org/showthread.php?t=1925460](http://ubuntuforums.org/showthread.php?t=1925460) so if you're wondering why I had to re-install this is why.

Anywho. 

I was re-installing Ubuntu Server like 4 days ago and everything was all nice and dandy till I got this error-message: " No installable kernel was found in the defined APT sources.". 

Which I thought was pretty odd since I got Ubuntu Server 10.04 LTS to work just fine before. So I thought it could be the installer voor 11.10 itself so I used 10.04 and 11.04 to no avail. I got the same error..

This keeps happening during the base system install. This bug basically describes the same problem: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/947905](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/947905) . Though I'm using the Pendrive USB installer.

How do I solve this? Is something wrong with the USB installer?

Thanks in advance, Rope.

P.S. This is my entire hardware-setup: [http://nl.hardware.info/wensenlijst/10183/rope/streaming-setup](http://nl.hardware.info/wensenlijst/10183/rope/streaming-setup)

---

### Post by RopeNL on 2012-04-03
No-one? I really looked for an answer all over the internet and I can't find a solution anywhere. Come on guys. I thought that Linux based OS's were know for their community. I didn't get an answer on the other topic as well..

---

### Post by gordintoronto on 2012-04-03
Here's a suggestion: install Ubuntu Desktop, and add the server modules you need. Ubuntu Server has a small advantage if you're running a high-volume web site or heavy-duty database, but Desktop is a lot easier to use!

I assume you took the 64-bit version?

By the way, the Ethernet controller on your motherboard has some issues with some versions of Ubuntu. I'm not sure of the details. My desktop system has the same chip, but I have never plugged in an Ethernet cable...

Oh, Google turned up this thread which might help you:
[http://ubuntuforums.org/showthread.php?t=1550587](http://ubuntuforums.org/showthread.php?t=1550587)

---

### Post by RopeNL on 2012-04-04
> **gordintoronto said:**
> Here's a suggestion: install Ubuntu Desktop, and add the server modules you need. Ubuntu Server has a small advantage if you're running a high-volume web site or heavy-duty database, but Desktop is a lot easier to use!

I assume you took the 64-bit version?

By the way, the Ethernet controller on your motherboard has some issues with some versions of Ubuntu. I'm not sure of the details. My desktop system has the same chip, but I have never plugged in an Ethernet cable...

Oh, Google turned up this thread which might help you:
[http://ubuntuforums.org/showthread.php?t=1550587](http://ubuntuforums.org/showthread.php?t=1550587)

Thank you so much for your reply! I'll try that.

Yes I took the 64-bit and even tried the 32-bit one time out of despair.

I had the cable plugged-in from the very start and at my first installation of Ubuntu Server there were no problems at all. Never lost connection or anything.

That solution doesn't really apply because I don't have a CD-drive ;p. But I'll see if It applies in some way or another.

I'll post my progress here for anyone who's also looking for a solution :).

Thanks again for the reply!

---

### Post by RopeNL on 2012-04-05
Well.. I found the problem for my case. There was something wrong with the USB-stick itself. I tried the installer on a different USB and it worked.

Thanks for the help anyway :).

---

