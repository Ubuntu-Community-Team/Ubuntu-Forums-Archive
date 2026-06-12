---
title: "Grandchild has school holliday's"
date: 2021-08-06
forum: The Cafe
---

### Post by oui on 2021-08-06
HI
Grandchild has school holliday's and we have to help to watch...
Yesterday: "You, Granddad, it's right, you have Linux? What is Linux really? I know M$-Windows and an other system on my phone, but Linux..."
I did begin to explain, like 25 y. ago in the past for my son, the dad, but, it was different, as Linux and Windows are different and at that old time, son did know MS-DOS and actual Windows young users don't know the function of the DOS substructure of Windows...
«Linux, it is twice! It is a kernel with great functions as bundle for the famous Linux's, the distributions or ...
... Android»
"Can Linux do somewhat alone?"

Good question! Famous question!!

I can remember that I did copy probably about 10..15 y ago one article about the thematic somewhat like MAKE A EXTREMELY MINIMAL LINUX YOURSELF WITH SIMPLY ONE KERNEL and a few other things... And did search the article on my HD. Today, no way to find it again!

Can somebody help me, can we perhaps start an experimentation here for children in school holiday:

WHAT CAN REALLY THE LINUX KERNEL DO ALONE?

WHAT IS TO ADD MINIMALLY TO DO SOMEWHAT?

HOW TO START IT SIMPLY?

Compared with M$-DOS where you need system.sys to start and that is good, with command.com and autoexec.bat, you can immediately make some actions (very few, but you can) in commando line if you did feed the partition with some tests files.

What can we offer in Linux to save a system on a minimal partition, to start it for ex. using grub (or more simple if possible), is an initrd a need and how to build it, how to boot it and which shell commandos are with only the kernel available? Can we use any kernel for ex. simply copied from an actual Ubuntu or do we need to build especially one fresh simple kernel ourself.

What can be the next steps (on MS-DOS compared with the action, I would add some editor etc etc.)?

Can Android also play a role in this consideration of absolutely minimal system?

How to grow all that rationally and step by step?

---

### Post by Tadaen_Sylvermane on 2021-08-06
[https://www.linuxfromscratch.org/](https://www.linuxfromscratch.org/)

I'm not sure how much that will be something for you. But it's a barebones build from the ground up. Very minimal. I've debated doing a build myself but I'm just too lazy.

---

### Post by grahammechanical on 2021-08-06
MS-Dos - Microsoft Disk Operating system. It was run from a floppy disc. I still have a floppy disc with a Linux operating system on it that could be used as a kind of rescue disk.

Ubuntu server would be a Linux command line OS. It would have some default applications that are useful to server operating systems. Something else to look at is a Netboot installation. There is an image available for Ubuntu 18.04

[https://cdimage.ubuntu.com/netboot/18.04/?_ga=2.14324983.1753932966.1628280255-2087616830.1622927185](https://cdimage.ubuntu.com/netboot/18.04/?_ga=2.14324983.1753932966.1628280255-2087616830.1622927185)

If I remember correctly everything is downloaded from the internet and the user gets to choose which packages and applications to download and install. You could choose to have a very basic Linux command line OS on which, after installation you start installing from the command line a desktop environment and a user interface. Or, you can select a desktop interface of your choice. Depending on your selection you may have a few desktop utilities and no applications or a full set of utilities with default applications.

I would not describe this as fun for the kiddies but it is educational.

Regards

Edit: Debian also has a Net install ISO image. With Debian there will not be any non-free software. It will all have to be installed afterwards.

[https://www.debian.org/distrib/netinst](https://www.debian.org/distrib/netinst)

---

