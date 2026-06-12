---
title: "Virtual Machine Won't Start (VirtualBox)"
date: 2008-05-05
forum: Virtualisation
---

### Post by Twizzle on 2008-05-05
I recently did a fresh install of 8.04, and have just downloaded and installed VirtualBox (not the OSE version).

It seems to start ok, but when I try and setup my first Virtual Machine (XP), I click Start and a new window opens with 'starting the virtual machine' and it just sits at 0%.

I can't close it and have to reset my computer to get rid of it / shutdown etc.

I have tried using an ISO and the CD of XP but both are the same.

All the other settings are as standard, the only thing I have changed is the mountdevsubfs file to enable USB.

---

### Post by cb951303 on 2008-05-05
there has been a bug with 1.6 version of vb.
try disabling vt-x/amd-v

---

### Post by Twizzle on 2008-05-05
I have done that in VB it's self. Do I have to do it in my Bios too? If so, will this affect the performance of Ubuntu normally?

---

### Post by cb951303 on 2008-05-05
> **Twizzle said:**
> I have done that in VB it's self. Do I have to do it in my Bios too? If so, will this affect the performance of Ubuntu normally?

it should be enough to disable it in virtualbox.

and no, if you disable virtualization instruction from bios, it wont affect ubuntu's performance (not that you need to disable it) ;)

---

### Post by Twizzle on 2008-05-05
Hmm, still no luck and still hanging at the 0% mark...

I guess I will have to give VMWare a go instead.

---

### Post by Twizzle on 2008-05-05
Can any one tell me how to completely remove Virtual Box. As I did not install the OSE version I can't use the normal Add / Remove option. :confused:

<EDIT> Sorry - Stupid me did not realise that when I installed the non OSE version it added it to Synaptic. Uninstalling now! <EDIT>

---

