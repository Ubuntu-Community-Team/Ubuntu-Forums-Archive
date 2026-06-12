---
title: "Howto enable networking more early in boot process and include sshd in initrd?"
date: 2007-04-30
forum: Server Platforms
---

### Post by fadenb on 2007-04-30
Hi.

I am currently running several computers with encrypted / filesystem as described in [https://help.ubuntu.com/community/EncryptedFilesystemHowtoEdgy?highlight=%28encrypt%29](https://help.ubuntu.com/community/EncryptedFilesystemHowtoEdgy?highlight=%28encrypt%29)

Currently I start the computer, wait a moment, enter my password an the boot process goes on.
1. mounting / filesystem
2. keymap etc.
3. networking

I want to move the networking options further up before the filesystem is mounted and include an sshd to enter the luks passphrase remotely.

Can anyone tell me howto enable networking before filesystems and include files like the sshd into the initial ramdisk?
Would be nice if this could be automated with some initramfs scripts so i do not have to do it everytime i update my kernel.

THX

---

### Post by fadenb on 2007-05-01
*push*

---

