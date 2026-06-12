---
title: "Auto-Mount Encrypted Container"
date: 2015-09-04
forum: Security
---

### Post by hj7-c on 2015-09-04
Hi,

I'm currently using TrueCrypt but I need an encrypted file system (got to be an ext file system, ext4  preferred) in a file container. The file container can't be on my HDD  but has to be a network device (ftp and samba are possible for sure,  other option might be available). I need a program which makes it  possible to automatically mount the volume without password prompt (the  password can be provided as a parameter of the mounting command or  something).

  Do you know any program which makes this possible? It'd be great if it's possible with TrueCrypt, but I'm open to new software.

Edit: TrueCrypt seems to be a bad idea anyway because I'd have the enter my account password.

---

### Post by TheFu on 2015-09-04
truecrypt project died last year.

Automatic decryption as described for stuff like this kinda defeats the purpose of using encryption, doesn't it?

I suspect any solution would mandate pulling the file local, then mounting the encrypted data.
Another option, if you control the remote system, is to use HOME directory encryption and connect over sshfs. You can use ssh-keys.  Might work, but system-level backups are harder in this situation.

---

