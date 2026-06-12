---
title: "Retro Encrypting Ubuntu Live Persistent USB Casper Partition"
date: 2020-02-10
forum: Security
---

### Post by mattzab on 2020-02-10
[COLOR=#242729][FONT=Arial]I've created a persistent live system on a 128 GB USB Drive. This has all of my useful tools onboard, and I'm also logged into all my accounts in Chrome Browser, and have my Google Drive mounting through rclone.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Needless to say, there's a good bit of sensitive stuff on this drive. I would like to encrypt it, should I lose it.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I recognize that this part of the request might be controversial, but I've thought it through: I'm okay with very basic encryption. I'm not trying to hide from intelligence agencies of any kind. I'm just trying to prevent the guy that finds my lost drive from logging into all my stuff when he realizes this is a bootable drive. If a simple encryption method will work, I'm okay with that. I'm looking for the simplest possible solution.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I've tried putting a password on the account, but they don't seem to stick. I can log in without a password, just leaving the field blank and hitting enter. I've used the GUI password changer and passwd as well. No joy. This doesn't prevent anyone from finding my stored files though, if they browse through the drive itself.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]All of the guides I'm finding online seem to be outdated or inapplicable. I wasn't able to "Just Select LUKS Encryption During The GUI Installation Process" because I'm running a live, persistent drive. (I'm also using a casper partition, rather than a casper file)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]How can I add encryption, and keep this thing bootable and persistent? Trying various tutorials with cryptsetup has yielded an unbootable device.[/FONT][/COLOR]

---

### Post by C.S.Cameron on 2020-02-12
If you want full disk encryption you will need to do a Full install.
Unplug any other internal or external drives.
Plug in the blank target USB and boot the Live installer USB.
Select the options for encryption while installing.
Rebuild your home folder when complete.

**Encrypted Folder See:**  [https://askubuntu.com/questions/1119534/how-to-encrypt-usb-pendrive-thumdrive-that-can-be-accessed-from-windows-also/1121695#1121695](https://askubuntu.com/questions/1119534/how-to-encrypt-usb-pendrive-thumdrive-that-can-be-accessed-from-windows-also/1121695#1121695)

**BIOS/UEFI Flash Drive with Full Disk Encryption see:**  [https://askubuntu.com/questions/1086309/how-to-make-bios-uefi-flash-drive-with-full-disk-encryption/1086314#1086314](https://askubuntu.com/questions/1086309/how-to-make-bios-uefi-flash-drive-with-full-disk-encryption/1086314#1086314)

---

### Post by sudodus on 2020-02-12
I agree with C.S.Cameron,

There is no good way to encrypt a persistent live drive. You had better create an installed system using LVM with LUKS encryption (when installing to the USB pendrive) like it were into an internal drive.

Edit: It is possible to create a second user with a password. Give this user sudo permissions and after that remove the original user. But the files will not be encrypted, and will be easily available, if an intruder logs in live (without persistence).

---

