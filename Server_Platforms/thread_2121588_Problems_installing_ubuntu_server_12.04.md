---
title: "Problems installing ubuntu server 12.04"
date: 2013-03-02
forum: Server Platforms
---

### Post by darknuts on 2013-03-02
Hey guys. I'm trying to install ubuntu server 12.04 LTS on a virtual box and I keep running into an error during base installation. It says that the kernel could not be installed. During the process, I'm given the option to choose between kernels. No matter which one I choose, i get an error. I cant complete the installation with out this. Can anyone help?

---

### Post by darknuts on 2013-03-02
Well after pouring through the logs, I found the errors:

[ATTACH=CONFIG]239637[/ATTACH]

But it just says it failed to install...

---

### Post by darknuts on 2013-03-02
After further evalution, it seems it was just a bug in the 12.04 LTS version of Ubuntu server. I installed 12.10 server and it works fine. Thanks. Problem solved! :P

---

### Post by Mr. Shannon on 2013-03-02
I just wanted to add to this in case anyone reads this and has the same problem. It is probably not a bug in Ubuntu 12.04 server as I installed 12.04 server on VirtualBox a couple day's ago and it worked fine.

Please mark this thread as solved if you feel the issue has been resolved.
Temporary solution to marking a thread as solved: [http://ubuntuforums.org/showthread.php?t=2121377&highlight=solved](http://ubuntuforums.org/showthread.php?t=2121377&highlight=solved)

---

### Post by darknuts on 2013-03-03
If what you say is true then technically the problem is not solved. I wonder why it worked for you and not for me. In the log it said 'bootstrap base failed with error code 1'. What were your Virtual Box settings. I would rather use 12.04 since it's LTS.

---

### Post by LHammonds on 2013-03-03
In the threads in my sig, I have noted how I install Ubuntu 12.04 LTS and it has worked for me inside VirtualBox AND vmware ESXi since the initial release of 10.04 LTS and every service pack after it up to 12.04.1 (have not installed 12.04.2 directly from image yet)

LHammonds

---

### Post by Mr. Shannon on 2013-03-04
Did you confirm the checksums of the disk?  Also, are you trying to install 64 bit additions, if so you need to make sure that VT-x/AMD-V is turned on, both in VirtualBox and in the BIOS.

---

