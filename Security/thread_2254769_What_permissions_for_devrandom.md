---
title: "What permissions for /dev/random"
date: 2014-11-29
forum: Security
---

### Post by astarmathsandphysics on 2014-11-29
I am surprised to find this file has permissions 660
Is this correct or can I tighten it a bit?

Also, permissions on /ysr/sbin/pwck are 755.
Can I tighten this too?

---

### Post by sudodus on 2014-11-30
Have a look at the following and other descriptions found via the internet.

[https://en.wikipedia.org/?title=/dev/random](https://en.wikipedia.org/?title=/dev/random)

I'm not sure it is an improvement, if you change the permissions of /dev/random. It is a block device, and not the program, that is creating the random numbers.

> In Unix-like operating systems, **/dev/random** is a special file that serves as a blocking pseudorandom number generator. It allows access to environmental noise collected from device drivers and other sources.
...
It is also possible to write to /dev/random. This allows  any user to mix random data into the pool. Non-random data is harmless,  because only a privileged user can issue the [ioctl]("https://en.wikipedia.org/wiki/Ioctl")  needed to increase the entropy estimate. The current amount of entropy  and the size of the Linux kernel entropy pool are available in /proc/sys/kernel/random/, which can be displayed by the command cat /proc/sys/kernel/random/entropy_avail.

Edit: About the other file and its permissions:

pwck is an executable program, and only root can change it, which should be OK.

---

### Post by astarmathsandphysics on 2014-11-30
Thanks. Think ok - just frantic about secirity right now.

---

