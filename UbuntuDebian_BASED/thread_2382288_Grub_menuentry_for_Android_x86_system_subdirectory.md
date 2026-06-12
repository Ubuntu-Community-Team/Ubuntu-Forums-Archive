---
title: "Grub menuentry for Android x86 system subdirectory within Ubuntu ext4 partition"
date: 2018-01-11
forum: Ubuntu/Debian BASED
---

### Post by ajirios on 2018-01-11
I have a relatively serious problem. 


I am trying to install Ubuntu on a custom UEFI PC and then install Android x86 (another Linux distro) within it as a subdirectory or in another ext4 partition. The reason why I need to do this is to boot the new system using Ubuntu's UEFI grub2, which I have verified works. The Android install does not have its own grub2. 


I have tried two things:



1) Installed Android x86 inside Ubuntu as a folder without formatting. When the system reboots, it loads Ubuntu operating system, although the Android system is within.

2) Formatted the entire Ubuntu ext4 partition and replaced it with an Android x86 ext4 install. When the system reboots, it loads the grub black screen with the terminal showing only ***grub>*** .

I was told I need to enter a grub menu entry like this:
[I]


[FONT=Arial]It seems Android-x86 cannot install grub bootloader with UEFI / Secure Boot feature enabled.[/FONT]

[FONT=Arial]The only way out I've found - without disabling UEFI / Secure Boot feature - is:[/FONT]

[FONT=Arial]1) installing it alongside (as a sub-directory under) a Linux distro with a working grub bootloader using via a RPM package at [/FONT][https://www.fosshub.com/Android-x86.html](https://www.fosshub.com/Android-x86.html)[FONT=Arial] or via a DEB package (using "alien" tool to convert), and[/FONT]

[FONT=Arial]2) manually adding the following grub menu entry:[/FONT]

[FONT=Arial]menuentry 'Android-x86' --class android-x86 { [/FONT]
[FONT=Arial]        linux /android-???/kernel androidboot.selinux=permissive [/FONT]
[FONT=Arial]        initrd /android-???/initrd.img [/FONT]
[FONT=Arial]}[/FONT]

[FONT=Arial]3) replacing the file "system.sfs" with the "unsquashed" directory named "system" to use the system area in read-write mode (either by extracting or by copying from a direct installation).[/FONT][/I]



But, I'm not sure exactly how this code would boot Android x86 from its system folder... Any help would be appreciated as this is a new DIY.

---

### Post by yancek on 2018-01-11
I don't use any Android devices but the Grub2 entry would need to specifically include the path to the kernel and the initrd files.  The example entry you posted would mean that you have a directory named "android-??? in the root of the Ubuntu filesystem with the kernel immediately under it, in that directory.  Same for the initrd.  You would also of course, need the exact name of the kernel and initrd files.  Is that actually the case?  

THis method was often used with Grub Legacy when people didn't have a CD/DVD drive functioning to boot a system and even use it to install, loop mount an iso file and then copy it to the root of another Linux filesystem and boot it.  Works with Grub2 also.  Is this a 32 bit Android system?

---

