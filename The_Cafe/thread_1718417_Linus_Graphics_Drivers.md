---
title: "Linus Graphics Drivers"
date: 2011-03-31
forum: The Cafe
---

### Post by jennybrew on 2011-03-31
I believe Ive posted several comments relating to the Linux driver model.
Im not a fan and have some reservations about allowing executing code from applications into kernel space. At the very least this seems to run counter to the much vaunted Unix basic principles.

However, Im a novice, having just embarked on a training course, and dont have any
credibility in this area as yet. Maybe one day though :)

A company called Xi Graphics seems to share my reservations, and more, and they
do have credibility.
 
[http://www.xig.com/Pages/Edu/LinuxGraphicsProblems.pdf](http://www.xig.com/Pages/Edu/LinuxGraphicsProblems.pdf)

Any thoughts?

---

### Post by Npl on 2011-03-31
"allowing executing code from applications into kernel space" - well thats a bit broad. If you consider OpenGL (or X-Drivers) as Application then thats true, but otherwise its just a kernel driver like IDE/LAN/USB sending data back and forth to Apps. No code passes from Apps to kernel-level, just data.
This data can be problematic however because the format is very flexible/complicated and could be used for exploits - in other words you need to verify it before processing.

Whatever you do, you wont get around managing gfx-cards in kernel-space, just you should try to make this as simple and small as possible. The more you do the more can go wrong and you dont want thinds to go wrong in kernel-space (simplified). This is the drivermodel that MS uses since Vista and Wayland will do something similar, the X-driver model cant die soon enough

---

### Post by jennybrew on 2011-03-31
> **Npl said:**
> ". This is the drivermodel that MS uses since Vista and Wayland will do something similar, the X-driver model cant die soon enough

Company are sponsoring me through a Windows system development course. If Im successful I will be able to join the dev team. Im not sure if Ill get through the course though as it looks difficult ..and guess what ..it is!
Anyhow .. the Windows model, from what I’ve learned so far, involves programming against a binary interface.
That way the driver and the OS can cruise along in blissful ignorance of each other. The advantages over the Linux model are obvious in my opinion ..but lots of people think otherwise. Like I said Im just a novice yet and struggling at that :)

The article I posted is fascinating reading and explains in some detail why Linux has problems with graphics drivers.
And yes I think you really do have to consider OpenGL is an application.

---

### Post by Npl on 2011-03-31
> **jennybrew said:**
> Company are sponsoring me through a Windows system development course. If Im successful I will be able to join the dev team. Im not sure if Ill get through the course though as it looks difficult ..and guess what ..it is!
Anyhow .. the Windows model, from what I’ve learned so far, involves programming against a binary interface.Uhhh... thats always the case, just that the binary interface on Windows is stable for years while Linux changes it every few kernel version.
For a quick overview: [http://msdn.microsoft.com/en-us/library/ff570589(v=VS.85).aspx]("http://msdn.microsoft.com/en-us/library/ff570589(v=VS.85).aspx"). The important part is that the only thing thats running in kernel-space is handling the state of the hardware, not D3D or OpenGL, and common functionality between drivers is provided by MS.
This is a common scheme on MS OSes, you can just stack a specific mini-driver on top of a generic one.
> **jennybrew said:**
> That way the driver and the OS can cruise along in blissful ignorance of each other. The advantages over the Linux model are obvious in my opinion ..but lots of people think otherwise. Like I said Im just a novice yet and struggling at that :)Its a matter of defining a good forward-thinking interface, on Linux you just get changes from different projects that ultimately end up in the kernel. The interface is made up as they go.
> **jennybrew said:**
> The article I posted is fascinating reading and explains in some detail why Linux has problems with graphics drivers.
And yes I think you really do have to consider OpenGL is an application.As soon as you run it in kernel space its no Application anymore but kernel-mode software. But thats my definition =)

---

### Post by disabledaccount on 2011-03-31
At first, I would say that Linus may have some grphics drivers installed  on his PC, but for sure it has nothing to do Linux driver model :)

It  seems that Your point is that "linux graphics problems" are the effect  of bad driver model. This is VERY complicated area to discuss and MANY  aspects have to be considered.
I'll try make it short:
GPUs have  closed specification - It started to change slowly, but it's far from what is available for regular CPUs. There are serious consequences from this fact - we  have practically 2 manufacturers that can compete in terms of  performance - AMD/ATI and NV. Both of them are making buggy drivers,  both for Windows with it's "stable binary interface" and for Linux.  Hundreds of examples, tens of drivers versions which suffered from  performance and stability issues - just to mention famous crashes of *[SIZE=1][I]ATI2MTAG*.SYS[/SIZE][/I] (windows). So it's not faulty driver model - unless You want to tell that WDM is bad too.
As  oposite, open source drivers for older ATI cards are far more stable,  compatible and often providing better performance than old, discontinued  proprietary versions. (I've made some testing on Radeon X1600) So -  it's not Linux/Xorg Driver Model fault - it was ATI that failed to write  good code - but at that time they've just begun learning Linux :)

Performance:  OpenCL works insanely fast with ATI stream on Linux today (I haven't  worked with NV yet). OpenGL apps: Native opengl linux games are working  without problems. My biggest experience with 3D CAD comes from  Protel/Altium which is using OpenGL for viewing PCBs in 3D and for  drawing in 2D - and it works slow under win - free KiCad is WAY faster  in 3D and it produces better graphics, 2D is comparable - but I agree  that this is not neccessarily good measure.

Xorg: the biggest  problem of Xorg are remote connections - but there are alternate  solutions that can be used. For about 3 years Xorg is growing  dynamically - after rewriting of PCI code most problems with  autodetection of hardware and with stability have been solved.
Xorg  performance: Xi Graphics is right - Xorg can be more efficient, but in  current version it's not so bad - Enlightment is a proove that it can  work very efficiently.
It was designed to be flexible - and it is  extremely flexible - You can mix old S3 Trio with some Matrox and GF480 -  and it will handle all of them - by using native (compatible) drivers. I  wonder if it would be possible with Xi Graphics modifications - I gues  not.

Security: OGL code is regular data for CPU/kernel - it can't  be executed - so it's not more insecure than any other possible holes -  f.e. in sudo.

Few words about "binary stable interface" - it  makes things esier - both for driver programmers and for viruses. One  version of virus will work on every PC. In Linux there is high chance  that slight differences between kernel versions will render it  nonoperational.
Killer app: konbot - Linux is quite resistant of it,  and it's very easy to make it fully resistant - by compiling own kernel  version.

---

