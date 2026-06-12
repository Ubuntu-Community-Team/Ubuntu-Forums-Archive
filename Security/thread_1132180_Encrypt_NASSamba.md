---
title: "Encrypt NAS/Samba?"
date: 2009-04-21
forum: Security
---

### Post by fhsm on 2009-04-21
I use Ubuntu 8.10, OS 10.5, and Windows XP Pro.  I have a RAID NAS on my network I use to store some common files and backup all of my systems to.

I store my documents in encrypted volumes on all systems.  Of course these documents get decrypted on the fly and backed up in the clear on my NAS.  This is obviously a significant hole.  

I'd like to encryption before sending the data to the NAS.  I need whatever tool I'm using to be cross platform so I can decrypt a file from all three systems.  Any ideas?

Thanks!

---

### Post by bodhi.zazen on 2009-04-21
Did you try ssh ? Take a look at scp and sshfs.

Many tutorials on sshfs, try :

    [http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html](http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html)

---

### Post by lensman3 on 2009-04-21
Encrypt the NAS and then put a file system on top.  Use "truecrypt" as the encryption program. The only common filesystem between Linux, OSX, and Xp is DOS.  You will have to format the disk with DOS after truecrypt has laid down the encrypted system.  I have moved a SATA drive between work (XP) and home (Linux).  Truecrypt runs native on both and has no problem decrypting the file system.  If someone steals the drive, it looks like it has never been formatted.  Truecrypt is free.  

I am currently backing up my home network using truecrypt as the encryption program.  On top of truecrypt I have a ext4 partition.

Hope this helps.

---

### Post by fhsm on 2009-04-22
> **bodhi.zazen said:**
> Did you try ssh ? Take a look at scp and sshfs.


That seems like it would give me a secure connection but not secure storage on the NAS file system.  Or have a I missed something?

> **lensman3 said:**
> Encrypt the NAS and then put a file system on top.  Use "truecrypt" as the encryption program. The only common filesystem between Linux, OSX, and Xp is DOS.  You will have to format the disk with DOS after truecrypt has laid down the encrypted system.  I have moved a SATA drive between work (XP) and home (Linux).  Truecrypt runs native on both and has no problem decrypting the file system.  If someone steals the drive, it looks like it has never been formatted.  Truecrypt is free.  

I am currently backing up my home network using truecrypt as the encryption program.  On top of truecrypt I have a ext4 partition.

Hope this helps.

Not sure I follow how.  If I encrypt this sounds like the NAS is going to have to do the crypto itself, which is clearly not an option given the processor power of the nas.  It does however seem likely that TrueCrypt will be involved in this at some point.  Could you give a little bit more detailed explanation?

---

