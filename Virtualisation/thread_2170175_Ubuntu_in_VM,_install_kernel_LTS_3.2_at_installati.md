---
title: "Ubuntu in VM, install kernel LTS 3.2 at installation and stay there?"
date: 2013-08-25
forum: Virtualisation
---

### Post by rotation2 on 2013-08-25
I want to use Ubuntu or Xubuntu in a Virtual Machine.
I just istalled Ubuntu 12.04 twice: One with downloading updates, the other one without downloading updates while installation.
Both were on Kernel 3.8.
The long term kernel is 3.2 (or so), how do I install kernel 3.2 and stay there, without installing 3.8?

---

### Post by TheFu on 2013-08-25
I don't know which kernels are included with which releases. My 100% patched 12.04 box is running 3.2.0-52-generic-pae today. 3.2.0-52-generic is on the x64 VM server.

So, which 12.04 release did you install?  I guess there are 6 different versions, perhaps more based on the service pack levels.

Are you certain the VMs have 3.8?  **uname -a** verified?

---

### Post by rotation2 on 2013-08-25
I verified with uname -a.
I downloaded the disc today: ubuntu-12.04.3-desktop-i386

---

### Post by TheFu on 2013-08-25
Perhaps if you got 12.04.1 and never used dist-upgrade?

OTOH, I use dist-upgrade every week for the last 5+ yrs to get new kernels.  
```
$ uname -a
Linux lubuntu 3.2.0-52-generic-pae #78-Ubuntu SMP Fri Jul 26 16:43:19 UTC 2013 i686 i686 i386 GNU/Linux
$ more /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS"
```

This machine was installed as Ubuntu Server 12.04, fresh in 2012 - probably July.  I run apt-get update && apt-get dist-upgrade on it almost every Saturday morning. Clearly, it has 3.2.x kernels.  Let me check a few other servers ... 
```
$ ansible all -m command -a "uname -a" | egrep Linux
Linux romulus 3.2.0-52-generic #78-Ubuntu SMP Fri Jul 26 16:21:44 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Linux regulus 2.6.32-50-server #112-Ubuntu SMP Tue Jul 9 20:45:08 UTC 2013 x86_64 GNU/Linux
Linux qbe 3.2.0-52-generic #78-Ubuntu SMP Fri Jul 26 16:21:44 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Linux remus 3.2.0-45-generic #70-Ubuntu SMP Wed May 29 20:12:06 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Linux toron 2.6.32-50-generic #112-Ubuntu SMP Tue Jul 9 20:28:23 UTC 2013 x86_64 GNU/Linux
Linux bavar 3.2.0-52-generic #78-Ubuntu SMP Fri Jul 26 16:21:44 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Linux celes 3.2.0-52-virtual #78-Ubuntu SMP Fri Jul 26 16:45:00 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

The 2.6.x kernels are on 10.04.04 servers. The others are all 12.04.3 as of today.
I did pull down the 12.04.3 Server ISO yesterday from a local mirror, but haven't installed it anywhere.

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop) says, "> **Ubuntu Kernel 3.8**
By default, the 12.04.3 point release will ship with a newer 3.8 Ubuntu kernel from Ubuntu 13.04, and a matching X.org stack. This is based on the 3.8.0 Extended Upstream Stable Kernel Release. The purpose of providing a newer kernel in the 12.04.3 point release is for hardware enablement."
That is the explanation.  The page has other notes about the 3.2 and 3.5 kernels in 12.04.2 that might be interesting reading for some.

---

### Post by Cheesemill on 2013-08-25
You need to install from the 12.04.1 media to get the 3.2 kernel....

[http://old-releases.ubuntu.com/releases/precise/](http://old-releases.ubuntu.com/releases/precise/)

You can run all the *apt-get upgrade* and *apt-get dist-upgrade*'s you want and you'll stay on the 3.2 kernel unless you specifically follow the instructions [here ]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")to upgrade to a later kernel.

---

### Post by Bucky Ball on 2013-08-25
*Thread moved to **Virtualisation**.*

Unsure why this was in ABS. Please post in the appropriate sub-forums. Thanks. ;)

---

