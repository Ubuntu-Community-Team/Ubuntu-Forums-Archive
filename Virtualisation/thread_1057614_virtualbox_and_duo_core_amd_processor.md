---
title: "virtualbox and duo core amd processor"
date: 2009-02-02
forum: Virtualisation
---

### Post by wildmanne39 on 2009-02-02
Hi everyone, can anyone tell me how to get vista inside virtualbox to see both of my cpus? I am running hp laptop amd64 duo core with 2.5 gigs of ram can anyone tell me how to get vista to run faster in virtualbox? Thank everyone in advance.

---

### Post by HotShotDJ on 2009-02-02
> **wildmanne39 said:**
> Hi everyone, can anyone tell me how to get vista inside virtualbox to see both of my cpus? I am running hp laptop amd64 duo core with 2.5 gigs of ram can anyone tell me how to get vista to run faster in virtualbox? Thank everyone in advance.The OS that is running inside VirtualBox does not see your CPU's at all.  It is running within a virtual (not real) environment.  Very rarely (such as with USB devices and pass-through mode for CDRW/DVDRW's) is the actual hardware exposed to the guest OS.

The best way to get faster performance from Vista is similar to how you would do it on an actual machine... give it more RAM.  Just be careful, you need to leave enough for the Host to run properly.  With 2.5 gig of physical RAM, you should be able to safely assign 1.25 gig to Vista (you might be able to get away with up to 1.5 gig, but giving a virtual machine more than half the system RAM can get a bit dodgy).

You might also try enabling VT-x/AMD-V if your processor supports it.

---

### Post by Neural oD on 2009-02-02
HotShotDJ hit it on the head - give it more ram - if there's to spare. Also why would u need dual core on the vista - doing some video editing etc?

---

### Post by wildmanne39 on 2009-02-02
Hi, thank both of you for your suggestions, I am already doing what you both suggested and I am going to order more ram.  I really appreciate both of your help.



QUOTE=HotShotDJ;6661236]The OS that is running inside VirtualBox does not see your CPU's at all.  It is running within a virtual (not real) environment.  Very rarely (such as with USB devices and pass-through mode for CDRW/DVDRW's) is the actual hardware exposed to the guest OS.

The best way to get faster performance from Vista is similar to how you would do it on an actual machine... give it more RAM.  Just be careful, you need to leave enough for the Host to run properly.  With 2.5 gig of physical RAM, you should be able to safely assign 1.25 gig to Vista (you might be able to get away with up to 1.5 gig, but giving a virtual machine more than half the system RAM can get a bit dodgy).

You might also try enabling VT-x/AMD-V if your processor supports it.[/QUOTE]

---

