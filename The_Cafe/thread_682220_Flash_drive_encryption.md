---
title: "Flash drive encryption"
date: 2008-01-29
forum: The Cafe
---

### Post by cartisdm on 2008-01-29
So I have a flash drive that I carry around with me everywhere but it does occationally have stuff on it that I wouldn't want floating around if I lost it.  I downloaded TrueCrypt and created a 200mb folder that is password protected.  One thing I'm confused is, do I have to have this TrueCrypt software installed wherever I try to mount this encrypted folder? I want to be able to plug my drive in anywhere, simply enter in my password, and access my protected files.  How can I do this? What do you all do to protect your files?

---

### Post by blastus on 2008-01-29
Personally, I would not bother trying to use an encrypted USB drive as a means of transferring files from one computer to another. Use an encrypted USB drive to backup your sensitive data and use an unencrypted for transfer. It's just too much of a hassle. 

In Debian Etch and Ubuntu Gibbon auto-mounting encrypted drives does not work. You have to manually mount and unmount. In Gibbon, I actually have to logout and then log back in again to remount. In Etch I don't have to logout.

[Encrypted partitions with Ubuntu/Debian](http://johnleach.co.uk/words/archives/2006/12/06/245/)

---

### Post by Biochem on 2008-01-29
Not only does truecrypt needs to be installed on the computer but you need to have admin privileged to create partition and change password.

On the other hand, freeotfe.org hava a portable version that doesn't need to be installed. And it is compatible with dm-crypt/LUKS encrypted partition. But as blastus said there are problem with mounting encrypted flash drive in Gutsy

---

### Post by ice60 on 2008-01-29
double posted, i wish i'd never posted in this thread. :|

---

### Post by ice60 on 2008-01-29
[color=blue]EDIT[/color] actually, i don't think it will work on a second computer, i'll leave the post incase it's useful for anyone who needs to use it on just one computer.
> **ice60 said:**
> i think you need truecrypt on all the computers for it to work on a flash drive. you could try GPG, you'd have to test if it decrypts on a second computer - not the one that encrypted it.

instead of my rubbish explainations i found a link lol
[http://www.cyberciti.biz/tips/linux-how-to-encrypt-and-decrypt-files-with-a-password.html](http://www.cyberciti.biz/tips/linux-how-to-encrypt-and-decrypt-files-with-a-password.html)

if you do use GPG, when it encrypts the file it leaves the cleartext original behind, you can securely erase that with either 'wipe' or 'shred'

EDIT. in the comments to the link i gave it mentions about leaving cleartext files behind in tmp directories. i don't know anything about that, so it's probably best not to use this, unless the files aren't that important!

---

