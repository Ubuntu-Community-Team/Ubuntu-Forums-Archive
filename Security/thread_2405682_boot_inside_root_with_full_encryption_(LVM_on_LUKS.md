---
title: "/boot inside /root with full encryption (LVM on LUKS) on UEFI PC: grub cmd when booti"
date: 2018-11-09
forum: Security
---

### Post by Tim_Banchi on 2018-11-09
Dear all,

While I successfully deployed LUKS encrypted /boot on MBR systems, I have troubles doing the same with EFI based systems.

I try to fully encrypt my new 18.04 Ubuntu install with /boot inside root directory. I know that I could use keyfiles to unlock root from /boot, but would like the simplicity only having one LUKS->LVM partition. I don't get any error message, but I'm just thrown to the grub console (not grub rescue). 

My (simple) setup:
/dev/sda1 -> EFI
/dev/sda3 -> LUKS->LVM with /boot folder on /root
(dev/sda2 was boot but is deleted)

After a clean install, I do the following from LIVE CD
1) copy content of /boot partition to /boot folder on /
2) change /etc/fstab to not mount /boot + mount /dev/sda1 to /efi
3) chroot into new installation (/efi /proc /dev /sys /dev/pts mounted/bind)
4) add to /etc/default/grub:
GRUB_PRELOAD_MODULES="luks lvm cryptodisk" #don't know if necessary, but to make sure
GRUB_CMDLINE_LINUX="... cryptdevice=UUID=XXXX-XXXXX-XXXX:sdX3_crypt root=/dev/mapper/ubuntu--vg-root ..."
GRUB_ENABLE_CRYPTODISK=y
5) delete /boot/efi (so it's not used any more, as efi is mounted at /efi)
5) generate grub config file
grub-mkconfig -o /boot/grub/grub.cfg #no errors except lvmmeta
6) install grub + prepare initrd 
grub-install --target=x86_64-efi --efi-directory=/efi --bootloader-id=ubuntu --recheck #all fine, no errors
sudo update-initramfs -c -k all #all fine, no errors except lvmmeta

I then reboot, and get thrown into grub command bash .. no warning, no error, nothing.

Before I deleted the "old" /dev/sda2 (/boot) partition, I was booting fine. lsblk showed /dev/sda2 not mounted any more, but I guess it was used by grub to load kernel and initrd during boot process. 

Since I deleted /dev/sda2, grub cannot find /boot any more. Somehow I fail to tell grub where boot (or root) is.

can anyone help me out? I did find ample information on the net, but nowhere I could find the hint what to do.

---

### Post by oldfred on 2018-11-09
I do not use LVM, but see this link:
       Full-system encryption with manual control and dual-booting Paddy Landau
[https://ubuntuforums.org/showthread.php?t=2357627](https://ubuntuforums.org/showthread.php?t=2357627) 
    
And it goes to this:
[https://help.ubuntu.com/community/ManualFullSystemEncryption](https://help.ubuntu.com/community/ManualFullSystemEncryption)

---

### Post by Tim_Banchi on 2018-11-10
Hi olfred,
thanks, I found above links, but both use a separate /boot partition next to LVM with /root and swap.

Here is a description about grub opening LVM on LUKS: [https://bbs.archlinux.org/viewtopic.php?id=188182](https://bbs.archlinux.org/viewtopic.php?id=188182)

I can boot from grub command loading luks, cryptomount, and lvm, (using example of above link). So it seems I have all the ingredients, but not the correct configuration.

What I realize now, I might need to install grub in /efi/EFI/ubuntu/grub/grub.cfg, not in /boot/grub/grub.cfg (as grub needs to open /root to get to /boot). I just tried that with:
sudo grub-mkconfig -o /efi/EFI/ubuntu/grub/grub.cfg
sudo grub-install --target=x86_64-efi --efi-directory=/efi --bootloader=ubuntuluks --boot-directory=/efi/EFI/ubuntu --recheck

however, same result: I get thrown to the grub command, no automatic boot process. I cannot find out how to see the problem of grub (is there a log or error file of grub/efi boot process?)

---

### Post by Tim_Banchi on 2018-11-22
I can (partly) answer my own question.

I realized that /boot inside /root would either need the keyfile integrated in initramfs (which I don't want) or having 2 passwords anyway (as with separate boot). 

So I decided to have a separate boot partition with the grub configuration taken from paddy landau code (thank you so much!).

however, with secure boot enabled, I get a:
```

error: no such device: <long-UUID-string> 
error: no server is specified
error: you need to load the kernel first

``` 

Encrypted boot and secure boot together seem not to work yet, see also [https://ubuntuforums.org/showthread.php?t=2398512](https://ubuntuforums.org/showthread.php?t=2398512) and [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1401532](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1401532)

So currently secure boot off, but with encrypted boot.

I have the problem that after a kernel/initramfs update, the boot breaks. I'm not sure why, because my MBR encrypted /boot partition setups don't break with kernel updates, and I configured the EFI setup exactly the same (except grub configuration directory and grub installation location of course), and I don't use a keyfile for /root in initramfs.

I might as well just use paddy landau's automatic script the next time :)

---

