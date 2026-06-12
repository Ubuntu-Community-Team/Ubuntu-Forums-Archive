---
title: "[SOLVED]android-x86-4.4-r3 live booting to Root Terminal (No GUI)"
date: 2015-09-22
forum: Ubuntu, Linux and OS Chat
---

### Post by kagashe on 2015-09-22
I am trying to run android-x86-4.4-r3 live on Lenovo G50-45 Laptop which has AMD E1-6010 APU with AMD Radeon R2 Graphics.

I have downloaded EFI image: android-x86-4.4-r3.img from Sourceforge and made EFI Bootable USB Stick.

I am getting Android Boot Menu and selecting the first menu entry to boot live. I am not getting any GUI but getting root terminal.

How can I boot to GUI?

Kamalakar

---

### Post by kagashe on 2015-09-28
I posted on android-x86 forums and was advised to try test builds of android-x86 5.1.1 Lollipop for my radeon card.

I could successfully run android-x86 Lollipop live and could install it to hard disk.
'
Since these images are non EFI, initially I switched to legacy in UEFI BIOS. Later on I learnt to put boot entries in grub 2 and could boot them without changing BIOS to Legacy.

Following are the entries in /etc/grub.d/40_custom
```
menuentry 'Android-x86 5.1 live' --class android-x86 {
	set root='(hd1,msdos1)'
	linux /kernel root=/dev/ram0 androidboot.hardware=android_x86 quiet SRC= DATA=
	initrd /initrd.img
}

menuentry 'Android-x86 5.1 on sdaX' --class android-x86 {
	set root='(hd0,gptX)'
	linux /android-2015-08-16/kernel root=/dev/ram0 androidboot.hardware=android_x86 quiet SRC=/android-2015-08-16 DATA=/android-2015-08-16/data
	initrd /android-2015-08-16/initrd.img
}

```

Kamalakar

---

