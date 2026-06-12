---
title: "VMware Player 5.0.4 Not Intalling On Ubuntu 14.10"
date: 2015-06-11
forum: Virtualisation
---

### Post by mdw818 on 2015-06-11
I am trying to get VMware Player 5.0, but it does not install. I am a noob to ubuntu, so could someone help? By the way I tried two versions.

maxwell@M-1:~$ sudo sh VMware-Player-5.0.4-1945795.x86_64.bundle
[sudo] password for maxwell: 
sh: 0: Can't open VMware-Player-5.0.4-1945795.x86_64.bundle
maxwell@M-1:~$ sudo sh VMware-Player-5.0.4-1945795.i386.bundle
sh: 0: Can't open VMware-Player-5.0.4-1945795.i386.bundle

---

### Post by LastDino on 2015-06-11
Is there any particular reason you're installing the older version?  Is your system/OS x32 or x64? 

Was your ''procedure'' this? If not, then could you follow it and show us the results (in case of x64 system)?
1. Open a terminal window. 2. Type in the following commands then hit Enter after each.
 > sudo apt-get install build-essential linux-headers-`uname -r`

 > mkdir ~/VMware && cd ~/VMware 

 > wget -c [http://goo.gl/I2Hytp](http://goo.gl/I2Hytp) -O VMware-Player-7.1.0.x86_64.bundle.tar 

 > tar -xvf VMware-Player-7.1.0.x86_64.bundle.tar 

 > chmod +x VMware-Player-7.1.0-2496824.x86_64.bundle 

 > sudo sh VMware-Player-7.1.0-2496824.x86_64.bundle



---

