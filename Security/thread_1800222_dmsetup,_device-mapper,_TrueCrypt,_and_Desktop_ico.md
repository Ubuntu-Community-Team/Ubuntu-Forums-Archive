---
title: "dmsetup, device-mapper, TrueCrypt, and Desktop icon labels"
date: 2011-07-08
forum: Security
---

### Post by c.cobb on 2011-07-08
Anyone know how device-mapper works, or can someone point me to any docco (other than the man page)?

Couple years ago I wrote a TrueCrypt wrapper script for use on Puppy Linux, and am reworking it for Ubuntu. Puppy sometimes didn't have the 'dmsetup' device-mapper utility available, but TrueCrypt still works without this when the '-m nokernelcrypto' option is used.

My script notices when dmsetup is available and skips this option. When the TC volume gets mounted (somehow using dmsetup), the Desktop icon is labled with the leaf name of the /media/mount_point -- so far, so good.

However, if I force the script to add the no-kernel-crypto option, and the TC volume is mounted without using dmsetup, the Desktop icon ls labled with the size of the volume. Say what?

Running df shows the difference between the two mounts is whether /dev/mapper is used. So *how is* dmsetup making this happen? The manpage isn't much help. Is it just the 'rename' sub-command? I am unable to find any details about this mechanism.
Thank you,

```

With dmsetup: Icon on desktop is labeled 'testing.tc'

Filesystem   Type   1K-blocks   Used Available Use% Mounted on
/dev/mapper/truecrypt2
             vfat        1769      6      1763   1% /media/testing.tc

------------------------------------------------------------------------
Without dmsetup: Icon on desktop is labeled '1.8 MB Filesystem'

Filesystem   Type   1K-blocks   Used Available Use% Mounted on
/dev/loop3   vfat        1769      6      1763   1% /media/testing.tc

```

---

### Post by c.cobb on 2011-07-26
No one knows how this works, huh? Even a pointer to somewhere? 

On a related subject, does  anyone know where / how Ubuntu caches drive icon images, when you have  an autorun.inf file and an icon file in the top-level directory of a  device? There's a subtle issue concerning the deniability of how one is  using TrueCrypt on a system.

Update: I found the icons under ~/.thumbnails/normal/ with different names (08bb589a0ce1c187ecbcbf71f630a6cb.png, 50f265147a8b12498b573d331608d60e.png) but deleting them didn't help. Are they cached in memory? Hope there's a way to uncache them.

---

