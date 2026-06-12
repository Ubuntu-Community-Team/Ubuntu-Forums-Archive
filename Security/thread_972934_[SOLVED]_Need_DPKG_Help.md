---
title: "[SOLVED] Need DPKG Help"
date: 2008-11-06
forum: Security
---

### Post by shadow_people785 on 2008-11-06
first of all when i go to try to install upsdates it says: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report." so i go to terminal and type:dpkg --configure -a. and when i type that in i type in my password as always and all that comes up is: ">". so i dont know what to do from here.... also when i try to install a .deb package, it says this: "Only one software management tool is allowed to run at the same time

please close the other application e.g. 'update manager', 'aptitude' or 'synaptic' first."

so im in a really tough spot... so i dont know how to shut off the update manager.... all i see running is the red arrow at the top of the screen w/ the ! in it..... 
please help

also i am running ubuntu 8.10 official.
thank you in advance

---

### Post by thomasyen on 2008-11-06
Do you have Synaptic and GDebi (dpkg frontend) running at the same time? Because if you are, close one as only one is allowed to run at one time.

---

### Post by shadow_people785 on 2008-11-06
> **thomasyen said:**
> Do you have Synaptic and GDebi (dpkg frontend) running at the same time? Because if you are, close one as only one is allowed to run at one time.

all that is running is the deb package manager and the quick update icon at the top of the screen. if that helps

---

### Post by dakkar9999 on 2008-11-07
I'm having the same problem.  My computer locked up during an update (hard lock) had to reset and now I get that error message.

How was your problem solved?

---

### Post by cariboo on 2008-11-07
CLose all package manager and in a terminal type:

```
sudo dpkg --configure -a
```

If you get the error message that:

> Only one software management tool is allowed to run at the same tim

Ypu may have to look for a lock file that wasn't closed. Check in:

```
/var/cache/apt/archives
/var/lib/dpkg
/var/lib/apt/lists
```

Jim

---

