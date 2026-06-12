---
title: "Backing up encrypted home in 9.10 with rsync+ssh?"
date: 2009-10-31
forum: Security
---

### Post by jonthysell on 2009-10-31
So, I've installed 9.10 UNR on my netbook, clean, using the encrypted home option during install. I want to use rsync+ssh to backup my files securely to a remote server.

I see that ultimately, everything looks like it's really stored under /home/.ecryptfs/<user> and that stuff all gets magically mounted to /home/<user>

So, can I just rsync+ssh /home/.ecryptfs over to the server? Yes, I realize that the filenames would all still be encrypted, and that files will be padded larger, because of the encryption, etc, but that's what I want, encrypted backup files that can be stored on an unencrypted partition on the server.

And say the netbook is stolen, would I be able to decrypt/mount the backup files on the server? As in, ssh into the sever box, run a command to mount the files there, without any access to the original netbook?

Sorry if this is answered elsewhere, but all I can find is info about ecryptfs in jaunty, and about people making backups and not being able to decrypt because they forgot to save /var/lib/ecryptfs or long convoluted restoration steps that require chrooting the original disk, etc.

In other words, are the files stored in /home/.ecryptfs portable and self-contained (presuming I know the passwords)?

Thanks!

/jon

(Currently my desktop just uses full disk encryption, and I have a script that, when the machine is on and drives mounted/decrypted, ssh's into my server, mounts a luks/dm-crypted backup disk there, then performs a rsync+ssh copy of the desktop's unencrypted files to the server's backup drive, then unmounts the backup drive, thereby reencrypting them. It's kludgey as it involves scp'ing a key file temporarily for the mount, and having the same files reencrypted on the server drive.)

---

### Post by oldmankit on 2010-05-02
Blast!  My very question.  But no answers...

---

### Post by jonthysell on 2010-05-03
Yeah, I've just been backing up everything under /home/.ecryptfs on all of my machines. The files are encrypted and so can be put anywhere, though I've still yet to explore the remounting scenario.

---

### Post by oldmankit on 2010-05-03
> **jonthysell said:**
> though I've still yet to explore the remounting scenario.

I've found something that looks promising:
[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)

---

### Post by jonthysell on 2010-05-04
It looks like the answer may be here: [https://answers.launchpad.net/ecryptfs/+question/97115](https://answers.launchpad.net/ecryptfs/+question/97115)

All you need is your "mount" passphrase. You should have saved it somewhere safe when you fist installed the encrypted home folders, but if you didn't I think you can get by running:

```
ecryptfs-unwrap-passphrase
```

Type in your login password and it should spit out your mount password. Keep it somewhere safe!

---

