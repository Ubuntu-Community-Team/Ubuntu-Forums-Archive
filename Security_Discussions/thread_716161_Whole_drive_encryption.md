---
title: "Whole drive encryption"
date: 2008-03-05
forum: Security Discussions
---

### Post by arbulus on 2008-03-05
I recently purchased a Dell Inspiron 1501 laptop for work.  It came with Windows Vista pre-loaded, but I've shrunk that partition down to 30GB and have installed Ubuntu on the remaining free space and use it as my main OS on the laptop.  But I'm curious about whole-drive encryption:  Vista has a utility built in called BitLocker that can encrypt the entire HDD and create a USB key which, when inserted at boot time, will allow the computer to boot (without which the machine cannot boot).  My question is: can this still work when you have multiple OSes installed, such as my dual boot case, since Grub is the main bootloader and not Window's bootloader?  Or is there a Linux utility that can do the same thing and work with multi-boot systems (a solution that I would prefer)? Does anyone else have any experience with whole-drive encryption with a multi-boot system?

---

### Post by mrsteveman1 on 2008-03-05
Bitlocker i BELIEVE works with dual boot systems, I remember testing it before vista came out, as far as i remember the only encrypted part of the drive with bitlocker is the windows partition itself. Bitlocker has its own problems though, for one if you ever lose the key you are screwed. 

I do know that Truecrypt 5 can encrypt the windows partition and work perfectly fine with grub etc. With TC5 its the password that unlocks the system, not a separate key, nothing to lose etc. You also have a small recovery CD with which you can boot the system or even decrypt it entirely if something goes wrong. I would look into TC5 though if i were you, I've been using it for a while and it works fine on its own and with triple boot (hardy and gutsy separate).

If you need to encrypt Linux as well, you can use the ubuntu alternate CD and it will allow you to setup encrypted root similar to bitlocker and TC5.

---

### Post by arbulus on 2008-03-05
> **mrsteveman1 said:**
> Bitlocker i BELIEVE works with dual boot systems, I remember testing it before vista came out, as far as i remember the only encrypted part of the drive with bitlocker is the windows partition itself. Bitlocker has its own problems though, for one if you ever lose the key you are screwed. 

I do know that Truecrypt 5 can encrypt the windows partition and work perfectly fine with grub etc. With TC5 its the password that unlocks the system, not a separate key, nothing to lose etc. You also have a small recovery CD with which you can boot the system or even decrypt it entirely if something goes wrong. I would look into TC5 though if i were you, I've been using it for a while and it works fine on its own and with triple boot (hardy and gutsy separate).

If you need to encrypt Linux as well, you can use the ubuntu alternate CD and it will allow you to setup encrypted root similar to bitlocker and TC5.



Ok, so I would need a separate encryption solution for each partition as neither Bitlocker nor TC5 can encrypt both partitions at the same time?

---

### Post by mrsteveman1 on 2008-03-05
Correct.

Linux can coexist on the same drive with an encrypted Windows partition with both Bitlocker and TC5, but neither one can be used to encrypt the Linux partition itself, because Linux won't be able to load etc.

The only way to encrypt Linux itself is to do it separately with LUKS, which can be done by the Ubuntu alternate CD.

If you do use Bitlocker or TC5 to encrypt the Windows partition, you won't be able to read it from Linux, even though there is a Linux version of TC5, it doesn't work yet.

You can in fact read an encrypted Linux partition from Windows if you need to with FreeOTFE and a suitable EXT3 driver for windows.

---

### Post by arbulus on 2008-03-05
> **mrsteveman1 said:**
> Correct.

Linux can coexist on the same drive with an encrypted Windows partition with both Bitlocker and TC5, but neither one can be used to encrypt the Linux partition itself, because Linux won't be able to load etc.

The only way to encrypt Linux itself is to do it separately with LUKS, which can be done by the Ubuntu alternate CD.

If you do use Bitlocker or TC5 to encrypt the Windows partition, you won't be able to read it from Linux, even though there is a Linux version of TC5, it doesn't work yet.

You can in fact read an encrypted Linux partition from Windows if you need to with FreeOTFE and a suitable EXT3 driver for windows.


Got it.
Thanks a ton for your help!

---

### Post by HermanAB on 2008-03-06
Actually, the best way is to buy a drive with hardware encryption built in.

---

### Post by Biochem on 2008-03-06
mrsteveman1 ,
How did you make TC5 work with a dual boot?

 When I tried in in a Virtualbox it would stop working the second I said I was not using windows boot loader (ie. grub).

 Beside, it was also taking 20 min to boot windows, which was about tne amount of time it took to encrypt the whole drive. Was that a VM artifacte?

---

### Post by mrsteveman1 on 2008-03-06
Thats definitely a VM problem. On this laptop, which is fairly fast with a new SATA disk, the 60gb Windows partition took around an hour to encrypt. The cool thing is you can stop it and even reboot the machine with it half encrypted, and the system still works fine. Then you can continue it later on etc.

Heres what i have setup:

sda1 is Vista SP1 encrypted with TC5

sda2 is Hardy 

sda3 is Gutsy

sda4 is linux swap

All 3 OS have their respective bootloaders installed into their own partitions, IE grub is installed on both ubuntu parts and each one is only used to boot itself.

The reason it works is this, ONLY the vista partition is encrypted, and the TC5 bootloader sits outside all of these partitions, before the vista partition itself. Because the TC5 bootloader understands how to chainboot partitions, all I have to do when it boots is press escape and choose one of the linux partitions. Otherwise i have to type the TC password, which then boots windows. Booting windows like this takes around 20 seconds longer than it would otherwise.

The error you saw has to do with the following situations, TC5 can't be used to encrypt the entire drive (IE all partitions) if another OS is on the drive, because the other OS won't be operable once it starts. The second thing you can't do is allow grub to install into the MBR, because TC5 needs to have control over the boot process. Other than that, it all works fine.

There is a series of questions when you are encrypting the windows drive, but all of them are only intended to prevent users from messing something up. If you encrypt ONLY the windows partition, and tell the installer that you have another OS installed, but not a 3rd party MBR, it will work fine.

---

### Post by wieman01 on 2008-03-06
There is perhaps another option that I have been discussing with other users here:

[http://ubuntuforums.org/showthread.php?t=715741]("http://ubuntuforums.org/showthread.php?t=715741")

Wubi on an encrypted Windows partition basically... Not sure if it works, the OP had no success but this might be specific to his hardware. Personally I have never tried Wubi, so I don't really know how it works & where is installs GRUB.

---

### Post by ggavalas on 2008-04-24
I know I'm a little late to the party, but I have the following setup to allow for encryption with dual boot and both Vista and Hardy encrypted

sda1: Windows Vista encrypted with TC5
sda2: Ubuntu Hardy Heron /boot partition (not encrypted)
sda3: Ubuntu Hardy Heron encrypted volume with LVM inside and / and swap partions within LVM (to save partitions used overall incase it gets over 5 partitions)
sda4: Working on installing OSX Leopard on this partition currently.

The steps I used are as follows, in brief:
1) Installed Vista first (actually pre-installed on laptop)

2) Installed Ubuntu second using encrypted physical volume with LVM inside it and 2 partions / and swap inside the LVM(at this point, grub was in the MBR)

3) Ran full windows system encryption (not full disk encryption) through TC5 and let it write its bootloader to the MBR. (obviously overwriting Grub in the MBR)

4) Booted with a live cd and copied the truecrypt bootloader from the MBR to a file in the /boot partition (sda2) 
use these commands to do so:
dd if=/dev/sda of=/mnt/boot/truecrypt.mbr count=1 bs=512
dd if=/dev/sda of=/mnt/boot/truecrypt.backup count=8 bs=32256

5)Reinstalled grub to the MBR using these commands:
sudo grub
install (hd0,1)/grub/stage1 (hd0) (hd0,1)/grub/stage2 0x8000 p

6) Added a chainloader to the menu.lst Vista entry to point to the truecrypt bootloader within the /boot partition like so:

title Windows Vista/Longhorn
rootnoverify (hd0,0)
makeactive
chainloader (hd0,1)/truecrypt.mbr
boot

The only partition not encrypted in the /boot partition so far, which is fine.  After grub loads, no matter which OS I choose, I enter a passphrase and that OS starts.  

For more detailed instructions which I pulled from but which are for XP instead of Vista, use this link:

[http://ubuntuforums.org/showthread.php?t=761530](http://ubuntuforums.org/showthread.php?t=761530)

---

### Post by mikko.ohtamaa on 2008-07-14
> **ggavalas said:**
> I know I'm a little late to the party, but I have the following setup to allow for encryption with dual boot and both Vista and Hardy encrypted
dd if=/dev/sda of=/mnt/boot/truecrypt.mbr count=1 bs=512
dd if=/dev/sda of=/mnt/boot/truecrypt.backup count=8 bs=32256


Thank you very much! This did the trick for me and made my setup perfect. I wrote a blog how to make encrypted home coexisting with Truecrypted Windows partition.

[http://blog.redinnovation.com/2008/07/15/perfect-dual-boot-crypted-hard-disk-setup-with-truecrypt-and-luks/](http://blog.redinnovation.com/2008/07/15/perfect-dual-boot-crypted-hard-disk-setup-with-truecrypt-and-luks/)

---

