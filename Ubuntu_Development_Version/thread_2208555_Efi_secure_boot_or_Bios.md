---
title: "Efi secure boot or Bios"
date: 2014-02-28
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2014-02-28
I know I can install Ubuntu 14.04 with efi secure boot on, or off in bios mode.  What I would like to know which is best.  Afaik there are no issues either way.

So I guess it boils down to which is really more secure, and which will allow Ubuntu to boot faster.  Any opinions on this.

Henry

---

### Post by ventrical on 2014-03-01
> **Hewjr100 said:**
> I know I can install Ubuntu 14.04 with efi secure boot on, or off in bios mode.  What I would like to know which is best.  Afaik there are no issues either way.

So I guess it boils down to which is really more secure, and which will allow Ubuntu to boot faster.  Any opinions on this.

Henry

 I have a brand new B75MA-P45 MSI MoBo with UEFI. I have UEFI/Secure Boot OFF. I can install Windows 8 first , 64bit, then, use the Ubuntu Ubiquity partitioner for resize and install Trusty. No problems so far. After install of Ubuntu all I have to do is use the GRuB rescue disk and it  reinstalls GRuB to workable. I can also just straight install Ubuntu(s) on multiple partitons with no UEFI.

UEFI is needed for 3 Terabyte hdds in Windows. I'm not sure how it works in Ubuntu but my 1.5TB works fine.

---

### Post by Hewjr100 on 2014-03-01
Thanks for your reply.  I used to dual boot both os's but not anymore.  Would prefer to stick with just Ubuntu 14.04 only.  That's why I wondered if secue boot was better than legacy bios.

Henry

---

### Post by grahammechanical on 2014-03-01
Secure boot is not the same as UEFI. We can compare BIOS and UEFI but Secure Boot is something separate.

There are very good reasons why we should use secure boot if we have that available. The first is, that it increases the security of our computer. The second is, that Ubuntu has been able to install with secure boot enabled since Ubuntu 12.10. So, why disable something that Ubuntu can use to protect our machine?

As far as I can tell from reading threads relating to problems users have had is that Ubuntu should be installed in the same mode as Windows was installed. If Windows is installed in UEFI mode then Ubuntu must be installed in UEFI mode.

> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.[FONT=inherit][/FONT]
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[FONT=inherit][/FONT][/FONT]

[*=left]if Ubuntu is the only operating system on your computer, then it does not matter, you can install Ubuntu in EFI mode or not.
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I do not see this a being a 14.04 specific issue unless there have been changes to the Installer/partitioner and other install related stuff that need testing. Which is always a possibility.

Regards.

---

### Post by oldfred on 2014-03-01
The entire secure boot issue is primarily Windows Marketing as it has historically had so many secuity issues with virus. But boot virus are rare even with Windows.

 [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

Supposedly UEFI is faster, but you may want to test.
 Legacy BIOS and  UEFI AMI AptioMar 2012 -  20 MIn
[http://www.youtube.com/watch?v=dRMIvY7BiL4](http://www.youtube.com/watch?v=dRMIvY7BiL4)


If just installing Ubuntu, use gpt partitioning as Ubuntu can boot from gpt with UEFI if you have a efi partition or with bios if you have a bios_grub flagged partition. And you can then reinstall grub-pc(BIOS) or grub-efi(UEFI) to see the differences.

If you use the 30+ years old MBR(msdos) partition scheme you can only boot in BIOS mode. UEFI requires gpt partitioning.

      For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

