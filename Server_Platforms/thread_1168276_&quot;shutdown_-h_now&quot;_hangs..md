---
title: "&quot;shutdown -h now&quot; hangs."
date: 2009-05-23
forum: Server Platforms
---

### Post by japtar10101 on 2009-05-23
I have a Ubuntu Server Edition running via terminal-only.  When I run either "sudo shutdown -hP now" or "sudo shutdown -h now", it throws an error saying the IDE device is unreadable, then hangs without turning off:
```

$ sudo shutdown -hP now
* stopping ClamAV
* stopping MySQL
* Saving system clock
* Asking all remaining processes to terminate
* All process ended within 2 seconds
* Deconfiguring network interfaces
* Deactivating swap
* Unmounting local filesystems
* Will now halt
halt: Unable to iterate IDE devices: no such file or directory
[182.820656] System halted.

```
It's clear at this point that the system no longer detects for input, so it's completely unresponsive, and I have to physically press the on/off button to turn the server off.

Reboot works fine, to let you know.

Kind of strange it unmounts the filesystem first, then throws the error there's no file/directory.

---

### Post by koenn on 2009-05-24
it's a know bug for some combinations of certain  BIOSes/chip sets and specific versions of upstart/init/kernel modules : the 'halt' wants to spin down IDE devices, but there are none, so it waits forever for a signal that it's OK to power off.

[https://bugs.launchpad.net/upstart/+bug/92685](https://bugs.launchpad.net/upstart/+bug/92685)
[https://bugs.launchpad.net/ubuntu/+bug/193125](https://bugs.launchpad.net/ubuntu/+bug/193125)

---

### Post by japtar10101 on 2009-05-24
> **koenn said:**
> it's a know bug for some combinations of certain  BIOSes/chip sets and specific versions of upstart/init/kernel modules : the 'halt' wants to spin down IDE devices, but there are none, so it waits forever for a signal that it's OK to power off.

[https://bugs.launchpad.net/upstart/+bug/92685](https://bugs.launchpad.net/upstart/+bug/92685)
[https://bugs.launchpad.net/ubuntu/+bug/193125](https://bugs.launchpad.net/ubuntu/+bug/193125)

Sorry to sound like hopeless noob, but it's kind of hard to comprehend the best solution, here.  Am I supposed to use this posted file from "noisy halt" bug?
[http://launchpadlibrarian.net/25530105/halt](http://launchpadlibrarian.net/25530105/halt)

---

### Post by koenn on 2009-05-24
> **japtar10101 said:**
> Sorry to sound like hopeless noob, but it's kind of hard to comprehend the best solution, here.  Am I supposed to use this posted file from "noisy halt" bug?
[http://launchpadlibrarian.net/25530105/halt](http://launchpadlibrarian.net/25530105/halt)

I'd just ignore it and power off manually after seeing
```
halt: Unable to iterate IDE devices: no such file or directory
[182.820656] System halted.
```

That modified halt script looks ok, as does [https://bugs.launchpad.net/ubuntu/+bug/193125/comments/22](https://bugs.launchpad.net/ubuntu/+bug/193125/comments/22) : judging by the comments in the bug reports, the test that causes the error msg is not really needed, so removing it shouldn't harm.

but no guarantees. :)

---

### Post by toolfan2k4 on 2009-05-24
If you are powering off have you tried just using a capital P?


```
sudo shutdown -P now
```

---

### Post by japtar10101 on 2009-06-02
> **toolfan2k4 said:**
> If you are powering off have you tried just using a capital P?


```
sudo shutdown -P now
```

Nope, same thing.
Looks like my plan to add automated shutdown and power on is not going to happen....

---

### Post by Vegan on 2009-06-03
I have found that bug to be widespread.

Keep in mind that a server does not usually get turned off, its up 24/7.

---

