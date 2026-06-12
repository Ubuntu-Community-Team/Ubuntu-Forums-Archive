---
title: "Is it possible to overwritte disk encryption software?"
date: 2009-02-23
forum: Security
---

### Post by Diabolis on 2009-02-23
Is it possible to overwrite disk encryption software? No to steal information or recover passwords, but just to be able to reboot.

I ask this because I ran into the following problem:

I installed DiskCryptor, but for some reason my password is not recognized when the computer restarts.

Fortunately I just encrypted a 256MB partition, so I deleted it with a live-cd and rebooted. However, I-m still being asked for a password.

After that I deleted the whole windows installation and rebooted, it still asks for the password... So I figured that the only way this can work is if the part of [DiskCryptor]("http://www.diskcryptor.de/en/") that asks for the password is installed in the MBR or something like that. How can I delete it?

---

### Post by HermanAB on 2009-02-23
Note that erasing a disk with dd does exactly that - using these instructions you will erase the whole disk.  If you have more than one disk and erase the wrong one, don't complain about it, take it like a man...

The partition table is stored in the first few hundred bytes of the disk.  So if you don't mind losing *all* your data, then you can delete it using dd:
$ sudo dd bs=1024 count=1 if=/dev/zero of=/dev/sda

You can use the same method to overwrite the entire disk (resulting in the same net effect), but it will take a long time.  In this case, simply don't tell dd when to stop, so it will carry on till the end of the disk:
$ sudo dd if=/dev/zero of=/dev/sda

Cheers,

Herman

---

### Post by Diabolis on 2009-02-23
> **HermanAB said:**
> If you have more than one disk and erase the wrong one, don't complain about it, take it like a man...


Sometimes I say that too :popcorn:

So I was about to try the dd command, but I had to do some work before and I did a emergency Ubuntu install in a new partition and it fixed the problem!

I conclude that reinstalling grub overwrote the left overs of DiskCryptor.

---

