---
title: "Will antivirus hurt Windows?"
date: 2013-01-05
forum: Security
---

### Post by calebp on 2013-01-05
I just recently installed Ubuntu 12.10 with wubi on my Windows 7 PC. I am planning on sharing files with Windows. I was thinking about installing Avast for Linux to prevent sending viruses to Windows since I use Avast in Windows. Since wubi is within Windows, will installing antivirus in Ubuntu cause conflicts with Windows or my Avast software in Windows?

Also, is there a better antivirus software for Ubuntu. I want one that autoscans rather than making me do it manually.

Thanks so much for your help.

---

### Post by Bucky Ball on 2013-01-05
[I]Thread moved to [B]Security Discussions
[/B][/I]

---

### Post by ajgreeny on 2013-01-05
I don't think there is an antivirus application for Linux that autoscans in the background as almost all of them do in windows, mainly because it is not really needed in Linux.

Windows will not be able to read anything in your ubuntu system as it can not decypher any Linux filesystems, and your wubi filesystem is just an encrypted file as far as windows is concerned., so there is no need to worry on that count.

The only way you can share files is to put all your data files into a shared ntfs partition, which you can mount at boot in Ubuntu by editing the /etc/fstab file.

I do not really know or fully understand wubi installs so can not help with the necessary edit of fstab as I don't know if it differs in wubi from a proper, partitioned dual boot installation's fstab.

---

### Post by Bucky Ball on 2013-01-05
> **ajgreeny said:**
> 
I do not really know or fully understand wubi installs ...

+1. Many of us here don't as few use it. Intended to 'try before you buy', or in this case, install Ubuntu. Not intended as a long-term solution.

---

### Post by calebp on 2013-01-05
I was going to save the files I want to share on the Windows file system or through a USB. Can installing antivirus in Ubuntu cause problems in Windows? I'm not sure if the antivirus would only run once in Ubuntu, or if it could run itself when the computer begins booting.

Thanks for letting me know about the lack of autoscan.

---

### Post by coldcritter64 on 2013-01-05
Agree with Bucky Ball, wubi is best for a tryout.

As I understand wubi (I don't use it, I used full partitioning dual booting and Avast), it is installing Ubuntu to within a hidden file on the Windows NTFS filesystem and dual booting Win and Ubuntu via Grub and a Windows bootloader modification.

When Ubuntu is booted Windows isn't loaded and vice versa. It is actually dual booting from the same filesystem. With Avast also being "On Demand" in Ubuntu, that is no background process/shield is running, I can't see any problems with using it. In my opinion it would be safe to do. I would advise to wait for a regular wubi user to comment or confirm its safe usage though. Cheers :)

---

