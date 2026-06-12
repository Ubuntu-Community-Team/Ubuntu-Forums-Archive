---
title: "replacement for wine?"
date: 2010-12-21
forum: Wine
---

### Post by kinderen on 2010-12-21
i hve been using wine a lot. but more then half of the software  that i try to use dont work. or part of it does not work, or even sometimes that the intaller cant even run. all of theys problems have frustrated me a lot. so i was wodering if  the if there was a replacement for it. if yes please tell me. i really want it.

thanks,
vince...

---

### Post by hakermania on 2010-12-21
I don't know any good replacement for wine. You can install virtualbox in your system and install there a windows OS.

---

### Post by WienerWuerstel on 2010-12-21
> **kinderen said:**
> i hve been using wine a lot. but more then half of the software  that i try to use dont work. or part of it does not work, or even sometimes that the intaller cant even run. all of theys problems have frustrated me a lot. so i was wodering if  the if there was a replacement for it. if yes please tell me. i really want it.

thanks,
vince...

Just use native *Linux* Apps because they tend to work on *Linux*. 
There are native *Linux* [Alternatives]("http://linuxappfinder.com/") for almost every *Windows* Application.

---

### Post by kinderen on 2010-12-21
i know about alternatives. but for the software i want, there either is no alternative. or ones that really lack tools that i need.

---

### Post by Robert_Willis on 2010-12-21
Kinderen:

You may want to look into CodeWeavers product  "CrossOver".  It is built "on top" of Wine with some "value adds" which bring about more sophistication and more Windoze program compatibilities.  The only drawback is that CrossOver is not free.  See their website:  [http://www.codeweavers.com/about/](http://www.codeweavers.com/about/)

Note: this is not an endorsement of proprietary software nor of CodeWeavers products - just a hopefully helpful hint to someone with a problem they need to solve.

  BW

---

### Post by cogadh on 2010-12-21
> **Robert_Willis said:**
> Kinderen:

You may want to look into CodeWeavers product  "CrossOver".  It is built "on top" of Wine with some "value adds" which bring about more sophistication and more Windoze program compatibilities.  The only drawback is that CrossOver is not free.  See their website:  [http://www.codeweavers.com/about/](http://www.codeweavers.com/about/)

Note: this is not an endorsement of proprietary software nor of CodeWeavers products - just a hopefully helpful hint to someone with a problem they need to solve.

  BW
While this is a good suggestion, CrossOver is not really built on top of Wine, it actually **is** Wine. CrossOver is the commercial version of Wine with the only major difference being that it has a nice GUI front end that assists with configuration and installation of software. If an application doesn't work in Wine, odds are, it also won't work in CrossOver (there are rare exceptions). Really the only reason to go with CrossOver instead of Wine is you want to support the further development of Wine (proceeds from CrossOver are used to support Wine development).

As for the question at hand, if you want to run Windows applications in a semi-native manner, Wine or its derivatives are your only options. Your only alternative is to run a virtual machine with Windows installed, such as the previously mentioned Virtualbox.

---

### Post by cwwilson721 on 2010-12-21
Amazing what people want, as compared to what things are.

wine actually stands for "**W**ine **I**s **N**ot an **E**mulator". This means that wine is an application that provides SOME of the programming 'hooks' that Windows provides, without actually using Windows code, thus avoiding Windows licencing issues. This allows SOME Windows applications to work, at varying levels of function. Since wine is NOT an emulator, it does NOT provide a 'real' Windows environment for Windows apps to run freely. Some work, most don't, and some work in a limited fashion.

A virtual machine, on the other hand, emulates a hardware space that you can install another OS in, such as Windows, and the OS thinks it's all by itself. Since the hardware is emulated, some functions can be slow (3D video, for one). It also "shares" system memory and CPU usage with the host OS, so you can also run into issues there. However, if you have a legal copy of Windows, and HAVE to run a Windows app, and have the hard drive space, CPU cycles, and memory to spare, it is a viable alternative. Just don't expect gaming to work very well (if at all in some VMs. While VMWare has 3d video emulation, the FPS is horrible.) Examples of VMs are VMWare Player, Workstation, and Server, Virtualbox, and a few others. Personally, I use VMWare Player to run 3 Windows 2008 Server VMs inside my Ubuntu install at the same time on my server box.

As a previous poster said, wine is your ONLY option at the moment to run Windows apps as close to natively as possible on a Linux install. Your other option that will work for 99.9% of Windows apps is a Virtual Machine.

Your choice.

---

### Post by handy on 2010-12-21
Crossover is quite often easier to use than Wine, it is cheap, the support on the forum is great as the dev's watch the forum closely & communicate with the posters when appropriate.

They try to solve problems that come up, & tell their users honestly where their development is up to on whatever is the topic when appropriate.

The Tips & Tricks tab on whatever game/application page on their site, often has very useful information as well.

Honesty permeates the whole Codeweavers site which is surely different to that other bunch's site that folked Wine (in more ways than one).

---

### Post by dino99 on 2010-12-22
Maybe you have not patience or have no skill to find errors then installed/tweaked the missing dll/files

keywords are:
winehq
playonlinux
q4wine
winetricks

---

### Post by khelben1979 on 2010-12-22
> **kinderen said:**
> i know about alternatives. but for the software i want, there either is no alternative. or ones that really lack tools that i need.

Are you sure there is no alternatives? What software is it that does not have a proper replacement that you need?

---

### Post by mastablasta on 2010-12-23
otherwise Windows tends to run Windows software preety well....

---

### Post by cogadh on 2010-12-24
> **khelben1979 said:**
> Are you sure there is no alternatives? What software is it that does not have a proper replacement that you need?
He's probably trying to run games, which there are almost no real alternatives for in Linux, as in, there are Linux games, but there is no Linux version of Bioshock. 

Other than that, there are several applications like chat clients, network management software, certain code compilers, etc. for which there are Linux alternatives, but the alternatives don't have 100% of the functionality of their Windows analog, which for many is more than enough to resort to Wine.

---

### Post by indike on 2010-12-26
Just try a virtual emulator SW like Virtual box and install windows inside. Then any app will run on it.

---

