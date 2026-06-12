---
title: "Strange PS/2 Issue"
date: 2009-01-10
forum: Windows
---

### Post by jediborger on 2009-01-10
I have a very interesting issue that I can not fully explain. Basically Windows does not recognize the ps/2 ports on my motherboard. Now for the long story.

I recently built a new computer with Intel's new i7 chip. The motherboard is the MSI x58. I love this new power horse and Ubuntu runs swell on it, yes the ps/2 ports work under linux. I decided to install Windows XP SP3 on the machine to play some games and I must say that I've had nothing but trouble getting it to work on this hardware. Really I am proud that Ubuntu detected everything on its own but I would like to figure out why Windows can not use the ps/2 ports, most of the time. Strangely enough the ps/2 ports work about every fourth boot into Windows. I have yet to have them work on a cold start, but if I boot into Ubuntu and then restart into Windows, the ports work most of the time. I have upgraded the bios to the latest version MSI provides. I know I'm living a little in the past by using a ps/2 keyboard and mouse but this problem just does not make sense to me. Why would Windows recognize the ps/2 ports only some of the time?

If anyone in this community has any insight/experience, it will be greatly appreciated.

---

### Post by jrusso2 on 2009-01-12
Did you check in the device manager and see if there are any devices with no drivers or ? marks or ! in yellow?

---

### Post by forrestcupp on 2009-01-12
You need to install the motherboard drivers.  Since hardware vendors don't make drivers for Linux a lot of times, they have to reverse engineer support for hardware and work it into the kernel.  So the Linux kernel automatically has to support a lot of different kinds of hardware.

Windows doesn't work like that.  Everyone makes drivers for Windows, so MS doesn't have to worry about it.  So you have to install your motherboard drivers.

It doesn't really apply, but Vista seems to have a lot more drivers built in than XP does.

---

### Post by jediborger on 2009-01-12
I have  installed all drivers that MSI provides to the latest versions provided online. There are no errors or alerts listed in the Devive Manager. Is there a way to drill down to just deal with the ps/2 controller? I don't see anything listed but a bunch of Intel stuff under System Devives. The strange still is the mouse and keyboard work sometimes. I have yet to get it down to a pattern but I'm trying to find one. Maybe then I will know what the problem is.

---

