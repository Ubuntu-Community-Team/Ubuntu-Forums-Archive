---
title: "multiple disks - decrypt on boot"
date: 2016-01-11
forum: Security
---

### Post by nicolasdiogo on 2016-01-11
Good Morning,


I would like to request guidance as to how I can go about having a system setup with multiple encrypted disks that can be decrypt at boot.

I suppose it would be a situation where I will enter the password for decrypting / (root).  The Keys for the other the other partitions should be available in the (root) partition to allow decryption.

In this way, it would be possible to decrypt all partitions used by the system with a single password during boot - the one used for decrypting the (root) partition.


With Regards,

Nicolas

---

### Post by CharlesA on 2016-01-13
I'm giving this a bump because I had similar thoughts when I was thinking of doing full disk encryption on my home server. My main through was to have it decrypt based in a key on a USB stick, but I don't know how easy/hard that type of setup would be to well, set up. It sounds like you have the same type of idea in mind, is that the case?

---

### Post by mikodo on 2016-01-13
> **nicolasdiogo said:**
> I would like to request guidance as to how I can go about having a system setup with multiple encrypted disks that can be decrypt at boot.

I think one way is to use [LVM]("https://wiki.archlinux.org/index.php/LVM#LVM") volumes for the disks then, encrypt on **'top' **of the [LVM with LUKS]("https://wiki.archlinux.org/index.php/Dm-crypt/Encrypting_an_entire_system#LUKS_on_LVM").

Addendum: 

If you go this route, don't forget to: [backup the LUKS header]("https://gitlab.com/cryptsetup/cryptsetup/wikis/FrequentlyAskedQuestions#6-backup-and-data-recovery").

---

### Post by HermanAB on 2016-01-14
Google for: "arch linux cryptsetup usb key"

---

### Post by Dáire Fagan on 2016-01-14
I actually came onto the forums because I want to encrypt a complimentary HDD for storage, and I was pleasantly surprised by the coincidence that the last post under specialised support, visible on the main page without searching, was this one :)

In the past on a different computer I did something that may be of some use to you, please see the last two posts: [Window 8.1, Ubuntu 14.04, Debian, GPT UEFI multi-boot with LVM and encryption]("http://ubuntuforums.org/showthread.php?t=2218477")

I am going to revise that post myself and what others have recommended here in your thread and see what I can come up with. Less complicated this time, I am not booting from this complimentary HDD, and there will just be one partition on the LVM - what is important to me like you is that one password allows me login to Ubuntu which runs on my SSD, but also unencrypts the HDD so that the encryption is completely seamless.

[URL="http://ubuntuforums.org/showthread.php?t=2218477"]
[/URL]

---

### Post by Dáire Fagan on 2016-01-16
I have gotten so far but run into difficulty. Although I am after the same result and the OP here does not seem to be responding, I would rather not hijack their thread entirely. Please see if you can help me: [Automounting non-root LUKS LVM on boot?]("http://ubuntuforums.org/showthread.php?t=2310164#post13424239")

---

