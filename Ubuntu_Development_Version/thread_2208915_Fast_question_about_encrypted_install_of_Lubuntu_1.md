---
title: "Fast question about encrypted install of Lubuntu 14.04"
date: 2014-03-03
forum: Ubuntu Development Version
---

### Post by wjbmd48 on 2014-03-03
Hi:  I installed Trusty Tahr from the daily build, and have been updating it regularly. I love it, but I have a quesiton about the encrytped install I did from a live-USB.    On initial setup, it told me that the swap was corrupted (I have multiple systems, told me this with each install), and so to terminal "sudo swapoff -a" after which the install went normally.    So the question is, am I fully encrypted?  When I enter sudo dmsetup status, I get a return of:        

sda5_crypt: 0 125419520 crypt 
   lubuntu--vg-root: 0 122265600 linear 
   lubuntu--vg-swap_1: 0 3121152 linear       

And when I click in LUKS on "Partition 5 -- 64 GB LUKS" it tells me that it has LUKS encryption, but when i click, presumably, on the boot sector to the left of that, "Filesystem Partition 1 255 MB Ext 2" it tells me it's /dev/sda1, but nothing about it being encrypted. 

     Thanks!

---

### Post by Herman on 2014-03-03
LUKS file system encryption is a good way to prevent any person who gets physical control of your operating system from gaining access to your personal files without your password.

Your first partition, /dev/sda1, 255 MB, ext2 will be your /boot partition. The /boot partition contains the boot loader files and the linux kernels and initial ramdisks, (initrd.img files).  None of those files is very interesting to any potential intruder. The /boot partiiton will not be encrypted. When the system boots, the boot loader loads the kernel in RAM and then the kernel looks to the initial ramdisk which is unique to your own computer and is used to decrypt the / (or 'root') file system and allows the kernel to find /sbin/init which it needs to continue booting normally.

I once tried an experiment and I deleted the initrd.img files and replaced them with equivalent copies from another system for teh same kernel number and sure enough, the operating sysetm was unbootable. To fix it I had to chroot into it and run sudo mkinitramfs to generate a new initrd.img unique to my system. After that it was fixed again. So that's why we need a separate /boot when we have a fully encrypted Ubuntu installation.

GRUB2 has support for LVM, and I have recently been experimenting with LVM (without the LUKS encryption this time). Despite all the LVM installation how-tos and tutorials out-dated advice, we do not need a separate /boot if we just have an LVM installation, since GRUB has a module called lvm.mod and GRUB can deal with LVM seamlessly now. The use of LVM is no longer a reason for needing a separate /boot, although having a separate /boot probably doesn't do any harm.

I have no idea of the difficulties that could be involved for GRUB programmers trying to get GRUB to support LUKS. If it is possible then we could have a fully encrypted disk and we wouldn't need a separate /boot partition anymore and we could just use a normal initrd.img. Probably it in impossible or at least extremely challenging or they would have done it by now. Or maybe they just have more improtant things to do first.

At some point during boot-up you should be prompted for your encryption  password and if that's so then I would sasy you can be quite confident  you have a fully LUKS encrypted installation. Very often, (for me  least), the screen stays black and I can't see the encryption prompt,  but after waiting long enough to expect it to be there I just type my  encryption password to the black screen and press enter and the system  still boots okay.

You could also try mounting your encrypted file system from another Ubuntu installation or from a Live CD. The other Ubuntu installation should prompt you for your encryption password. Another way to decrypt your encrypted file system from a Live CD or another Ubuntu installation is to use the GUI program called 'Disks'.

Another GUI program you might find useful is called 'Logical Volume Management', or system-config-lvm. You should be able to see a graphical representation of your file systems in LVM using that and you should be able to 'see' your swap area inside the LVM.

The Ubuntu Live CD goes for any swap area it can find in the computer and tries to use it. The use of the swap area improves performance of the Live CD and makes installation much faster, especially in some computers. Maybe you have another Gnu/Linux installation somewhere and it was left in hibernation mode? (So the swap area couldn't be used?) I'm just trying to guess. Anyway, it could be a good thing, because an annoying habit of the Live CD is to reformat all the other swap, which means we need to go and edit /etc/fstab with new UUID numbers in other Gnu/Linux installtions when we install a new Ubuntu installtion. If this could be the case in your instance then maybe the installer saved you a little work by complaiing and getting you to do sudo swapoff -a this time. Check your /etc/fstab in your other installations anyway and make sure they are up to date with the UUIDs for /swap.

---

### Post by wjbmd48 on 2014-03-03
Herman:

I cannot thank you enough for taking the time to explain all that. I  can't say I understood every word--I'm a Linux newbie--but it was pretty  reassuring.

More info, if it helps:

1) Yes, I do get the prompt for the encryption code on bootup, won't boot without it.

2) When I mount the system with a USB harness on another Linux system,  it also asks me for the encryption code; only after entering it can I  see the disk contents.

3) When I mount it on a Windows system, the disk doesn't appear in explorer/my computer.

4) BUT, when I mount it in disk management, I can see two partitions,  one 243M "Healthy (Active)," presumably the boot sector, and a second  "29.24 GB Healthy (Unknown Partition)," which is the size of the SSD,  more or less. But of course you can't open the disk from that utility.

I shall install LVM manager and see what I can see.

Does any of that provide any additional information?  

We travel a lot, so system theft is an issue, even with the best attention to physical security.

Thanks,

Bill

---

### Post by Herman on 2014-03-04
1) 2) & 3): It sounds like your operating system partition is encrypted alright, that's good.

4) You can't open it and browse the file system, but there's a handy feature in Disk Manager for unlocking the LUKS encryption. It will prompt you for your password. I just had a look and in my newest installation it looks like some of the buttons have been removed from Disk Manager, and it's just called 'Disks' now. I'm sure it had a file system check option and a few other things, but those buttons seem to have vanished. Maybe they're working on it.

5) Logical Volume Manager is a GUI toolkit for looking at your LVM setup, and it can do just about everything a person would normally use the command line for when looking at and working with LVM. You probably won't need it if you only want to use your laptop. In a computer with more than one hard disk it can be useful and fun. You can expand your operating system over more than one hard disk, for example. It doesn't actually provide as much information or functionality as using the  commands can, but it can do most things and it's quite user freindly once a person gets to know their  way around in it.

6) It's a great idea to use a fully LUKS encrypted operating system, especially for laptops, and even more especially for people who travel a lot. Providing you have a reasonably good password, your data and your identity will be perfectly safe.

---

### Post by wjbmd48 on 2014-03-04
Herman:

You are very kind to take the time to answer my questions.

Thanks so much!

Bill

---

