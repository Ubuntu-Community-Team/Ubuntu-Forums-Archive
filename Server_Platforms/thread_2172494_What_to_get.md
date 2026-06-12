---
title: "What to get?"
date: 2013-09-05
forum: Server Platforms
---

### Post by Arunomi on 2013-09-05
Hi I have a old comp that I tough I could make a server of
but it will not take my hdd.
So Im in the market for new hardware.

What is better Amd or Intel cpu?

How many cores should I have?

Is there some motherboards, cpu's, ram, or graficards that I should not buy?

At first its going to be a fileserver with mysql and a Gateway/router

Later in its life I would want to have it as a backend for spotify, netflix and Tv.

And Im a little intrested in virtual servers.

Many thanks Sean

---

### Post by TheFu on 2013-09-05
The answer is "it depends."

Mixing too many things on a single OS install is NOT a best practice. By using virtual machines, you can segment the risks, but that also means some hardware-based requirements need to be selected specificallly to run well with a virtual machine. This is really important for TV tuners. If you get a network-based tuner, VMs work fine. If you have a PCIx or PCIe tuner card ... well, you are generally screwed.

Mixing a gateway/router with anything else is poor network design. That security device should be simple, 1 purpose, not complex. Running a full Linux OS as a gateway probably isn't a smart idea.  Check out ipcop, smoothwall, and pfSense for that need. pfSense is what all my network security friends recommend - something about Linux crashing under heavy loads whereas BSD just slows down. I've deployed pfSense as clients.

Servers shouldn't have GUIs.  Adding a GUI lowers the overall system stability.  Adding and removing programs, like we tend to do on desktops reduces system stability more.

To answer your other questions, we need to understand your budget. I don't think there is anything as a "backend" for netflix.  Running Netflix on Linux is non-trivial, just so you know. Running any GUI-centric program on a server ... I suppose you can do it - just hope that the video drivers don't crash the entire system. Video drivers tend to be crap and X/Windows leaked lots and lots of memory over the years. Bad for system stability.

So, with all that said - get the cheapest nvidia GPU you can. $20 is perfect for a server.
CPUs - doesn't matter provided it supports VT-x, but get the best band for your budget. Both Intel and AMD are fine.  I like the price point/features of the Core i5 line, but if you want to play with more "server features", make sure that VT-d is supported. I like 4 or more cores, for for most home use it just doesn't matter.

The motherboard will flow from the selected CPU and GPU.

RAM doesn't matter provided it works. The RAM will flow from the selected motherboard. 8-32G depending on the virtual work loads.  8G is more than any desktop needs and I run 6 concurrent VMs on 8G with room to grow. When you don't run Windows, much less RAM is needed.

MySQL is on the way out. MariaDB (100% server compatible) is what all the cool kids run now. ;) Avoiding Oracle is a good thing.

Virtual servers ... Xen, KVM, ESXi, openVZ, VirtualBox, LXC ... if you want to run ESXi, you need to select very specific hardware. The others don't care so much.  It is smart to get ESXi compatible hardware even if you don't plan to run it. Google for "HCL ESXi whitebox" and select your hardware from that stuff.

So .. in short, the answer is "it depends."

---

