---
title: "dm_crypt/LUKS mounting swap without passphrase"
date: 2011-05-13
forum: Security
---

### Post by bradmont on 2011-05-13
(apologies if this doesn't belong in the security forum)

I'm running 11.04 on my laptop, and I've got it set up with LVM and dm_crypt/LUKS.  The encrypted volumes are within separate LVMs (I did the nesting this way so I can reassign partitions to volumes across multiple OS installs).  My goal is to have a single passphrase prompt on boot.  My partitions are as follows:

```
/boot, unencrypted
/, encrypted, unlocked with passphrase at boot.  Contains encryption key for:
/home
swap partition
```

I followed the instructions at [http://ubuntuforums.org/showthread.php?t=837416]("http://ubuntuforums.org/showthread.php?t=837416") to set up the passphrase and so on.  This has worked for /home, but not for the swap.

So now, on boot, I am prompted for a passphrase for /, then immediately for a passphrase for the swap space.  /home now mounts without input, as expected, using the keyfile.

I tried commenting out the swap space in my fstab to try activiating the swap manually later, but I was still immediately asked for a passphrase for the swap on boot.

Any suggestions?

---

