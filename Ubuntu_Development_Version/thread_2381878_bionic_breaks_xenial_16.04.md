---
title: "bionic breaks xenial 16.04"
date: 2018-01-06
forum: Ubuntu Development Version
---

### Post by ventrical on 2018-01-06
Installing the bionic daily from Jan . 01/01/18 ISO will break 16.04 in UEFI mode while doing a 'alongside' installation. At this point , 16.04 is unrecoverable but Bionic will boot gnome-wayland.

Regards..

---

### Post by dino99 on 2018-01-06
maybe you share a single /home partition, and got some settings conflicting or overwrited

---

### Post by kansasnoob on 2018-01-06
> **ventrical said:**
> Installing the bionic daily from Jan . 01/01/18 ISO will break 16.04 in UEFI mode while doing a 'alongside' installation. At this point , 16.04 is unrecoverable but Bionic will boot gnome-wayland.

Regards..

I wonder if it's changing something in the EFI boot partition? I've been trying to figure out why a UEFI drive won't boot any longer after switching motherboards. Boot Repair had no effect on it. But [Super GRUB2]("https://www.supergrubdisk.org/super-grub2-disk/") will boot the operating systems.

---

### Post by oldfred on 2018-01-06
Every UEFI install overwrites /EFI/ubuntu folder in the ESP - efi system partition. Similar to the way MBR gets overwriten. 
Best to fully back up the ESP. But once booted, the partition is hidden with umask=0077 in fstab.

I have posted bug reports to let users change /EFI/ubuntu to something else, but nothing.
You can change name in /etc/default/grub      but then it still uses the 3 line grub.cfg in /EFI/ubuntu.
 The have hard coded the location of grub.cfg in ESP.

I have installed Bionic twice, and had no issue other than having to edit this back to UUID & partition my main working install is in.
Have not installed for a couple of weeks will do that again, soon.

```
search.fs_uuid 5c1e1a3f-261f-4da5-a0c2-8f479b3039de root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```

---

### Post by ventrical on 2018-01-06
> **kansasnoob said:**
> I wonder if it's changing something in the EFI boot partition? I've been trying to figure out why a UEFI drive won't boot any longer after switching motherboards. Boot Repair had no effect on it. But [Super GRUB2]("https://www.supergrubdisk.org/super-grub2-disk/") will boot the operating systems.



Look at the screenshot in this post here: [https://ubuntuforums.org/showthread.php?t=2380665&page=3&p=13726611#post13726611](https://ubuntuforums.org/showthread.php?t=2380665&page=3&p=13726611#post13726611)

That was from the bionic current jan. 01/01 with gnome3. I started it up today and  I still get those errors and now 16.04. kaput but will try Oldfred's idea

---

### Post by ventrical on 2018-01-06
> **oldfred said:**
> Every UEFI install overwrites /EFI/ubuntu folder in the ESP - efi system partition. Similar to the way MBR gets overwriten. 
Best to fully back up the ESP. But once booted, the partition is hidden with umask=0077 in fstab.

I have posted bug reports to let users change /EFI/ubuntu to something else, but nothing.
You can change name in /etc/default/grub      but then it still uses the 3 line grub.cfg in /EFI/ubuntu.
 The have hard coded the location of grub.cfg in ESP.

I have installed Bionic twice, and had no issue other than having to edit this back to UUID & partition my main working install is in.
Have not installed for a couple of weeks will do that again, soon.

```
search.fs_uuid 5c1e1a3f-261f-4da5-a0c2-8f479b3039de root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```

My point being is that the BIOS UEFI bug from artful is  now migrated to Bionic? and it's a xenial breaker?

regards...

---

### Post by ventrical on 2018-01-06
Restored the xenial desktop but now have the dreaded llvmpipe.

---

