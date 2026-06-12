---
title: "Can a LUKS partition be hacked, ie. password retreived ?"
date: 2008-09-18
forum: Security
---

### Post by ekh on 2008-09-18
I'm back again after several installs and and much security reading. Please excuse me for being in paranoid mode, in addition to being attacked for a month, I had an experience this morning I would like to tell you.

Pre-history:

```

Installed yesterday Ubuntu desktop 8.4.1 from alternate disk with LUKS on a lenovo T41, 
without internet connected
Made the hardening instructions from this:

www.cromwell-intl.com/security/linux-hardening.html

except not changing /temp to a RAM fs.
Edited /etc/apt/sources.list for removing comments added by the installer.

Connected internet.
apt-get update
apt-get upgrade
apt-get dist-upgrade
installed libc6  (needed by Ossec)
installed Noscript 0.7.5.5 and Addblock plus 1.8.1
Disconnected internet.

installed Ossec 1.6

Installed thunderbird 2.0.0.16
copied my thunderbird profile from another computer.
Read my mail for the first time in a week.

Under the work above, the internet was only plugged in while communicating.

Rebooted with 7.10 Ubuntu Live CD
umount harddisk root.

Inserted an identical harddisk via USB to make a verbatim copy of the harddisk.

$ dd if=/dev/sda of=/dev/sdb bs=32768

After the copy finished I booted the 7.10 Ubuntu Live CD on a system without harddisk.

I plugged in the harddisk copy via USB

$ grub
> find /grub/stage1
> root (hd0,0)
> setup (hd0)
> quit


```

The original harddisk was now swapped with my copy and booted. Stored the original harddisk.
I booted and connected to the internet and fetched mail once more, disconnected internet and read the mail.
turned off the computer.

The T41 has not been on the net since this point.

This morning I then booted the computer, and it made a fsck and informed me an error on the boot sector was corrected. When the boot was done the computer was frozen. 

I turned it off and then rebooted. This time the behavior seemed normal. Ossec has nothing to report.
After maybe 10 minutes it froze again. I then turned off and removed the extra 1GByte RAM, as I have never seen this Lenovo T41 freezing with the original RAM only. Writing this, the T41 has been alive for more than 2 hours without a freeze.

My questions are: 

1. Have I installed in an unsafe way ?
2. Can a LUKS partition be hacked by an attacker by replacing fsck and setting the counter, so fsck is run at next boot ?
3. Can the replaced fsck replace the initial code run for LUKS password entry, store the password on the boot partition or some other free area of the disk for later retrieval, and do a complete cleanup ?
4. If point 3 is possible, can it be prevented, and how ?


Finally I will mention this special live CD edition of Kubuntu a friend directed me to, it has been a great help for me.

[www.polippix.org](www.polippix.org)

It is presently the only system I can use to log in at [www.ebay.de](www.ebay.de), other systems ( OpenBSD and Ubuntu) repeatedly gives a fresh login screen after user and password entry.

This post is sent from the Polippix.

[Edit] Corrected wrong grub command in post, correctly done during work.

---

### Post by hyper_ch on 2008-09-18
> **ekh said:**
> 1. Have I installed in an unsafe way ?
If have no real clue what you did... what about that hardening and swapping disks....

> **ekh said:**
> 2. Can a LUKS partition be hacked by an attacker by replacing fsck and setting the counter, so fsck is run at next boot ?
This has not much to do with LUKS

> **ekh said:**
> 3. Can the replaced fsck replace the initial code run for LUKS password entry, store the password on the boot partition or some other free area of the disk for later retrieval, and do a complete cleanup ?
if it's a modified fsck then I'm sure it could do that.

> **ekh said:**
> 4. If point 3 is possible, can it be prevented, and how ?
Create a bootable cd-rom that will have an initramfs that you trust on there... then it will (1) load the initramfs which has also the crypto parts in it (2) use the cryptoparts to unlock the actual partitions (3) make the real boot from the actual partitions.

---

### Post by ekh on 2008-09-18
Thank you for the answer.

> **hyper_ch said:**
> If have no real clue what you did... what about that hardening and swapping disks....

For the hardening part, I followed the recommendations in the link applicable for linux. A few sysctl was not defined for Ubuntu, and I did not do the RAM fs suggestion for /tmp.

Disk swapping. I just did a verbatim copy of my harddisk and then used the copy instead of the original, so I have a backup in the original disk. 

> **hyper_ch said:**
> 
if it's a modified fsck then I'm sure it could do that.


That implies, that the encrypted data is not safe even when the computer is turned off, if it has been infected previously. I'm here thinking of someone getting hold of the computer in a powered off state.

This then also applies to a system never connected to the net. If an infected file for this purpose is executed, then the LUKS password is available after next boot. 

> **hyper_ch said:**
> 
Create a bootable cd-rom that will have an initramfs that you trust on there... then it will (1) load the initramfs which has also the crypto parts in it (2) use the cryptoparts to unlock the actual partitions (3) make the real boot from the actual partitions.


This sounds like a safe suggestion. Unfortunately it is a solution that adds to boot time.

After years of no significant internet issues, it is overwhelming how much material there must be read, before just thinking of cathing up with the attackers.

I wonder if it could be worth the effort to have the Ubuntu live CD have an option that could verify all Ubuntu binary files on the PC. 

To be sure you don't lose the anonymity of the data on a PC without power, what about this.

If the start-up procedure was made so that after entry of the password minus the last 5 characters, a checksum of the boot partition could appear on the screen. The checksum is generated as a function of the first part of the password.

If that checksum is OK then the last 5 keystrokes (or more) could be entered to initiate the boot. If failing to enter the remaining password correctly, as an option it could after n failed attempts block the disk for further access.
Doing regular backups this is better than the data falling in the wrong hands.

If the checksum is not OK, then we know it has been tampered, and thus stop giving the full password. In this way I think we can be quite sure the data is safe when the computer is turned off. Any objections ?

What we can trust while the computer is turned on by the owner is another matter...

Do anyone have an explanation on the Ebay login mystery ?

---

### Post by hyper_ch on 2008-09-18
it doesn't add much boottime... initramfs is just a small kernel that prepares to load the actual one...

---

