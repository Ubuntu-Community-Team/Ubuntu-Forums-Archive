---
title: "Virtual Box"
date: 2012-04-03
forum: Virtualisation
---

### Post by Dave_G on 2012-04-03
Hi

I'm using Ubuntu 11.10 and have installed Virtual Box.

I'm looking at removing my other partition of Windows 7 and installing it instead in Virtual Box. Will my current Windows apps of Photoshop CS5, Photomatix etc all run fine in the guest Windows 7?  I've tried Wine but have lost patience with it.

Thanks

Dave.

---

### Post by CharlesA on 2012-04-03
If it's an OEM copy of Windows, it might have issues running in VBox - activation and whatnot due to change of hardware.

But given enough resources, it should be able to run Photoshop and the like, but the performance won't be the same as when it was running natively.

---

### Post by Dave_G on 2012-04-03
Charles, thanks for the reply.

What about if I doubled my laptop memory from 4GB to 8GB; would this boost the performance?

---

### Post by CharlesA on 2012-04-03
It might. The thing is you will be running Windows on top of Linux, so you are basically running 2 OSes at the same time and that can affect performance.

---

### Post by QIII on 2012-04-03
You would probably get a performance boost after adding more physical RAM if you committed more to the VM.

Double your RAM and double the RAM committed to the VM.  (But don't over do it and keep your host from running!)

I often commit 4GB and two of my six cores to VMs, depending on how many I have running.

(And I'd like to tag this on to CharlesA's response:  You may get an OEM copy running without any problems in VBox, but you need to read the EULA carefully.  Some OEM distributions explicitly forbid installation in a VM.)

---

### Post by haqking on 2012-04-03
you can also create additional virtual hard drives and configure those for swap for photoshop (not as in linux swap though you could do that also) but as in photoshop configured swap/scratch 

it will use the physical write to disk (virtual hard disk file) as ram though obviously but may help improve things.

But that being said it depends how intensively you use photoshop, if you are dealing with large raw format images then its probably needed or better off use dual boot, if its just casual photoshop then it will be fine, i have photoshop in a XP VM with 2GB ram assigned and it works fine for casual stuff.

Cheers

---

### Post by CharlesA on 2012-04-03
Oh and use a preallocated vhd instead of letting it do it dynamically. That'll help somewhat.

---

### Post by Rebelli0us on 2012-04-06
I have win7 and Win8 Preview running as guests with only 1GB ram each. Win7 will work fine even with 500MB. The advantage, you can run several OSes simultaneously and whatever apps you need, including Photoshop.

---

### Post by santosh83 on 2012-04-06
> **Dave_G said:**
> Charles, thanks for the reply.

What about if I doubled my laptop memory from 4GB to 8GB; would this boost the performance?

IME at least, I've found that VMs are not good for accelerated graphics, as even though I may have a full-featured video card, the VM usually presents the guest a stock or generic SVGA adapter. The same for the sound card. Thus you find that many advanced capabilities of your hardware are often simply not seen by the guests.

Also even if you give it loads and loads of RAM, with some applications which talk to hardware a lot (I/O intensive), VM will be slower than running on metal, as it catches each I/O request and does special manipulations.

Especially note that if you're a heavy player of modern heavyweight games, VM simply won't do.

---

