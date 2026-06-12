---
title: "Encrypt Data On Portable USB Pendrive"
date: 2006-08-02
forum: Server Platforms
---

### Post by lynxus on 2006-08-02
Hey guys, ive been seraching hi and low for an answer and have come up lost :(

I have a 128mb penddrive that need to hold my SSH keys and password files (Open office spreadsheets) this needs to be encrypted ,

IE: when i plug the drive in the only way to gain access is to enter the password & possibly a passphrase? not sure exactly how it all works..

Anyway , can anyone here advise. Please note im a slight newbie to this so a easy walkthru would be great.

I think i need to use GPG or summat like that?

Cheers
Graham

---

### Post by soul_rebel on 2006-08-02
No way to get a beautyful password prompt when you plug the usb key. There are different approaches anyway. 
Encrypted loop device: real encryption, done by the kernel. Transparent read and write.

EncFS userspace encryption (uses fuse module), files are stored in a folder encrypted, then mounted to another folder unencrypted (if the password is correct). Transparent read and write. Possibility to keep unencrypted files too.

gpg single file encryption. Just encrypts the file you want, very long password are accepted. You may be able to integrate this with nautilus or konqueror.

I recommend encfs if you use many files for a long time or gpg if you use just one file per time for a short time.

---

