---
title: "Virtualbox - Ubuntu host and guest = stable?"
date: 2012-04-18
forum: Virtualisation
---

### Post by Sternfan on 2012-04-18
Hi all,

System:  Host is 64-bit ubuntu server.  There are multiple VMs (XP & 2003 server) which run fine.  I set up an ubuntu VM as a test wordpress server and everything appeared OK to start.  After a short while, however, the VM became unstable - locked up, froze etc. - forcing hard reboots and disk checks.  Eventually it got so bad I retired the VM and am in the process of creating a new one.

**My Questions:**

1) When the VM started I got the infamous "I/O cache" warning, but figured that since the message stated that it was turning on the cache, left it alone and assumed it was turned on.  **Even with this message, could the VM I/O cache have still been disabled resulting in the corruption?**  This is my guess, but I am looking for some verification.  *my testing shows that when the VM is started with the warning, if you go into the settings of the running ubuntu VM, the checkbox for I/O cache remains unchecked.  If you shutdown, check the box, restart the VM and check the settings - it is ON.  Looks to me that even if the message states that it is turning on I/O cache, it isn't.*

2) For the new VM I will be enabling the I/O cache from the start.  **How stable is running ubuntu on both the host and guest?**

Hardware notes - host is 64-bit VT capable, two dual core xeons (2ghz each) and 12gb ram.  Storage is raid10 array.

Any help or comments greatly welcome,
Rob

---

### Post by CharlesA on 2012-04-18
I've been running Ubuntu 10.04 (both server and desktop) in a VM for quite a long time with no problems.

I have I/O cache enabled on all my VMs.

The host is running Ubuntu 10.04 on a 3.xGhz i7 with 16GB of RAM.

---

### Post by Sternfan on 2012-04-18
Thanks for the prompt response.  Comforting to know someone else hasn't had these issues.

Rob

---

### Post by CharlesA on 2012-04-18
Try enabling I/O cache and reinstalling the VM and see what happens. If should run fine. :)

---

### Post by OliverHaslam on 2012-04-19
Sorry to butt in, but what's I/O cache and do I need to switch it on? I'm running an Ubuntu 11.10 host and various VMs off it - Ubuntu web server, Windows 7, Windows 8, Windows XP print server.

---

### Post by CharlesA on 2012-04-19
Are you running off an EXT4 partition?

See here:
[https://www.virtualbox.org/manual/ch05.html#iocaching](https://www.virtualbox.org/manual/ch05.html#iocaching)

It should default to on.

---

### Post by anejo on 2012-04-24
> **CharlesA said:**
> Try enabling I/O cache and reinstalling the VM and see what happens.
BIG +1
I 'm running vbox 4.1.12 on 12.04 and its very stable!

---

