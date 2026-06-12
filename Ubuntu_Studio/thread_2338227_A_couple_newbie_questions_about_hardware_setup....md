---
title: "A couple newbie questions about hardware setup..."
date: 2016-09-26
forum: Ubuntu Studio
---

### Post by ragsocks on 2016-09-26
Hello,

I just installed Ubuntu Studio 16.0.4 for the first time and have a few questions about hardware setup. How do I know if all my devices and hardware were properly setup during installation? Is there a device manager included with Ubuntu Studio? Should I bother to install the Intel microcode driver that shows up in the addition drivers app? 
I have an older HP DV7t 6000 laptop with the Intel i7 switchable AMD 6770m gpu setup. What is the best way to handle this situation? How can I determine which gpu is being utilized? Is there currently an easy way to switch the AMD gpu off? My gpu seems to be supported by the new Radeon driver, but what sort of limitations are there? I primarily want to use Ubuntu Studio for video/photo editing and 3d modeling in Blender, is the new Radeon driver model in 16.0.4 sufficient for these tasks? I'd prefer to use the latest version of Ubuntu Studio, but would it be worth installing the older version that has more robust driver support for the AMD gpu? Thanks.

Joe P.

---

### Post by CrocoDuck on 2016-09-26
> **ragsocks said:**
> How do I know if all my devices and hardware were properly setup during installation?

This command is one of your best friends:

```
lspci -vnn
```

It will list all the available info for each piece of hardware on the PCI. This amounts to pretty much everything. If recognized, your hardware will show up there. Also, the -vnn will show the driver loaded by the system for the device. A less verbose option is to use only

```
lspci
```

There are GUI programs that do the same. Google "list hardware components Linux".

> **ragsocks said:**
> Is there a device manager included with Ubuntu Studio?

What do you mean? Usually under Linux you install the kernel modules (drivers) needed for each device. This is done automatically by Ubuntu.

> **ragsocks said:**
> Should I bother to install the Intel microcode driver that shows up in the addition drivers app?

Yes, [read more]("https://wiki.archlinux.org/index.php/Microcode") (Arch Wiki, but relevant also on Ubuntu).

> **ragsocks said:**
> I have an older HP DV7t 6000 laptop with the Intel i7 switchable AMD  6770m gpu setup. What is the best way to handle this situation?

Not sure how to help you here, as I never used these sort of dual gpu laptops. These Arch Wiki pages should get you started:

[https://wiki.archlinux.org/index.php/AMDGPU](https://wiki.archlinux.org/index.php/AMDGPU)
[https://wiki.archlinux.org/index.php/AMD_Catalyst](https://wiki.archlinux.org/index.php/AMD_Catalyst)
This in particular: [https://wiki.archlinux.org/index.php/ATI#Hybrid_graphics.2FAMD_Dynamic_Switchable_Graphics](https://wiki.archlinux.org/index.php/ATI#Hybrid_graphics.2FAMD_Dynamic_Switchable_Graphics)

Probably you will need to do some research to know how to handle it. However, there are two cases:


[LIST=1]
[*]Ubuntu will setup everything in some way when you install additional drivers that it is good for you. 
[*]You will need to install few additional packages. 
[/LIST]

I point you to Arch wiki as it is more up to date and information rich. On Ubuntu you will have to find how the packages are called, and install them through software center or apt-get. Names will be probably pretty close. Once you made your mind clearer on Arch wiki you will know better what to google in order to achieve your goal on Ubuntu.

> **ragsocks said:**
> How can I determine which gpu is being utilized?

Use lspci.

> **ragsocks said:**
> Is there currently an easy way to switch the AMD gpu off?

Read the above documentation. You can also probably disable in the bios or just unload its kernel module driver.

> **ragsocks said:**
> My gpu seems to be supported by the new Radeon driver, but what sort of  limitations are there? I primarily want to use Ubuntu Studio for  video/photo editing and 3d modeling in Blender, is the new Radeon driver  model in 16.0.4 sufficient for these tasks? I'd prefer to use the  latest version of Ubuntu Studio, but would it be worth installing the  older version that has more robust driver support for the AMD gpu?

Try and see how it goes.

Now, I hate to be that guy, but forums are intended to ask specific questions. I took the time to reply to you as I want to be a kind duck, but most of these question could have been answered by some googling, which would have narrowed down the areas where you need help to few and helped a great deal in formulating your questions. Take your time reading the docs and revert back if you encounter troubles. I strongly advise to post **specific questions in appropriate forum areas**, as these large questions are hard and complex to answer completely: the only thing one can do is to point you to some docs or other sources to give you a blueprint, but nothing too much detailed. Nobody can write a tutorial for your particular case after a bunch of questions.

Hope it helps, good luck.

---

