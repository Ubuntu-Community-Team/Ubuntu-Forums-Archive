---
title: "grub with luks support"
date: 2011-03-08
forum: Security
---

### Post by skraps on 2011-03-08
Has anyone tried encrypting the boot partition to prevent the kernel from being modified.

Iv tried following this but I'm running into issues when building.

[http://xercestech.com/full-system-encryption-for-linux.geek](http://xercestech.com/full-system-encryption-for-linux.geek)

Im using the source from 

bzr checkout [http://michael.gorven.za.net/bzr/grub/luks3](http://michael.gorven.za.net/bzr/grub/luks3)

Last time I tried I screwed grub and it wouldnt boot.

---

### Post by bodhi.zazen on 2011-03-09
You could probably do this with a custom initramfs. Simply include dm-crypt in the initramfs and write a script to decrypt /boot.

I do not know of a detailed walk through to accomplish this, but this will get you started :

[http://en.gentoo-wiki.com/wiki/DM-Crypt_with_LUKS#Creating_initramfs_image](http://en.gentoo-wiki.com/wiki/DM-Crypt_with_LUKS#Creating_initramfs_image)

Should be "rather trivial" (After writing a custom initramfs of my own I think this would be easier).

Honestly, I think it is easier to simply keep /boot on a removable device.

---

### Post by psusi on 2011-03-09
> **skraps said:**
> Has anyone tried encrypting the boot partition to prevent the kernel from being modified.


That won't prevent you from booting a modified kernel.

> **bodhi.zazen said:**
> You could probably do this with a custom initramfs. Simply include dm-crypt in the initramfs and write a script to decrypt /boot.

No, the initramfs is run by the kernel after grub has already booted it.

---

### Post by skraps on 2011-03-09
I'm confused. initram is stored on the /boot partition. How would making a custom initram do anything is I encrypt the partition it is on?

---

### Post by bodhi.zazen on 2011-03-09
> **psusi said:**
> No, the initramfs is run by the kernel after grub has already booted it.

I was not aware of that, I thought the initramfs was loaded by grub, then the kernel. I know you can build an initramfs into the kernel, but I thought you could have a separate initramfs and chain initramfs as well.

---

### Post by skraps on 2011-03-09
> **psusi said:**
> That won't prevent you from booting a modified kernel.



No, the initramfs is run by the kernel after grub has already booted it.


How would it not prevent a modified kernel from being loaded, with a encrypted /boot partition that means the attacker needs to crack the /boot partition before being able to modifying the kernel. Im only talking about hacking the machine locally, not remote exploits.

---

### Post by bodhi.zazen on 2011-03-09
> **skraps said:**
> How would it not prevent a modified kernel from being loaded, with a encrypted /boot partition that means the attacker needs to crack the /boot partition before being able to modifying the kernel. Im only talking about hacking the machine locally, not remote exploits.

If one has physical access one can provide a kernel so encrypting the kernel / boot partition does not add much, if anything, beyond encryption of / , /home , and swap.

---

### Post by skraps on 2011-03-09
They have to get the "salt" for the encryption off the boot partition before being able to run a differnt kernel on a encrypted system.

---

### Post by psusi on 2011-03-09
> **bodhi.zazen said:**
> I was not aware of that, I thought the initramfs was loaded by grub, then the kernel. I know you can build an initramfs into the kernel, but I thought you could have a separate initramfs and chain initramfs as well.

It is *loaded* by grub, but *run* by the kernel.  As far as grub is concerned, it is just a data file being passed to the kernel as an argument.

> **skraps said:**
> How would it not prevent a modified kernel from being loaded, with a encrypted /boot partition that means the attacker needs to crack the /boot partition before being able to modifying the kernel. Im only talking about hacking the machine locally, not remote exploits.

Plug in USB flash stick; boot whatever kernel you want.

---

### Post by skraps on 2011-03-09
Yeah if you allow boot from a usb, and even then they couldnt modify any of the partitions without first cracking the salt/password used with the encrypted partitions.

---

### Post by bodhi.zazen on 2011-03-09
> **psusi said:**
> It is *loaded* by grub, but *run* by the kernel.  As far as grub is concerned, it is just a data file being passed to the kernel as an argument.

I see that now, thank you for the information.

---

