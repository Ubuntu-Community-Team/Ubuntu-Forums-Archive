---
title: "Prevent kernel initramfs extraction"
date: 2010-07-16
forum: Security
---

### Post by executivul on 2010-07-16
Hello,
I'm writing here because it's mainly a security issue even though it's rather kernel related.

I'm compiling my own vanilla kernel with an initramfs included in the bzImage. That image contains encryption keys for the rest of the system. Even though it's not for everybody the initramfs image can be extracted from the kernel, decompressed and the keys extracted.
I'm looking on a way to prevent this. 
Any help/ideas are welcome.

---

### Post by Agent ME on 2010-07-16
Can you set the permissions so it can't be read by users? (Or am I misunderstanding the problem?)

---

### Post by bodhi.zazen on 2010-07-16
Physical access = pwnage

Keep /boot on a removable flash drive =)

Do not mount /boot in fstab.

Once initrd and the kernel are loaded, remove the flash.

---

### Post by executivul on 2010-07-19
The systems are booting over the network. in a 2 stage mechnism:
1. Kernel containing the initramfs is served via TFTP which is a non secure protocol, so everybody can tap into and download the pxelinux and kernel.
2. Kernel boots the initramfs and with the key provided inside downloads the rest of the system to ram and starts the normal boot process. 

Extracting the initramfs from the TFTP downloaded kernel it's not very simple but it can be done, thus allowing the hacker to download the rest of the system.
That's what I'm trying to prevent.

@bodhi.zazen: The initramfs is cleard when switching root into the main image, so not  mounting in fstab does not provide any more security. No USB storage involved in using the system and I would like to keep it that way.

PS: sorry for my English, not my native language.

---

