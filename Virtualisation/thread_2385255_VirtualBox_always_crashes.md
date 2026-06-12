---
title: "VirtualBox always crashes"
date: 2018-02-18
forum: Virtualisation
---

### Post by kazakore on 2018-02-18
Trying to get a VM running, I have tried a number of different images downloaded from [https://www.osboxes.org/virtualbox-images/](https://www.osboxes.org/virtualbox-images/) of both x64 and i386 variety and tried starting them with various different options set within VirtualBox itself and every time my system hangs and completely freezes in less than a second of trying to start it.

System is running Ubuntu Studio 16.04
HP Elitebook 840 G2
i7 5600U
16GB RAM

What can I do to try and get this working?

EDIT: I had done less testing with the 32bit version but playing with more settings after posting this and I can boot 32bit VM if I disable VT-x in the Settings. This setting can not be disabled for 64bit images though! Hopefully this can help us find where to fix matter....

EDIT2: Well it doesn't crash the host system but the OS still doesn't load! Log file below.

[https://paste.ubuntu.com/p/gkBrXSJXN9/](https://paste.ubuntu.com/p/gkBrXSJXN9/)

---

### Post by kazakore on 2018-02-18
OK found some other threads of people with similar issues and it seems the version in the Ubuntu repo just does not work at all!!!

Followed the instructions in the link below and initially was getting a load of other errors, but ones that sounded related to the previous install. Did a full purge of everything related I could and reinstalled version 5.2 and have just booted the i386 VM all the way. More testing to be done but looking promising.

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

EDIT: x64 version working with the 5.2 installed from the above link as well.

Marked Solved.

---

