---
title: "Is VirtualBox the best VM? and What is the system requirement?"
date: 2008-12-01
forum: Virtualisation
---

### Post by asaren on 2008-12-01
Hi Guys,

Is VirtualBox the best VM? and What is the system requirement?

I have found that many thread recommended Virtualbox for installing WindowsXP inside Ubuntu. What i need is to run Windows application perfectly in Ubuntu. Is Virtualbox suitable?

My computer is PentiumD 2.00GHz and ~700MB ram is enough for Vrirtualbox?

Thank you

---

### Post by Greyed on 2008-12-01
Yes, that is enough.  As for it being the best that is like asking what the best vehicle is.  Lots of vehicles get you around.  Some go fast, some have two wheels, some carry lots of cargo.  What is best depends on whether you have to go fast, in tight quarters or carry lots of stuff.

The good parts about VirtualBox are that it is relatively simple to setup/get operational and it is FOSS (for the non-PEUL version).  The closest comparison is VMWare which isn't FOSS.

---

### Post by howefield on 2008-12-01
Virtualbox is an excellent program and I would expect will become even better with Sun behind it.

Requirements for running Virtualbox is explained here..

[http://www.virtualbox.org/wiki/End-user_documentation](http://www.virtualbox.org/wiki/End-user_documentation)


If 700 meg the total ram you have in your computer, it is on the tight side for running a virtual machine, but should work.

---

### Post by davidbilla on 2008-12-01
VirtualBox is really a good thing. I have both VMWare and VirtualBox installed on my system. You can try both and decide for yourself, really! Just install it from synaptic and set it up. The whole thing won't take 10 minutes.

> 
My computer is PentiumD 2.00GHz and ~700MB ram is enough for Vrirtualbox?


Your RAM has nothing to do (i.e., not anything new apart from the fact that more RAM generally speeds up your system) with VirtualBox. It actually has a lot to do with how much RAM you assign to your virtual os inside. About 400 MB for Windows XP should make the virtual os reasonably fast enough.

---

### Post by albandy on 2008-12-01
It depends on what do you want to virtualize, for virtualize a Windows S.O. it's a very good software, but Xen is better virtualizing Linux because of paravirtualization.

---

### Post by linuxvacuum on 2008-12-01
Yes it is the best. The only problem that can arise is when using USB devices. Not every USB device works under VirtualBox. Also, forget about 3D games #-o

---

### Post by HermanAB on 2008-12-01
In general, Virtualbox is easier to install and get to work than VMware.  However, whereas Virtualbox works on most systems, VMware works on all systems.  So, try Virtualbox first.

---

### Post by Greyed on 2008-12-02
> **albandy said:**
> It depends on what do you want to virtualize, for virtualize a Windows S.O. it's a very good software, but Xen is better virtualizing Linux because of paravirtualization.

This is not true.  I have a work laptop that has WinXP installed.  I cannot uninstall WinXP and when at work I must use WinXP to connect to the network and to run work related applications.  Xen allows me to virtualize Linux under those conditions how, exactly?

Unless one is running a VM leasing site virtualizing Linux on Linux when you can just run Linux seems kinda pointless.  On the other hand I did at one time entertain the notion of virtualizing my server box so its three roles were split out from one another.  ;)

---

### Post by zero244 on 2008-12-06
I cant run Virtualbox on my Edgy install because it requires a couple of lib files I cant get for Edgy.
I do run Vmware Player and it works very well........you can even copy and paste files to and from Linux or vice versa.
No 3d support but USB devices work fine.
Vmware Player will run most Windows programs that dont require video acceleration.
You can even run photoshop pretty well.
Office XP works great etc.
Right now I am downloading and listening to music from a XP VM while I type this in Firefox on Ubuntu Edgy with Beryl running without any problems.

---

