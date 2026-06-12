---
title: "Opinion on Ubuntu running a virual Vista or Vista running a virutal Ubuntu"
date: 2009-06-10
forum: Virtualisation
---

### Post by tgilbert328 on 2009-06-10
I'd like your opinions, I have been having an internal debate on what is the better route.

I am a Windows Developer at my company and use Visual Studio 2008 every day.  However, I also use Ubuntu as a virtual on that machine and use it occasionally.  I am reasonably happy with this.

However, I recently partitioned my work computer and created a small Linux partition.  I was curious about ext4 and whether I could get everything working on my XPS 1330.

Well, it worked very well firstly, my entire 4gb was addressable (using 64-bit), performance seemed better (in linux) with ext4.  Easier access to internet radio, ability to use compiz, etc.

This has tempted me to reverse my virtualization situation.

Linux host with vista Virtual  vs  Vista host and Linux virtual

Has anyone had any experience? opinions?

---

### Post by iposner on 2009-06-15
If Windows is your primary mission-critical work environment, then stick with it. Virtual machines don't offer all the features of a native install (e.g. DirectX). Also check out the peripherals you're using - many GDI printers don't work with Linux and Linux support for scanning via the SANE project is pretty poor.

Having said that, Virtual PC 2007 is not much cop without the Virtual Machine Additions (which MS doesn't provide for Linux) - you have to use a hypervisor-aware version of Linux to get performance, otherwise the VM runs in emulated mode (slow).

In short, don't rely on VMs for performance nor hardware compatibility.

---

### Post by tgilbert328 on 2009-06-15
Thanks for the feedback, I am using VMWare Workstation 6.5 so I don't think Hyper V is applicable since its seems to be a Microsoft add-in to Virtual PC.  

I did have to enable VT on the host machine in order to run a 64-bit version of Vista (fresh install).  That didn't really work out very well.  It seemed pretty quick, then all of a sudden it would just lock up the hard drive for 15-20 seconds and become unresponsive.

I decided try to use my old 32-bit Vista.  So I used VMWare Convert to convert my Windows instance to virtual and save it on the network.  Then I grabbed a new hard drive and put Ubuntu 9.04 x86 on it.

I am now copying the virtual windows computer back to the laptop.

I will report back on performance... if this doesn't work out, I will try a fresh install of a 32-bit version of Vista.  If that fails, I will go back to what I was doing before- all the wiser. :)

Thanks.

Tim

---

