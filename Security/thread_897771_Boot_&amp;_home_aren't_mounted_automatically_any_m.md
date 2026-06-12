---
title: "Boot &amp; home aren't mounted automatically any more (cryptsetup LUKS)"
date: 2008-08-22
forum: Security
---

### Post by psie on 2008-08-22
Hey,
I am experiencing the problem that suddenly today my laptop doesn't boot anymore properly. 

It is somewhat weird. My system prompts me for my password as usual, accepts it but then it stops while:
```
*Starting early crypto disks...
```
*What does this actually mean? What happens at this point?*
When pushing "ctrl+alt+del" twice the boot process goes on with the following command:
```
init:rcS mani process (2748) killed by TERM signal
init: rc6 main process killed by TERM signal
``` until:
```
*Starting ACPI services...
```
From there I am able to use a shell by pushing "crtl+alt+F2" and log in. I find my / being mounted but not my /boot or /home partition! I can mount my /boot partition manually (which of course isn't encrypted), but I _can't even decrypt my /home_ partition using:
```
sudo cryptsetup luksOpen /dev/hda3 hda3
```

**I really don't know how to fix all this! How can I? And where should I start? I didn't change anything, as far as I know!**

By the way, I am able to decrypt and mount the /root and /home partition via a Live-CD, so I would be able to save my data but I don't want to loose all my settings!

Please someone help me to get my system back to work... :(

---

### Post by hyper_ch on 2008-08-23
are your encrypted devices in the /etc/crypttab referenced by their UUID or like /dev/sdX?

---

