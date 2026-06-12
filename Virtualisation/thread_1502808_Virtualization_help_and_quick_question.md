---
title: "Virtualization help and quick question"
date: 2010-06-06
forum: Virtualisation
---

### Post by Michael64 on 2010-06-06
I have a few questions that I hope you guys will be able to answer.

What is the best virtualization software? I know of two virtual box and QEMU, which is the best of the two? Are there any better ones?

When you are running windows inside of LINUX isn't very slow? I wasn't to run some programs that Linux-WINE program can not. I have a program called Ace Reader Pro Deluxe that I want to run.

Lastly, when you install windows inside of LINUX if you move your hard drive to another computer will it still run? I know if you install windows XP on a seperate partition and try to run it on another computer it won't work.

Thanks.

---

### Post by Michael64 on 2010-06-06
I have a quick question after install virtual box and getting windows running. The windows virtual box can't see any of my other partitions of the hard drive? How do I get the virtual windows to see like the linux partition or my movies partition?

For example when I get to my computer all there is only the C drive? I need my M, U etc drive.

Also can I update my system using windows updates? Or will that mess virtual windows up?

---

### Post by TheFu on 2010-06-07
> **Michael64 said:**
> I have a few questions that I hope you guys will be able to answer.
I'll try to be helpful, but your questions are VERY broad.

>  What is the best virtualization software? I know of two virtual box and QEMU, which is the best of the two? Are there any better ones?There is lots of different types of virtualizaton software available. Which is best will depend on your skill, what you want to do and what hardware you have. There is not "best" for everyone since we are all different and our situations are different. Choosing the best software for you will take research. However, I'd suggest that you start with VirtualBox knowing nothing about you, your skills, or your system(s). To learn more, there is a list of virtualization methods on wikipedia ... [http://en.wikipedia.org/wiki/Comparison_of_platform_virtual_machines](http://en.wikipedia.org/wiki/Comparison_of_platform_virtual_machines) Enjoy.

>  When you are running windows inside of LINUX isn't very slow? I wasn't to run some programs that Linux-WINE program can not. I have a program called Ace Reader Pro Deluxe that I want to run.Is Windows Slow? Sometimes yes, sometimes no. It really depends on the hardware, the installation, the configuration, and the programs. I have 1 vbox system that runs WinXP Pro and it is SLOW. The hostOS is slow on that machine too. I have another vbox system running WinXP-Home and it is FAST! Faster than I recall it ever being on any other hardware. 

Trying to get something working under WINE first is a great idea. Be certain to read the winehq FAQs for that program and use the WINE-tweaks.

>  Lastly, when you install windows inside of LINUX if you move your hard drive to another computer will it still run? I know if you install windows XP on a seperate partition and try to run it on another computer it won't work.For this answer, I'd like to say 100% yes, but I cannot. Because the Linux can be moved more easily between system and the hardware seen inside a virtual machine is ... uh ... virtual, you'll have a much better chance of it working. I've moved Linux installs between different CPU types, motherboards, etc and never had an issue provided the OS and CPUs were 64-bit and the RAM wasn't tiny compared to the original system. Sometimes I've had to find network and disk controller drivers, but I was always able to get Linux running on the newer system.

If you share your CPU model number, RAM, and specific host/client OSes, I suspect better answers for you will come. A little research on your part will go a long way too.

Good luck.

---

### Post by TheFu on 2010-06-07
> **Michael64 said:**
> I have a quick question after install virtual box and getting windows running. The windows virtual box can't see any of my other partitions of the hard drive? How do I get the virtual windows to see like the linux partition or my movies partition?

For example when I get to my computer all there is only the C drive? I need my M, U etc drive.

Also can I update my system using windows updates? Or will that mess virtual windows up?

Look up "Shared Folders" in the virtualbox help file.
In my experience, Windows Update works the same in virtualbox as it does without.

---

### Post by Michael64 on 2010-06-07
Hey thanks for the help I got virtual box running and everything but I am wondering would virtual box running windows be able to handle a new game like Dark Void? It was released this June.

---

