---
title: "Just a couple of non workies"
date: 2007-12-26
forum: Virtualisation
---

### Post by mikee55 on 2007-12-26
Hi all, having a good xmas?

I've got Virtualbox running XP in my Gusty host. Just wanted to run Steinberg's Wavelab. I got XP installed and now I can't Drag n Drop files from Host to Guest, I told it to share Documents but nothing happens, I drag a folder over let go click and it sails back to Documents by itself. I can't mount any  ISO images/ or even the host drive. What have I missed?

Cheers Mike:guitar:

---

### Post by stalker145 on 2007-12-26
> **mikee55 said:**
> Hi all, having a good xmas?

I've got Virtualbox running XP in my Gusty host. Just wanted to run Steinberg's Wavelab. I got XP installed and now I can't Drag n Drop files from Host to Guest, I told it to share Documents but nothing happens, I drag a folder over let go click and it sails back to Documents by itself. I can't mount any  ISO images/ or even the host drive. What have I missed?

Cheers Mike:guitar:

I haven't tried sharing folders yet, but I can tell you that mounting ISO's needs to be done *before* booting the guest OS... if the ISO is on your host, that is.

As for sharing the host CD-ROM, make sure you set that up in the guest's preferences before booting.

---

### Post by popch on 2007-12-27
> **stalker145 said:**
> I haven't tried sharing folders yet, but I can tell you that mounting ISO's needs to be done *before* booting the guest OS... if the ISO is on your host, that is.

As for sharing the host CD-ROM, make sure you set that up in the guest's preferences before booting.

Not quite true. You ***can*** attach an optical drive or an iso image while the virtual machine is running. You do not use the preferences window but the cd icon near the lower corner on the right hand side of the VMBox window (the status bar, if you will).

---

### Post by stalker145 on 2007-12-27
> **popch said:**
> Not quite true. You ***can*** attach an optical drive or an iso image while the virtual machine is running. You do not use the preferences window but the cd icon near the lower corner on the right hand side of the VMBox window (the status bar, if you will).

Thank you for the correction - I learned something new today. You know, I just thought those were pretty lights down there... seriously ;)

---

### Post by popch on 2007-12-27
> **stalker145 said:**
> Thank you for the correction - I learned something new today. You know, I just thought those were pretty lights down there... seriously ;)

It took me quite some while to find that out, and I found it out only because I was too stubborn to believe that they had left out so basic a function.

Sometimes it helps to look at the Blinkenlights.

---

### Post by mikee55 on 2007-12-27
Hi all, Tried all of them, with no joy! On Vista I got to know Mico$oft$ Virtual PC and Vmware products too.Would rather use Vmware.

Cheers Mike:confused:

---

### Post by rickycodie on 2007-12-27
you can use vmware on ubuntu too, it just needs to be compiled. and the package in the repo's is broke and has been since october.

---

### Post by popch on 2007-12-27
> **stalker145 said:**
> Thank you for the correction - I learned something new today. You know, I just thought those were pretty lights down there... seriously ;)

Correction to the correction: I just noticed that the very same function is also available by the even more obvious means of the window menu 'devices'. 

By the way, they (VirtualBox) seem have to left out the Drag&Drop. No mention of D&D in the fine manual. Lots of other interesting features. No D&D, though.

---

### Post by fjgaude on 2007-12-27
Drag & Drop is unstable in VBox, but dead reliable in VMware.

---

### Post by mikee55 on 2007-12-27
Hi all, Im not clever enough yet to Compile, it would be nice though. I just loaded Wavelab up in Wine, but as soon as I get it to except the serial key, the program closes.:(

Ideas on a postcard, please



Mike:guitar:

---

