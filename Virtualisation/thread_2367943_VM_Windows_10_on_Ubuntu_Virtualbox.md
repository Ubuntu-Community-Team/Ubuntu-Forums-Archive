---
title: "VM Windows 10 on Ubuntu Virtualbox"
date: 2017-08-05
forum: Virtualisation
---

### Post by abbasali31 on 2017-08-05
I have a Dell OPtiplex 745 with 3Gb of RAM. I have successfully installed Ubuntu 17.04 and it works very efficiently. I am having issues installing Windows 10 on Virtualbox. It loads to VM Windows 10 fine where I can see the Windows Logo and then it hangs. In other words the spinning wheel doesn't start.

I checked various sources and there I tried, but still no luck.

Unable to figure out if my desktop is not compatible to run Virtual Machines. I think it is an issue with some settings.

Please advise!

Thanks!

---

### Post by deadflowr on 2017-08-05
Run
```
egrep -c '(vmx|svm)' /proc/cpuinfo
```
from a terminal to determine if you can run VMs with that hardware.
(0 means no, 1 or more means yes)

Also, I wonder if you can even allocate enough resources for the Win10 vm to even start.

3GB of RAM means you'd by running Win10 on the low side.
(I mean 3GB of RAM is low to run Win10 even on real hardware let alone a VM on a machine running Ubuntu, presumably Ubuntu Desktop, which itself is probably eating a significant chunk of RAM. )

---

### Post by abbasali31 on 2017-08-05
Thanks!  I ran the command and it was 0.  No wonder it froze.

Regards,

---

### Post by abbasali31 on 2017-08-05
Is it possible to install another distribution of linux lbuntu and then run VM window 10?

---

### Post by QIII on 2017-08-05
Hello!

The limitation my be your CPU.

For a bit more detail, could you post the results of 

```
cat /proc/cpuinfo | grep model
```

If you get several repeated lines, just copy and paste the first one that sais "name".

---

### Post by abbasali31 on 2017-08-05
Here you go and thanks!

```

user@OptiPlex-745:~$ cat /proc/cpuinfo | grep model
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz
```

---

### Post by QIII on 2017-08-05
According to [this]("http://ark.intel.com/products/30781/Intel-Core2-Duo-Processor-E4500-2M-Cache-2_20-GHz-800-MHz-FSB"), your CPU does not support virtualization.  

>  Intel® Virtualization Technology (VT-x)  No

If VT-x is just not toggled on in BIOS/EFI it can be turned on (depending on what control your BIOS gives you).   But according to ARK, the CPU itself is not capable.

Even still, sometimes a 32-bit guest *might* run.  You can try that, but I would say chances are slim to none.

---

