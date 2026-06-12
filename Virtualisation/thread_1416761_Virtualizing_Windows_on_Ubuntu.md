---
title: "Virtualizing Windows on Ubuntu"
date: 2010-02-26
forum: Virtualisation
---

### Post by Leoq on 2010-02-26
So I want to create virtual Windows on my Ubuntu. I have Ubuntu on a bootable usb. I would love to make my already existing Windows on my laptop the virtual environment so I can run one program. 

I see that there might be problems with this, but I feel like its a possiblity.

Thanks.

---

### Post by Objekt on 2010-02-26
Yes, you can absolutely virtualize Windows in Ubuntu.  I do it because I have a printer which only has Windows drivers.  Ubuntu 9.10 is my main OS (the "host") and I run Windows XP through Virtualbox as a guest, so that I can use the printer.  I can only print from within the virtual Windows machine, but it is better than having to reboot into Windows just to print.

If you only need to run one Windows program, it is fairly easy to install & use Virtualbox OSE.  Virtualbox OSE is in the Ubuntu software repositories, which means you can install it through the Software Center in Ubuntu 9.10.

You may find it useful to browse the "Virtualization Mega Thread" at the top of this forum before you do anything.

I don't know what the one Windows program is that you want to run, but as long as it's not a 3D game, it should work fine on Virtualbox.  

If you need to use any USB devices on the virtual Windows machine, you can do that too.  Just ask if you have any more questions.

---

### Post by Leoq on 2010-02-27
So that works I guess. But Windows in my original system. I boot my ubuntu from a usb. I was wondering if theres a way to virtualize my windows already on my system in the ubuntu environment. 

I don't think that there is. But I feel like there should be a way.

---

### Post by dcstar on 2010-02-27
> **Leoq said:**
> So that works I guess. But Windows in my original system. I boot my ubuntu from a usb. I was wondering if theres a way to virtualize my windows already on my system in the ubuntu environment. 

I don't think that there is. But I feel like there should be a way.

VMware have a free tool to convert an existing Windows install into a VM.

---

### Post by Objekt on 2010-02-27
There is a way to convert an existing Windows install into a Virtualbox virtual machine, but it's somewhat complex.  It's a lot easier to start fresh with a completely new virtual machine.

Is there a specific reason you want virtualize your existing Windows install?  I'm not seeing the benefit of it.

---

### Post by Sticky_Bit on 2010-02-27
> **Objekt said:**
> There is a way to convert an existing Windows install into a Virtualbox virtual machine, but it's somewhat complex.  It's a lot easier to start fresh with a completely new virtual machine.

Is there a specific reason you want virtualize your existing Windows install?  I'm not seeing the benefit of it.

Na. It is really very simple. I had xp on a system and put together my new system with 9.10 on it, while running the old xp system as vm on it.

All you need to do is use the converter tool [http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)
What i did is moved as much data like docs, videos and music off of my xp machine, to external hdd, uninstalled games and apps that i can re-install again if needed, and cleaned everything up, and basically shrunk my old system to around 30-40GB.

Then i ran the converter on it, which creates a vm out of your physical system. I had the vm created on an external hhd. There are a few options you'll want to make sure you but its very simple to do.

When my new system was all set to go, I installed vmplayer 3.0, copied my vm over to partition on the new system, and ran the vm. It was easy and works great. Hope that helps.

edited to add: i used the option on the converter to break the vm up in 2GB blocks. This helps when moving the vm from system to system. For instance my external hdd would not let me creat it there using one big file. The converter also compressed the old system into about a 15GB vm in addition to me shrinking it down to 30-40GB before converting it.

---

### Post by Leoq on 2010-02-28
Thanks, that sounds like it might do what I want. I might give it a try. If I also want the option to boot into the existing without going through the VM can I? also the reason I want to do this is because I don't like vista, so i installed Ubuntu on a usb to operate it instead. but I can't give up my old system because I need to run ArcGIS for school. 

If anyone else has a different solution to this problem let me know. But I think I might have what I need now. We'll see.

---

### Post by Objekt on 2010-03-01
Outline of how virtualization works:

-You boot your installed OS, Ubuntu.  This is called the "host" in virtualization terminology.

-Once Ubuntu is loaded, you run some sort of virtualization program.  

-With the virtualization program, e.g. VMWare, you load the virtual Windows Vista machine.  This is the "guest" system.

-You do whatever you need to do in the guest system.  For example, run your GIS application.

So, there is never a choice of which one to boot.  You will always boot Ubuntu first.  There is no other operating system installed on your real, physical machine - Vista is only virtual.

If that still doesn't make sense, it will once you do it.  Doesn't matter whether you use Virtualbox or VMWare, they work pretty much the same once you have them set up.  

One thing to keep in mind: The virtual machine (guest) will not have direct access to your computer's hardware.  It will use a simulated video card, sound hardware, etc.  Virtualbox has some rudimentary 3D support, but I don't know about VMWare.  Not sure how well 3D works in either.  So far I haven't had any luck in Virtualbox.  3D apps either refuse to run, or have weird glitches when they do run (mouse uncontrollable for example).

---

