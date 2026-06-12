---
title: "Password sent in bug report?"
date: 2011-12-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by leeper69 on 2011-12-03
Hi I just tried to install precise everything went fine drive was formated ext4 files were loaded grub was installed in the mbr then the install failed. and I was asked to file a bug report and informed that my password would be sent with the info in the bug report. I don't want to give up my password. my only option is to reinstall and use another password so I can file a bug report.

---

### Post by cariboo on 2011-12-03
Moved to a thread of it's own, as it didn't belong in the thread it was in.

---

### Post by 3vi1 on 2011-12-03
> **leeper69 said:**
> Hi I just tried to install precise everything went fine drive was formated ext4 files were loaded grub was installed in the mbr then the install failed. and I was asked to file a bug report and informed that my password would be sent with the info in the bug report. I don't want to give up my password. my only option is to reinstall and use another password so I can file a bug report.

I ran into the same bug you mentioned earlier this morning - and the same dilema.

Disconnect your network cable (just unchecking "Download updates..." does not work and has a separate bug filed) so that it doesn't try to download the newer libc6 and run into dependency problems.  After the install finishes, connect everything and run sudo apt-get update && sudo apt-get upgrade.

I wouldn't bother filing a bug against the actual problem.  The packages causing the problem will change multiple times before we even hit beta.  I did add the details of the current state to another similar bug that I think has the same root cause though.

---

### Post by leeper69 on 2011-12-03
Thanks for the workaround 3vi1 installed without a hitch!

---

### Post by MacUntu on 2011-12-03
In my case ([https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/899683](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/899683)) it was a crappy partition layout that messed up the installation.

The password thingy is annoying, but you are using an alpha version of Ubuntu! Either ignore the bugs, invest some time in making Ubuntu better (which often starts with a high quality bug report), or just don't use an alpha OS.

---

### Post by leeper69 on 2011-12-03
well I have Ubuntu precise loaded and the hardware install for my Nvidia 9500gt was easy and works fine. I have changed my password so I will be able to file bug reports. The password can be changed whenever I get paranoid. thanks for answering my post macuntu and 3vi1!!!

---

