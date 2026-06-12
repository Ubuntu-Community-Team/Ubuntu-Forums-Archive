---
title: "Complete Full Disk Encryption with Lubuntu 22.04?"
date: 2022-07-01
forum: Security
---

### Post by lisa23 on 2022-07-01
I'd like to install Lubuntu 22.04 with bootloader etc. encrypted as  far as possible, with working suspend-to-disk, to an old netbook's SSD;  no EFI, no other OS.
 I found this guide for Ubuntu, but I also read that the Lubuntu-installer would handle FDE completely different, is that true? [URL="https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019"]https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019
[/URL]
How should the disk be partitioned on a system without EFI? 
Would it be reasonable not to use LVM and just have a swap file on the  encrypted partition? 
Is it still necessary to use LUKS1 instead of LUKS2 to install GRUB2  like the guide says, or is LUKS1 preferable on devices with low RAM  anyway? 
Is the recommendation to use a keyfile as safe as having to enter the  password twice?

---

### Post by guiverc on 2022-07-01
This was also asked at [https://askubuntu.com/questions/1416801/best-way-to-complete-full-disk-encryption-with-lubuntu-22-04](https://askubuntu.com/questions/1416801/best-way-to-complete-full-disk-encryption-with-lubuntu-22-04)

As I said on your question there

                                               > I too recommend using the default installer's method; as what you describe you're after (*excluding suspend to disk; only suspend to ram is QA tested for routinely*) is on the [QA testing checklist of Lubuntu]("https://phab.lubuntu.me/w/release-team/testing-checklist/")  with a number of BIOS tests you'll note (how pre-uEFI is referred in  testing).  The default install does not provide a large enough *swapfile* to allow suspend to disk.. so that would need to be increased; or swap partition setup manually (*which is tested for too, but not with encryption*).  Lubuntu uses full-disk encryption                                 – [guiverc]("https://askubuntu.com/users/469152/guiverc")                 
                 [35 mins ago]("https://askubuntu.com/questions/1416801/best-way-to-complete-full-disk-encryption-with-lubuntu-22-04#comment2464261_1416801")                                           

Have you installed Lubuntu with encryption?   Did you boot a *live* disk on the system after that and look at what's there? 

Lubuntu has used *full disk encryption* for awhile now ! and that's QA-tested on BIOS, uEFI & Secure-uEFI boxes using the same method since moving to LXQt with Lubuntu 18.10. 

The only difference with non-uEFI is there is no ESP partition created by the installer; that partition is **not** encrypted as the standard doesn't allow it to be encrypted (*that would work against the intention of uEFI*) so it does what you want already by default in my opinion. Lubuntu has a newer installer script than Ubuntu's `ubiquity` script the wiki page you're referring to assumes.

---

### Post by lisa23 on 2022-07-02
> **guiverc said:**
> Have you installed Lubuntu with encryption?

I have been using Lubuntu with FDE on that machine for about seven years in a multi-boot environment. I think I originally just used the installer, without changes to the encryption setup over the years (boot partition is unencrypted, no LVM). It's a 32bit install now stuck to 18.04, but the CPU is 64bit and I want to get a fresh 22.04 system, without multi-boot - but I'd like to get suspend-to-disk working and have the boot-loader second stage file-system encrypted.

I didn't try just installing anything yet as I wanted to figure out the way-to-go beforehand as I know that things can get very complicated when not doing them right from the beginning, like when I once tried to do an in-place-conversion of the 32bit install to 64bit ...

> Lubuntu has a newer installer script than Ubuntu's `ubiquity` script the wiki page you're referring to assumes.
So what has changed and to what extend is the guide still applicable?

---

### Post by guiverc on 2022-07-02
Lubuntu releases up to (and including) 18.04 used the `ubiquity` installer same as Ubuntu Desktop did.  The desktop used by Lubuntu in those releases was LXDE (ie. *deprecated *GTK2)

Lubuntu from 18.10 and later uses LXQt, which is why upgrades from 18.04 are *unsupported*. LXQt is Qt5 based, which means a new installer was required, so 18.10 and later use `calamares` (`ubiquity` only has a single Qt5 skin which is hardcoded to say Kubuntu; thus a different installer was sort of mandatory).  This resulted in newer scripts being used for Lubuntu than other *flavors* of Ubuntu, or Ubuntu Desktop itself. Yes Ubuntu Desktop hoped to no longer be using `ubiquity` (but using the current *canary* installer, but it's not yet ready for prime time..). Also Ubuntu Studio moved off Xfce & now use KDE, thus they also use`calamares` for the same reasons Lubuntu switched (*using the same install scripts*).

Lubuntu is a somewhat different system to what it was prior to 18.04, but then again it's also rather similar. LXDE is *deprecated*, with LXDE *developers *joining with Razor-Qt creating the replacement desktop LXQt that Lubuntu started using with Lubuntu 18.10; LXQt is still WM *agnostic* (just as LXDE was) with Lubuntu still using `openbox`.... 

With encryption I can't speak with authority sorry; most of what Tj (*who you'll note is a frequent editor of that page*) & Teward told me *sailed right over my head*, so I had to settle with learning only what to look for in QA to ensure full disk encryption was working correctly.

The guide as I understand it is perfectly applicable, however it assumes the different installer, and older scripts than Lubuntu/Ubuntu-Studio use. The result of a Lubuntu install (*with full disk encryption selected*) should achieve what that guide will produce (*as I understand it*).

---

### Post by lisa23 on 2022-07-04
Thank you very much for your detailed answer. I have used the installer and have Lubuntu 22.04 running fully encrypted now. 
I wanted to have unallocated space on the SSD for over-provisioning, so I couldn't use the basic install option which uses the whole disk. The manual partitioning options were confusing as I didn't know which partitions I would need and how to then get FDE. 
Eventually from the way the GUI displayed the disk I assumed that it maybe needs only one partition; which is indeed the case - there is no boot partition at all. I used Gparted or the KDE disk utility to make a mbr partition table with one partition on 85% of the disk space. There was a warning from the installer which recommended a GPT partition table on all systems, but I also wanted to use a special function of my netbook that speeds up the BIOS POST-process when there is a small 16 Mib partition available and I suspected that this wouldn't work with a GPT partition table, so I stayed with mbr. The installer then offered the option to install to the single large partition with system encryption, and it works very well now, except for hibernation.

Edit: I increased the swap file size (larger than RAM), changed the grub-config and hibernation works now, but only using the  command "sudo systemctl hibernate". 
How can I make the LXQt panel GUI  option work? The button is there but doesn't do anything.

(* just for  reference, I followed the section "Updating grub" from this guide:  [https://confluence.jaytaala.com/display/TKB/Use+a+swap+file+and+enable+hibernation+on+Arch+Linux+-+including+on+a+LUKS+root+partition](https://confluence.jaytaala.com/display/TKB/Use+a+swap+file+and+enable+hibernation+on+Arch+Linux+-+including+on+a+LUKS+root+partition)  
and this guide to increase the swap file size: [https://bogdancornianu.com/change-swap-size-in-ubuntu/](https://bogdancornianu.com/change-swap-size-in-ubuntu/) 
)

---

### Post by lisa23 on 2022-07-05
I'm finished with the system setup so far. I've got the hibernate panel option to work, by creating this file:
/etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla  > [Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

[Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate;org.freedesktop.login1.handle-hibernate-key;org.freedesktop.login1;org.freedesktop.login1.hibernate-multiple-sessions;org.freedesktop.login1.hibernate-ignore-inhibit
ResultActive=yes

reference:
[https://ubuntuhandbook.org/index.php/2021/08/enable-hibernate-ubuntu-21-10/](https://ubuntuhandbook.org/index.php/2021/08/enable-hibernate-ubuntu-21-10/)

---

### Post by guiverc on 2022-07-05
Well done for solving it & getting it working.

Thank you also for sharing what worked for you.

---

