---
title: "Enctrypt my all data/hard drive"
date: 2023-02-22
forum: Security
---

### Post by netw844f on 2023-02-22
Hello folks,

I intend encrypt my external backup. I want prevent anyone access the data through sata ou usb connection and on this way see and steal my data.

Which and what should I do to encrypt my all data (hard drive) and what kind problem can I get in the future?

I prefer do all stuff through cli (command line interface).

Thank you in the advance

---

### Post by TheFu on 2023-02-22
Use **cryptsetup** with the defaults.  The manpage for that command is pretty good and there are lots of examples for using it on the internet.   That's LUKS-based encryption, which is what whole drive encryption on Ubuntu uses too. Some file managers will understand LUKS encryption and will prompt you to unlock the LUKS encryption, then mount the storage. Some how-to videos and a text guide:

[LIST]
[*]Creating Part1: [Https://youtu.be/vk9Z2_rEUak](Https://youtu.be/vk9Z2_rEUak) (nerds should find this very funny)
[*]Accessing Part2: [Https://youtu.be/ELEVo6SbYl0](Https://youtu.be/ELEVo6SbYl0) seems to be it.
[*]Text version: [Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it](Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it)
[/LIST]


You probably want to setup a FIDO2 key to provide access.  Or you could put some decryption keys onto an external USB flash drive (or 3!) to ensure the access is never lost.

There are all sorts of problems that can happen with encrypted storage. Data corruption on an encrypted disk generatlly cannot be recovered or even accessed.  Forget about using testdisk or photorec to get specific files back when stored inside encrypted containers.

Encryption isn't some magic solution, but it will keep data at rest locked. When unlocked, the data is just as open and at risk as any non-encrypted storage.  Since backups need to be off-line most of the time, you'll need to unlock the storage, then mount it, before use.  Every 5-10 yrs, you'll need to wipe it and start fresh to get the newest encrypted storage driver updates.  All software, including encrypted storage drivers are moving forward with incremental fixes and improvements.

There is another option than using LUKS or any encrypted storage. You could use a backup tool that encrypts the backup files. Duplicity can do this. Same for Duplicati or Deja-Dup.  I don't use any of those backup tools, but lots of people do.

---

