---
title: "Which Kernel should I have?"
date: 2015-02-25
forum: Ubuntu, Linux and OS Chat
---

### Post by pfeiffep on 2015-02-25
Ok I'm confused. 14.04.2 has been released and according to what I've read should contain kernel 3.16

I just ran software updater and rebooted as suggested... here's the output[INDENT]```
pfeiffep@Dell-Studio:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty
pfeiffep@Dell-Studio:~$ uname -a
Linux Dell-Studio 3.13.0-46-generic #75-Ubuntu SMP Tue Feb 10 15:24:04 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```
[/INDENT]
I think my machine is working just fine, I'm just wondering about the apparent discrepiency.

---

### Post by v3.xx on 2015-02-25
When upgrading to the next point release, the kernel will remain 3.13.

A fresh install or manual kernel upgrade is necessary for the 3.16 kernel.

---

### Post by pfeiffep on 2015-02-25
> **v3.xx said:**
> When upgrading to the next point release, the kernel will remain 3.13.

A fresh install or manual kernel upgrade is necessary for the 3.16 kernel.Thanks for the quick reply..
So does manually installing a newer kernel affect the length of support as seemingly indicated [here]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")  ?

---

### Post by v3.xx on 2015-02-25
[http://ubuntuforums.org/showthread.php?t=2266755&p=13234723&viewfull=1#post13234723](http://ubuntuforums.org/showthread.php?t=2266755&p=13234723&viewfull=1#post13234723)

[https://wiki.ubuntu.com/Kernel/Support#A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/Support#A14.04.x_Ubuntu_Kernel_Support)

---

### Post by pfeiffep on 2015-02-25
So how exactly does one determine which HWE stack is installed

> Anyone running with the newer Trusty HWE stack will remain on that stack.  Users will **NOT** be automatically rolled forward to newer releases.

---

### Post by pfeiffep on 2015-02-25
So how exactly does one determine which HWE stack is installed

> Anyone running with the newer Trusty HWE stack will remain on that stack.  Users will **NOT** be automatically rolled forward to newer releases.

---

### Post by ajgreeny on 2015-02-25
One potential problem is that, as happened in Precise, the non-LTS hardware stack that you upgrade to now will be utopic and that may lose support in two months time as utopic loses support.

If all is working fine with 3.13, I would leave it alone as that kernel version will be supported for the full life of trusty; if you have wifi problems or some other problem when using 3.13 it might be worth moving to the utopic hardware stack or waiting until the next LTS hardware stack is available for trusty, though I do not know when that will be..
See [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

If you wish to go ahead run command ```
sudo apt-get install linux-generic-lts-utopic xserver-xorg-lts-utopic libegl1-mesa-drivers-lts-utopic xserver-xorg-video-all-lts-utopic xserver-xorg-input-all-lts-utopic
```and if you have a 64bit system with UEFI also run ```
sudo apt-get install linux-signed-generic-lts-utopic 
```
"If it ain't broke, don't fix it; if you do fix it and break it, you get to keep the parts"

---

### Post by pfeiffep on 2015-02-25
Thank you [**[COLOR=#000000]ajgreeny[/COLOR]**]("http://ubuntuforums.org/member.php?u=27747")

I am a believer of* if it aint broke don't fix it*; but OTOH keeping current with software upgrades has kept me out of trouble for quite a few years.

After searching for the past hour I can see absolutely no reason to install kernel 3.16 on my 2 **'working perfectly'** systems. 

So now what happens to the folks who install 14.04.2 from scratch (regarding LTS) ... the answer to this question is somewhat obtuse.

---

### Post by deadflowr on 2015-02-25
> So now what happens to the folks who install 14.04.2 from scratch (regarding LTS) ... the answer to this question is somewhat obtuse.
I don't know why you think it obtuse, they'd get the 3.16 kernel and utopic X stack.
But, unlike the 3.13 /X stack, it will only be supported until the stack for the 16.04 is made available, at which time the system will inform the user that they will need to upgrade to that stack.

Much the same as how users of precise were informed that they needed to upgrade to the trusty stack, if they had installed the point releases for 12.04.2, .3, or .4.

---

### Post by pfeiffep on 2015-02-25
> **deadflowr said:**
> I don't know why you think it obtuse, they'd get the 3.16 kernel and utopic X stack.
But, unlike the 3.13 /X stack, it will only be supported until the stack for the 16.04 is made available, at which time the system will inform the user that they will need to upgrade to that stack.

Much the same as how users of precise were informed that they needed to upgrade to the trusty stack, if they had installed the point releases for 12.04.2, .3, or .4.
IMO it's obtuse because LTS - 5 years or 2?
Maybe I'm off base but I originally thought that point releases were intended to minimize the effect of many updates if one re-installed for a reason. So now If I use the 14.04.02 image to re-install I cannot rely on the full 5 years support. I a new adopter sees LTS and 5 year support until 2019 and installs the new image the install won't be LTS??
**Ubuntu 14.04.2 LTS Released, Includes 3.16 Kernel**

---

### Post by deadflowr on 2015-02-25
Except for the hardware stack, everything on the point release will be supported until 2019.
It is just that the user will need to adjust the stack come August 2016.
But everthing else on a default install won't need to be updated, like gedit, or libreoffice-writer.

LTS releases are far more than a kernel and X stack.

---

### Post by v3.xx on 2015-02-25
I,m running older hardware, the 3.2 and 3.13 kernel works for me.

---

### Post by pfeiffep on 2015-02-25
> **deadflowr said:**
> Except for the hardware stack, everything on the point release will be supported until 2019.
It is just that the user will need to adjust the stack come August 2016.
So once again I ask [INDENT]**So how exactly does one determine which HWE stack is installed**?
[/INDENT]

---

### Post by deadflowr on 2015-02-25
> **pfeiffep said:**
> So once again I ask[INDENT]**So how exactly does one determine which HWE stack is installed**?
[/INDENT]

[The release notes]("https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes#Official_flavours")
But, also
I think eventually, like precise, the update-manager-core package will get an update which will include the hwe-support-status option.
You would then run
```
hwe-support-status --verbose
```
and will tell you if you are running Hardware Stack Enablement, or not, and which one, and how long it is supported for.
The original kernel and X stack are not considered hwe, so if you are running them it'll say you are not running a hwe release.

But, unless you opt to install into an existing installation of the original release(14.04, or 14.04.1), or you install a fresh installation of one of the point releases (versions .2, .3, .4)
you'd be using whatever was originally installed.
Of course.

It is done so that older machines, which may not run well or at all will not have to worry that they will be updated to a stack which would break their systems, but at the same time, the point releases offer better support for newer machine, which would not have had said support in the earlier releases.
If that makes sense into why an installed release only gets the basic package updates and not a new hwe.

There are definite flaws in it all, like how it doesn't auto upgrade from point release stack to point release stack for the non-original stacks, which i can see some people wanting.
Among other [s]errors[/s] things.

---

### Post by ajgreeny on 2015-02-25
> **deadflowr said:**
> [The release notes]("https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes#Official_flavours")
But, also
I think eventually, like precise, the update-manager-core package will get an update which will include the hwe-support-status option.
You would then run
```
hwe-support-status --verbose
```
and will tell you if you are running Hardware Stack Enablement, or not, and which one, and how long it is supported for.
The original kernel and X stack are not considered hwe, so if you are running them it'll say you are not running a hwe release.

But, unless you opt to install into an existing installation of the original release(14.04, or 14.04.1), or you install a fresh installation of one of the point releases (versions .2, .3, .4)
you'd be using whatever was originally installed.
Of course.

It is done so that older machines, which may not run well or at all will not have to worry that they will be updated to a stack which would break their systems, but at the same time, the point releases offer better support for newer machine, which would not have had said support in the earlier releases.
If that makes sense into why an installed release only gets the basic package updates and not a new hwe.

There are definite flaws in it all, like how it doesn't auto upgrade from point release stack to point release stack for the non-original stacks, which i can see some people wanting.
Among other errors.
That's a nice idea in theory, but a lot of users, including me, had a problem trying to upgrade the hardware stack in Precise with packages that could not be installed.  It was some time ago that I was in this position and I did eventually solve it by upgrading the needed packages but it had to be done in a particular order, if I remember correctly, and involved a lot of attempts that got me nowhere with the same error of "Package could not be installed because it requires package2 but package2 is not found" or something similar to that.

This time I shall stick with trusty and the trusty hardware stack until 16.04 appears and then I'll upgrade to that LTS version after the early bugs have been sorted out.

---

