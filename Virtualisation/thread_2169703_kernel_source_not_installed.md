---
title: "kernel source not installed"
date: 2013-08-23
forum: Virtualisation
---

### Post by hvn2 on 2013-08-23
Hi,

I run Lucid 10.04 (because of a specific application I can' t upgrade) and need to use virtualbox. Using synaptic I installed it, but I can't start any appliance because it says that virtualbox-dkms isn't installed. When I try to install it, it complains that the kernel source isn't installed. However, synaptic shows that I'm running kernel 3.0.0.32.36 and the kernel-source (installed using synaptic) shows it is version 3.0.0-32.51. This doesn't match obviously, but I can't get it right so far. Is there any solution to this?

Thanks.

---

### Post by TheFu on 2013-08-23
The software is telling you to install the "Guest Additions" for VirtualBox. On Linux, that means you need to pre-install the required dependencies.  [This article]("http://www.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox") explains that and a number of other virtualbox tuning techniques.

Whatever you do, please do NOT just install the headers for the specific kernel. If you do, when the next kernel gets released (you are on LTS server with support until 2015, right?), you'll have the same issue again. Solve it once, now, correctly.

If you plan to run this OS beyond 2014 - you'll want to get all the packages local that future installation dependencies could require before the packages are gone forever.

If you are running 10.04 desktop, supported ended earlier this year so no more patches should be expected. Please do not put that VM on the internet. Not safe.

---

### Post by hvn2 on 2013-08-23
It doesn't get to asking to install the Guest Additions. It doesn't want to start the virtual machine at all. At clicking "Start" it says: "Failed to open a session for the virtual machine BBbeagle. The virtual machine 'BBbeagle' has terminated unexpectedly during startup with exit code 1." When I click OK, it says "Please install the virtualbox-dkms package and execute 'modprobe vboxdrv' as root.". The dkms packages is installed, but at modprobe I see this: /etc/init.d/vboxdrv.dpkg-new There is no vboxdrv. So does your solution go for this problem too ?

---

### Post by TheFu on 2013-08-23
Ah ... the issue is on the hostOS, not inside the client. 
Run this on the hostOS```

$ sudo apt-get --reinstall install virtualbox-dkms
```
Let's see if a forced reinstall of the virtualbox kernel driver there helps.
Those previously linked instructions are for inside the client OS.

If I am misunderstanding something, please let me know.

---

### Post by hvn2 on 2013-08-23
This is the output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/671 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 330752 files and directories currently installed.)
Preparing to replace virtualbox-dkms 4.1.2-dfsg-1ubuntu1.1 (using .../virtualbox-dkms_4.1.2-dfsg-1ubuntu1.1_all.deb) ...

------------------------------
Deleting module version: 4.1.2
completely from the DKMS tree.
------------------------------
Done.
Unpacking replacement virtualbox-dkms ...
Setting up virtualbox-dkms (4.1.2-dfsg-1ubuntu1.1) ...
Loading new virtualbox-4.1.2 DKMS files...
Building only for 3.0.0-32-generic-pae
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules                                            
* No suitable module for running kernel found
                                                                         [fail]
invoke-rc.d: initscript virtualbox, action "restart" failed.

---

### Post by steeldriver on 2013-08-23
What does

```
apt-cache policy linux-headers-generic
```

say? Is that in sync with your running kernel?

Remember that the desktop version of 10.04 has already gone EOL (although last time I checked the repositories hadn't yet been archived - presumably because the server version is supported longer)

---

### Post by hvn2 on 2013-08-23
linux-headers-generic:
  Installed: 3.0.0.32.36
  Candidate: 3.0.0.32.36
  Version table:
 *** 3.0.0.32.36 0
        500 [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) oneiric-updates/main i386 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security/main i386 Packages
        100 /var/lib/dpkg/status
     3.0.0.12.14 0
        500 [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) oneiric/main i386 Packages

---

