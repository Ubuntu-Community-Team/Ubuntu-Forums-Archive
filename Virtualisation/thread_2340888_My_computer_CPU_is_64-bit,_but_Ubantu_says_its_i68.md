---
title: "My computer CPU is 64-bit, but Ubantu says its i686 and wont install 64-bit version"
date: 2016-10-22
forum: Virtualisation
---

### Post by easybullet3 on 2016-10-22
hi,
[U]
Background[/U]:
i'm running a virtual box (Live Linux USB Creator) on my Windows 7 laptop.  (via a USB stick).
I installed Ubantu 14.04 Gnome onto the USB stick (because this is a supported version of the 'Live Linux' software).
My Laptop CPU is an intel 64-bit CPU and running windows 7 (64-bit).

_BUT_:
upon running the Virtual Ubantu on my laptop, it wont boot up because it says I have i686 (32-bit) and i need to have x86_64 (64-bit).

 
I dont understand how ubantu is saying my CPU is 32 bit and not 64bit.

can anyone shed some light ?

---

### Post by QIII on 2016-10-23
Hello!

In your BIOS, look for the [VT-x]("https://en.wikipedia.org/wiki/X86_virtualization#Intel_virtualization_.28VT-x.29") setting and make sure it is set to True/On.  That should allow 64-bit virtualization.

Let us know how that goes.

Cheers!

---

### Post by howefield on 2016-10-23
And moved to the "*Virtualisation*" forum.

---

### Post by easybullet3 on 2016-10-23
> **QIII said:**
> Hello!

In your BIOS, look for the [VT-x]("https://en.wikipedia.org/wiki/X86_virtualization#Intel_virtualization_.28VT-x.29") setting and make sure it is set to True/On.  That should allow 64-bit virtualization.

Let us know how that goes.

Cheers!

Unfortunately, Virtualization was Already Enabled in my BIOS, (so that was not the reason).

Can you think of anything else perhaps ?

Also: for your info: my CPU supports VME, VMX, X64, etc

---

### Post by easybullet3 on 2016-10-23
ok,
UPDATE.
i decided to try 'OneBootin' virtual USB software, and it worked fine.
obviously there was a problem with the 'Live Linux' virtual USB software.

so, the problem has been avoided  ;)

I can now use Ubuntu  ;)

---

