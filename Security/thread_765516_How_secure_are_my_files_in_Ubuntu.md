---
title: "How secure are my files in Ubuntu?"
date: 2008-04-24
forum: Security
---

### Post by DJRepresent on 2008-04-24
How secure are my files in Ubuntu? If lets say I want to keep certain documents hidden from others, is there a way to protect them better than what NTFS currently offers?

By saying NTFS I mean that in a Windows based machine, one could always unscrew the hard drive and load it onto another computer as a slave or via USB, take ownership, and download the files. I heard that on Linux you can password protect certain files / directories and if you forget your password, you've lost your data for good.


Thanks

DJ

---

### Post by techolous on 2008-04-24
> **DJRepresent said:**
> 
By saying NTFS I mean that in a Windows based machine, one could always unscrew the hard drive and load it onto another computer as a slave or via USB, take ownership, and download the files. I heard that on Linux you can password protect certain files / directories and if you forget your password, you've lost your data for good.


What you are talking about is file encryption. I personally use '[cryptkeeper]("apt:cryptkeeper")', which is a frontend to 'encfs'. You could do this on windows with software like [TrueCrypt]("http://www.truecrypt.org/"). (or BitLocker in some versions of Vista)

Be aware that some programs might cache copies or metadata in other places. This is why people opt for full disk encryption, which I won't cover here.

---

### Post by Dr Small on 2008-04-24
There is always Truecrypt and GPG.
I use GPG to encrypt my files, though.

---

### Post by aysiu on 2008-04-24
Unless they're encrypted, your files are no more secure than they would be on Windows or Mac. Physical access is root access.

---

### Post by kevdog on 2008-04-24
This site is a good reference since it summarizes some file encryption techniques:
[http://www.movingtofreedom.org/2007/02/21/howto-encfs-encrypted-file-system-in-ubuntu-and-fedora-gnu-linux/](http://www.movingtofreedom.org/2007/02/21/howto-encfs-encrypted-file-system-in-ubuntu-and-fedora-gnu-linux/)

Notice whole disk encryption is a separate option and not discussed here.

---

### Post by hyper_ch on 2008-04-25
with the alternate install cd you can fully encrypt your system upon installation....

If you choose to do that... also make backups of your data... in case your harddisk fails at critical points you may not gain access to the encrypted data at all.

---

### Post by kevdog on 2008-04-25
Just a question...

If your harddrive fails at critical point on an non-encrypted disk -- wouldn't you be unlikely to recover files from it either??  Or is the recovery of files using disk encryption much more sensitive to hard drive encryption?

---

### Post by hyper_ch on 2008-04-26
Well, if you have a bad block on a non encrypted drive, then it will affect one for maybe a few other files... however if you have a bad block on a critical part of the encryption partition you may not be able to unlock all encrypted data any longer.

---

