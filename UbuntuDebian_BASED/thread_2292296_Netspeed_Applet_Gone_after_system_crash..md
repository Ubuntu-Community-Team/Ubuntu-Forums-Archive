---
title: "Netspeed Applet Gone after system crash."
date: 2015-08-26
forum: Ubuntu/Debian BASED
---

### Post by Thehandyman1957 on 2015-08-26
Hello all.  I am running Ultimate Edition 4.2 [B]
Release Base[/B]: debootstrapped (Ubuntu 14.04 Trusty Thar tree)
**Environment(s)**: Mate 1.8.0

I was working in the Synaptic Package Manager picking some things for Wine and my system froze.  I had to do a hard reset and now my Netspeed Applet is gone.  I tried to reinstate it but when I go to "ad to panel" and scroll down it is not there.  I tried to reinstall it through Synaptic package manager but it does not come back even after restarting the computer.   It says it's there but?

Any help would be great.

---

### Post by cariboo on 2015-08-26
Start in recovery mode and run:

```
Fsck /dev/sdX
```

where /dev/sdX = the partition you Ubuntu installed on.

---

### Post by Thehandyman1957 on 2015-08-27
Very new to Linux, What is recovery mode? And where would I find it?

---

### Post by howefield on 2015-08-27
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by Thehandyman1957 on 2015-08-28
Nice, my thread gets moved and now no one see's it.  Thanks a lot : (

---

### Post by QIII on 2015-08-28
Although we are happy to have users of other operating systems ask questions here, the Ubuntu Forums exist primarily to provide support for Ubuntu.  Your thread was moved to the appropriate subforum.

Ultimate Edition is based on Ubuntu, but is not a recognized Ubuntu flavor.

UE appears to have its own forum at [www.forumubuntusoftware.info](www.forumubuntusoftware.info).  You may avail yourself of that resource if you find the Staff's action to have been unacceptable.

---

### Post by Rob Sayer on 2015-08-30
Besides you could have searched "ubuntu recovery mode" in the same amount of time you spent complaining.

---

