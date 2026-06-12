---
title: "[SOLVED] BIOS EDD Suooprt - missing in 8.10?"
date: 2008-10-31
forum: Server Platforms
---

### Post by Krupski on 2008-10-31
Hi all,

I used to use "dd" to save an image of my boot drive (a 4 GB flash card) by referencing device "/dev/disk/by-id/edd-int13_dev80".

This was, by the way, with Ubuntu 64 bit server edition 8.04.1

Now, I upgraded the server to 8.10 64 bit and the EDD disk references are missing!

Removed? Bug? I screwed up? Any ideas?

Thanks!

-- Roger

---

### Post by Krupski on 2008-10-31
Nevermind - solved!

Only need to add "edd=on" in "/boot/grub/menu.lst":

```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=[COLOR="Red"]**edd=on**[/COLOR]

```

...then run...

```

sudo update-grub

```


-- Roger

---

