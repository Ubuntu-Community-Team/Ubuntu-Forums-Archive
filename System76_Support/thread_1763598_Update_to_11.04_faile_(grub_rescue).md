---
title: "Update to 11.04 faile (grub rescue)"
date: 2011-05-20
forum: System76 Support
---

### Post by adakite on 2011-05-20
Hi Guys,

 I tried to update my system76 (Lemur) from 10.04 to 11.04. The update run well but after rebooting the system, I got 

```
error: symbol not found: 'grub_env_export'
grub rescue>
```

I tried to deal with some grub rescue tips, but for some reasons the ls command gives me this strange return:
```
(hd0) (hd0,msdos5) (hd0,msdos1)
```

while no fat partitions are present on my system as only Ubuntu were installed by System76. Which is odd as well is that ls (hd0,msdos1)/boot/grub gives expected return (lot of *.mod files and so on) so something very funky happened during the update. 

Anyways, I thus created a bootable usb-stick from 11.04 (amd64) iso using dd command on my other laptop (Apple Macbook). this last is able to mount it, unfortunately, the Lemur isn't. I configured the Lemur so as to boot on the USB stick, but apparently is not able to do it correctly as I always get the grub error message mentioned previously.

 I don't really care about my data, but I would really appreciate to use my lemur. 

Is there any chance to have a clean install from USB, as lemur does not have any optic reader?

What did I miss?

Thanks for any help/ideas/suggestions&#8230;.

A.

---

### Post by isantop on 2011-05-20
Currently, it's not possible to create a Bootable USB drive from Mac OS X. Do you have another Ubuntu system or a Windows system from which to create the flash drive?

---

### Post by adakite on 2011-05-20
Hi isantop,

Actually I found that unetbootin (available for Win, OS X and Linux on sourceforge.org) is able to create a correct bootable USB Stick. I've just try it on my Mac and this works! I can use my USB as a bootable disk on my System76 Lemur. 

Apparently 'dd' does something odd when copying the ISO data into the USB stick. 


unetbootin seems to be THE solution for everyone. 

Cheers,
A.

---

### Post by adakite on 2011-05-20
Hi,

after have installed Ubuntu 11.04, everything seems to work fine except wireless. I install System76 plugin, but does seem to install anything. I tried to restore the system (from the System76 planel) the same. Wireless does not work. Of course I pay attention that wireless is switch on (FN+ F11).  The Network Tools  shows only Eth0 (ethernet card). How can I make my wireless back to work?

Thanks a lot,
 A.

---

### Post by isantop on 2011-05-23
Please go ahead and run this command from a terminal:

```
cat /etc/network/interfaces
```

Then post the output here. I'll check your configuration files and make sure they're set up properly.

---

