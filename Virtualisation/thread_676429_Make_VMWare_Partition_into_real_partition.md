---
title: "Make VMWare Partition into real partition"
date: 2008-01-23
forum: Virtualisation
---

### Post by .Michael on 2008-01-23
Is there a way to make it so the Ntfs drive can be a real partition then add it to grub conf?

Its way to slow in vmware.

---

### Post by dark_phantom on 2008-01-24
That would defeat the purpose of a VM, since you won't be running multiple OSes at the same time.  That would be called dual booting, which is what you're describing.

---

### Post by blaise1011 on 2008-01-24
I gotta agree with mike.. is there? VMware is slow as .... and i cant make a duel boot cause my computer doesnt support XP (the OS i originally wanted)

---

### Post by HermanAB on 2008-01-24
With a Windows VM, you can do things like that using the VMware Convertor.

You can then run Windows directly (dual boot) or as a VM from inside Ubuntu.  However, you need a cracked WinXP off the Pirate Bay to do that or Windows will ask you to re-register each time you reboot...

Cheers,

Herman

---

### Post by LordKelvan on 2008-01-24
Hi:

The activation problem occurs because each time you switch between the two boot methods, Windows finds a bunch of "new hardware" (i.e., it switches between "finding" your real hardware and VMware's virtualized hardware).  I do believe you can get around the activation problem by having separate hardware profiles (i.e., "Regular" for when you boot up normally, and "VMware" for when you boot up inside a VM).  So when booting Windows, you just pick the appropriate hardware profile, and you are done.  Just Google for "running vm off existing Windows install" or something similar.

---

### Post by dcstar on 2008-01-26
> **blaise1011 said:**
> I gotta agree with mike.. is there? VMware is slow as .... and i cant make a duel boot cause my computer doesnt support XP (the OS i originally wanted)

Any VM will be slower than a native boot - but that is the price you pay for the flexibility of simultaneously running multiple O/Ss on one set of hardware.

And for the record, my VM version of XP runs slower than a Windows boot, but more than well enough to do anything I need.

I also run all my VMware VMs in a separate high performance ReiserFS partition, I have found that this provides superior performance than using your "default" Linux partition that is also handling your base O/S.

There are also HOWTOs around on how to optimise Windows to run in a VM, if you don't implement these you are just handicapping yourself (immensely).

---

