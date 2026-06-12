---
title: "kernel update and nvidia"
date: 2020-10-20
forum: Ubuntu, Linux and OS Chat
---

### Post by T6&amp;sfpER35% on 2020-10-20
please take note 

if you plan to upgrade to latest [kernel version]("https://www.omgubuntu.co.uk/2020/10/linux-5-9-kernel-featureske") , and you have NVIDIA  , please read [here]("https://www.phoronix.com/scan.php?page=news_item&px=NVIDIA-Linux-5.9-Delayed")

[-X

---

### Post by Frogs Hair on 2020-10-20
Not a support request, moved to ***UL&OS Chat***.

---

### Post by sdsurfer on 2020-10-20
I've got Nvidia in all my machines, have used them for years, and frankly the constant hassles are becoming very tiresome. Fortunately this particular machine is 5.4. I think I'm going to start fishing for other GPU's.

---

### Post by T6&amp;sfpER35% on 2020-10-20
i also have NVIDIA for years  , and never had any problems .
i don't do gaming , only thing that could strain the graphics here  is watching movies ,and here's no problems with that

---

### Post by grahammechanical on 2020-10-20
There is an active thread in the Ubuntu Development Version section of this forum on the Linux 3.9 kernel. I think those members would find this report useful as they test the 3.9 kernel.

[https://ubuntuforums.org/showthread.php?t=2448933](https://ubuntuforums.org/showthread.php?t=2448933)

This problem may become an issue during the development of Ubuntu 21.04. People installing the 21.04 release of Ubuntu may have problems and if they come here for solutions at least we know the cause of the problem.

I do not understand why the Linux developers are so concerned with what Nvidia is doing. I am guessing from the little I have read about this that the Linux developers are concerned that proprietary code could enter into the kernel code by pretending to be GPL (General Public License) code and they are never going to allow that to happen as it would compromise Linux as GPL code. They are also concerned that Nvidia is not putting notices in the code as to who owns the copyright to the code. In this way Nvidia avoids blame for any bugs caused by their code.

Regards

---

### Post by CatKiller on 2020-10-20
> **grahammechanical said:**
> I do not understand why the Linux developers are so concerned with what Nvidia is doing.

The issue is that the GPL covers derivative code: code that's derived from GPL code *must* be GPL'd. That's pretty much the point of the GPL. Nvidia (and others) don't want their code to be GPL'd, but they do want to interface with the kernel. The line between derivative code and original interface code is fuzzy at this level, and to *actually* determine whether a particular thing is derivative code or not requires going to court, which would be lengthy, expensive, and may vary by jurisdiction, and no one wants that. So, instead, the kernel devs have highlighted particular functions that, in their opinion, would make code derivative of kernel code: the GPL symbols. Stuff that uses normal kernel interfaces but doesn't use those functions can use whatever licence, but if it uses those particular functions then it's derivative code, and must be under the GPL. Everyone gets some clarity, and no one has to go to court to get judgment on GPL violations. People want to prevent deliberate GPL violations, but they want to avoid accidental GPL violations, too.

---

### Post by rbmorse on 2020-10-20
In the comments of the Phoronix article several commenters note that only the UVM module is affected (CUDA and OpenCL).  The display driver itself works fine (apparently).

---

### Post by mastablasta on 2020-10-21
maybe they will at some point figure out that proprietary no longer make so much sense. if AMD can deliver, and if others actually help with improvements in their driver it might make them think.

---

