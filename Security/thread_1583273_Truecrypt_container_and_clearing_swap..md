---
title: "Truecrypt container and clearing swap."
date: 2010-09-27
forum: Security
---

### Post by keljaden on 2010-09-27
So, my current plan is to create a truecrypt container with the whirlpool hash.  This container will be located on a hdd that is not where my OS will be located (so a separate physical sata drive).

My concern is when this container is accessed, that some of the password information could be stored in my swap partition (which is on the main drive where the OS "/" is located)

I would like to have a script or command I could run that after I unmount those drives (or just halt the system) that my swap (and ram too if possible) could be wiped (or like overwritten with the shred command).

Also, am I going about this the right way, or should I just use truecrypts FDE on the entire drive? In addition, when Ubuntu does it's default install, does it create a swap file in addition to a swap partition?  If it does, would that be another vulnerability? If it is, how do I prevent this from happening?

I welcome any input you have on this.  I am aware that once the drive is mounted, it is vulnerable, but I want the data to be secure as possible once my computer is turned off.  Also, I have read that there are ram exploits where it holds your passwords for up to a few minutes after you turn the machine off, does anyone know how long that it and is there a way to clear it, or will only time let it fade?

---

### Post by Bachstelze on 2010-09-27
You can't wipe your (entire) RAM while the system is running. ;) Wiping the swap is easy:

```
sudo swapoff -a
sudo dd if=/dev/urandom of=/dev/<swap>
```

And repeat a couple times, then mkswap and swapon.  Or use a swap file instead of a swap partition and shred it.

The RAM is the main problem, but I'd be surprised if the TC devs didn't think of that and, for example, made it wipe the keys from RAM when you unmount a volume.  This is not bullet-proof, though, even if you write over the ram, you still have a risk of a residue of old data, but at that level, you're fighting guys who would probably have no problem using the proverbial $5 wrench.

---

