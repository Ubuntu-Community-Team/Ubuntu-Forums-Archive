---
title: "Dd anyone tried nvidia drivers 331.38 and/or xorg 1.15?"
date: 2014-01-18
forum: Ubuntu Development Version
---

### Post by spupazza on 2014-01-18
As per title I wanted to know if anyone tried the  very new nvidia drivers 331.38 (trough xorg-edgers ppa or compilation, in the latter case, pls explain how you did it, because I got failure in building dkms starting from a command line installation with all the dependencies needed)
and/or xorg 1.15.
I tried to install both on my machine 2 days ago, but the system froze once or twice in an hour so I reinstalled.
Today I read somewhere, that with xorg 1.15 the patch needed for the driver 331.20 (commenting few lines of nvacpi) is still necessary.
I don't know if that's true ,so I wanted to ask you if it's possible and if it doesn't make teh system unstable install the driver 331.38 from xorg edgers and the new xorg version from x staging ppa.

---

### Post by Cavsfan on 2014-01-19
> **spupazza said:**
> As per title I wanted to know if anyone tried the  very new nvidia drivers 331.38 (trough xorg-edgers ppa or compilation, in the latter case, pls explain how you did it, because I got failure in building dkms starting from a command line installation with all the dependencies needed)
and/or xorg 1.15.
I tried to install both on my machine 2 days ago, but the system froze once or twice in an hour so I reinstalled.
Today I read somewhere, that with xorg 1.15 the patch needed for the driver 331.20 (commenting few lines of nvacpi) is still necessary.
I don't know if that's true ,so I wanted to ask you if it's possible and if it doesn't make teh system unstable install the driver 331.38 from xorg edgers and the new xorg version from x staging ppa.

I have Nvidia driver 331.38 installed with the the “xorg crack pushers” team ppa. [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) 
It works great! No problems whatsoever.
```
cavsfan@cavsfan-MS-7529:~$ uname -a
Linux cavsfan-MS-7529 3.13.0-4-generic #19-Ubuntu SMP Thu Jan 16 18:10:11 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia
ii  nvidia-331                                                  331.38-0ubuntu1                                           amd64        NVIDIA binary driver - version 331.38
rc  nvidia-331-updates                                          331.20-0ubuntu9                                           amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-libopencl1-331                                       331.38-0ubuntu1                                           amd64        NVIDIA OpenCL Driver and ICD Loader library
rc  nvidia-libopencl1-331-updates                               331.20-0ubuntu9                                           amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331                                       331.38-0ubuntu1                                           amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-331-updates                               331.20-0ubuntu9                                           amd64        NVIDIA OpenCL ICD
rc  nvidia-persistenced                                         331.20-0ubuntu1~xedgers~trusty1                           amd64        Load the NVIDIA kernel driver and create device files
ii  nvidia-prime                                                0.5.3                                                     amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                             331.38-0ubuntu1~xedgers~trusty1                           amd64        Tool for configuring the NVIDIA graphics driver
```

[ATTACH=CONFIG]249590[/ATTACH]

---

### Post by spupazza on 2014-01-19
> **Cavsfan said:**
> I have Nvidia driver 331.38 installed with the the &#8220;xorg crack pushers&#8221; team ppa. [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) 

Hi thanks for your reply.

Did you need to apply the patch mentioned (editing the nvacpi file, by commenting few lines) like it was needed for kernel 3.13 before it became standard in Trusty?
Or you just installed it without patching the file?

I'm referring to this patch:
[http://ubuntuforums.org/showthread.php?t=2195166&p=12885245#post12885245](http://ubuntuforums.org/showthread.php?t=2195166&p=12885245#post12885245)
I just wanted to know if it's needed or not (can you pls check if you have this patch applied, in case you installed trusty more than 2 weeks ago)

---

### Post by Cavsfan on 2014-01-19
> **spupazza said:**
> Hi thanks for your reply.

Did you need to apply the patch mentioned (editing the nvacpi file, by commenting few lines) like it was needed for kernel 3.13 before it became standard in Trusty?
Or you just installed it without patching the file?

I'm referring to this patch:
[http://ubuntuforums.org/showthread.php?t=2195166&p=12885245#post12885245](http://ubuntuforums.org/showthread.php?t=2195166&p=12885245#post12885245)
I just wanted to know if it's needed or not (can you pls check if you have this patch applied, in case you installed trusty more than 2 weeks ago)

No I didn't install any patch. I first installed **nvidia-331-updates** I believe without the x-swat ppa added and it pulled in the other stuff, 
Then I added the PPA and installed **nvidia-persistenced** because it says in the description **Load the NVIDIA kernel driver and create device files** 
which seems important. There is also a bug to have **nvidia-persistenced** added to the regular repository for Trusty.
The other files just came with those and it was once 331.20 and has updated to 331.38 during the past few days.

Here is the bug [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-319/+bug/1246735](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-319/+bug/1246735)

---

### Post by Cavsfan on 2014-01-19
I installed less than 2 weeks ago:

```
cavsfan@cavsfan-MS-7529:~$ ls -ld /var/log/installer | awk '{ print $6 " " $7 " " $8 }'
Jan 8 15:59
```

---

### Post by spupazza on 2014-01-19
Thanks for all the infos. I tried and the drivers seems to work just fine like you said.
:D

---

### Post by Cavsfan on 2014-01-20
> **spupazza said:**
> Thanks for all the infos. I tried and the drivers seems to work just fine like you said.
:D

Good deal! :) Glad it worked for you. Don't forget to mark this thread as solved by editing the 1st post and changing the status to "solved".

Cheers!

---

