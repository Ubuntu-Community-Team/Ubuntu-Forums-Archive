---
title: "vserver kernels for gutsy?"
date: 2007-07-04
forum: Server Platforms
---

### Post by eudoxos on 2007-07-04
Hello,

is there some change of having vserver flavor of kernel in ubuntu archives for gutsy? Debian unstable has it, but I couldn't find the source of the patch and besides that, ubuntu kernels are maintained separately in git. If I had patches, I would be able to build packages and provide them for download. There used to be such possibility in dapper (from uniklu.de).

Regards, Eudoxos.

---

### Post by berryman77 on 2007-10-30
I like to see a vserver enabled kernel also.  I'm having to use a kernel.org build to use my vservers.  Is there an avenue for making formal requests?  I'd like to request this.

Randall

---

### Post by azelter on 2007-11-02
I'd like to see the kernel added too. I would have thought there would be plenty of Ubuntu users out there wanting to use vserver (and openVZ for that matter). Both options seem to have a partial presence in the repositories.

---

### Post by valeryvdr on 2007-11-12
It really would be nice to have a vserver enabled kernel available for gutsy. Is it possible to have any answer regarding the issue at least?

Thanks

---

### Post by azelter on 2007-11-12
From what I can see, you have to build your own kernel at the moment. Debian provide alot of tools to make that easier. Still not ideal though ...

---

### Post by berryman77 on 2007-12-10
The problem is not building the kernel.  The problem is patching it.  I've been unable to cleanly apply the vserver patches and the modifications necessary to make them apply cleanly are beyond me.  I'm using the vserver enabled kernel from Debian and that works OK, but I'm missing out on Ubuntu's patches.

My particular use for vserver is development.  With Vserver,  I don't have to worry about keeping my desktop setup compatible with what I'm working on.  Linux Vserver is simpler to use and has almost no overhead compared to other virtualization solutions.  I've used Xen, Qemu and VMware, but none of them fit this use case as well as Vserver.   I develop on a laptop, so stuff like Suspend to RAM and CPU frequency scaling need to work and I can't afford RAM wastage.  The other solutions fail in one or more of these areas while Vserver has minimal effect on how the system functions.

---

### Post by azelter on 2007-12-10
Interesting. I tried the a debian vserver enabled kernel, but lost acpi power management. As the server I am using is an always-on laptop, I also wanted cpu freq scaling etc. to work, and so dropped the vserver idea. Which exact kernel are you using?

---

### Post by berryman77 on 2007-12-20
debian kernel used is 2.6.22-2-vserver-686 #1 SMP

I'm having troubles that may or may not be related.  Sleep and suspend work most of the time, but the video card (Intel integrated) sometimes spews strange characters on the screen.  Sound system hangs sometimes for an undetermined reason.  Battery charge detected at 51% on boot.  Also, I had to install Debian's vserver utilities.

All this to say that it's a headache and I don't know what's a problem with Ubuntu and not because I'm running Debian's kernel.   But I need (or want) VServer enough to put up with it, but it would be so nice to have a Ubuntu blessed VServer kernel.

Randall

---

### Post by azelter on 2007-12-20
Hmmm. Thanks for the reply. Sounds like I'll be waiting for a little.

---

### Post by markba on 2008-01-21
I created a feature request for providing a vserver enabled kernel, just like debian does:
[https://bugs.launchpad.net/ubuntu/+bug/184764](https://bugs.launchpad.net/ubuntu/+bug/184764)

---

### Post by floberg on 2008-03-03
Yep!
Why do we have :
util-vserver - user-space tools for Linux-VServer virtual private servers
vserver-debiantools - Tools to manage debian virtual servers

in repository othervise ???

/F

---

