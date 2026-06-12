---
title: "TrueCrypt 6.3a problems - is it Ubuntu or TC?"
date: 2009-12-10
forum: Security
---

### Post by Objekt on 2009-12-10
First, I am running a variant of Ubuntu 9.04, called Kuki Linux 2.8.  It is Ubuntu 9.04 under the hood, with a few modifications to suit the Acer Aspire One netbook (e.g. XFCE GUI instead of the default Gnome GUI).

Second, I would like to use TrueCrypt to protect my data when traveling.  I downloaded TrueCrypt 6.3a and got it installed, but it seems broken.  Whenever I try to mount an encrypted volume file, I get an error dialog with the following message:

```
/proc/misc: No entry for device-mapper found
Is device-mapper driver missing from kernel?
Failure to communicate with kernel device-mapper driver.
/proc/misc: No entry for device-mapper found
Is device-mapper driver missing from kernel?
Failure to communicate with kernel device-mapper driver.
Incompatible libdevmapper 1.02.27 (2008-06-25)(compat) and kernel driver
Command failed
```

What in the world does all that mean?

I've tried creating an encrypted volume on both the Kuki Linux netbook, and also on my Windows XP desktop machine, both running TrueCrypt 6.3a.  The encrypted volume mounts just fine on the Windows machine, and I am definitely entering the correct password when trying to mount it on the netbook.  Nevertheless, I always get the same result on the netbook.

The encrypted volume file resides on an 8 GB micro SDHC card.  It shouldn't matter what it's stored on, but there you are.

I tried asking about this on the official TrueCrypt forums, but that place is dead as the underside of a rock on Pluto.  I hope someone else has tried using TrueCrypt on Ubuntu & will have some idea how to fix this.

---

### Post by michaelzap on 2009-12-10
KL seems to be using a custom kernel compiled specifically for the Aspire One:
[http://www.kuki.me/2009/04/how-to-install-kuki-linux-custom-kernel/](http://www.kuki.me/2009/04/how-to-install-kuki-linux-custom-kernel/)

That may mean that they've removed drivers and modules that they didn't think were essential. I would ask about this on Kuki's forums and see what they tell you. You might need to recompile your own kernel to keep your KL optimizations and add the modules necessary to run TrueCrypt.

You could use EncFS from your Linux system instead, but I gather you want to be able to mount this volume from Windows as well (and TrueCrypt is a good choice in that case).

---

### Post by Objekt on 2009-12-10
Yes, ideally I would want to be able to mount the volume in Windows as well.  The idea is that I would keep a small device - microSDHC card, USB stick, whatever - with all my really important info on it - encrypted.  Using an SD card makes it easy to transfer a reasonable amount of data - say 8 GB - between the netbook & desktop.

Eventually I want to do whole-system encryption.  Using an encrypted volume on a removable storage device would be good for now though.

I did post about this in the Kuki Linux forum, but so far no one has replied.

I'm off to try TrueCrypt 6.3a on my other netbook, which has Ubuntu Netbook Remix 9.10 on it.

update:
Yes, it's definitely a limitation of Kuki Linux 2.8.  I installed TrueCrypt on my Ubuntu Netbook Remix netbook, and have had no problems accessing the encrypted volumes there.

---

