---
title: "Is there any difference?"
date: 2010-06-22
forum: The Cafe
---

### Post by 98cwitr on 2010-06-22
Other than the installation processes, if you install a GUI (sudo apt-get install ubuntu-desktop) on Ubuntu Server, is there a difference between the desktop version?

---

### Post by NightwishFan on 2010-06-22
No I would not think so, though the server kernel does not use preemption. You can manually install one or both kernels though. If you have a desktop but still use server tasks having no preemption is fine.

---

### Post by McRat on 2010-06-22
When I did that, I ran into trouble with the wireless.  I could not isolate it.  I loaded GUI 32bit up and the problem went away.  The hardwire always worked.

---

### Post by NightwishFan on 2010-06-22
It should be no different from installing Ubuntu from the Alternate CD, which always worked for me. I just installed the Netbook Interface from my Desktop edition and it works. Though a recommendation, install the desktop using aptitude not apt-get.
```
sudo aptitude update && sudo aptitude install ubuntu-desktop
```

---

### Post by cbrunhaver on 2010-06-22
IIRC, the 32 bit server kernel uses PAE, where I believe that the desktop version does not.  [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

---

### Post by Lightstar on 2010-06-22
The ubuntu desktop kernel comes with PAE now, it's been like that for the last 2 versions maybe?

Yeah, I used to install the server kernel just for PAE, beside that, i never noticed any difference from the desktop version.

---

### Post by NightwishFan on 2010-06-22
linux-server has:

100hz timer
Deadline I/O Scheduler
No preemption
PAE


linux-generic has: (on 32-bit)

250hz timer
CFQ I/O Scheduler
Voluntary Preemption
PAE (as of late)

---

