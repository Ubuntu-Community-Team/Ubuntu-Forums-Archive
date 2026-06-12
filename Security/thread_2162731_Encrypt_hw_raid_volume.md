---
title: "Encrypt h/w raid volume"
date: 2013-07-15
forum: Security
---

### Post by Durkslag on 2013-07-15
*I have looked around and searched but haven't found a good solution that works for me and my hardware raid.*

I have a server running Ubuntu Server 12.04 on a standalone, unencrypted drive.

I also have a h/w raid that I mount in /media/ every time the computer starts (in /etc/fstab). Got some backups, Dropbox, documents, media, etc in this "folder".
I'd like the whole mount to get encrypted so the data can only get accessed if I type a password in the terminal.

This is what I need:
I already have files on it so I can't format.
Every time the computer starts I can login with SSH, enter a command followed by a password to decrypt the drive and access the files.
If the computer restarts it gets encrypted and I have to enter my password again.

I've looked at eCryptfs but don't know if that's what I'm looking for.

tl;dr
An encryption that makes my h/w raid inaccessible if someone connects with a USB flash drive os similar.
Only decrypts the mount if I enter a command and password through SSH.

Thanks in advance!

---

