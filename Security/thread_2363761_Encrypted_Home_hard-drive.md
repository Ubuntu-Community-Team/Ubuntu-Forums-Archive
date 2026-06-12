---
title: "Encrypted Home hard-drive"
date: 2017-06-14
forum: Security
---

### Post by Sami_Mattila on 2017-06-14
I have an encrypted Hard-Drive I have used as Home drive for a while now.
Every time I re-install Ubuntu (or Debian) I run in to problems trying to automatically mount the drive as my user's home-drive. (ie. /home/me)

I wonder if some1 could be kind enough to post a short how-to on adding encrypted home drive for proper boot after fresh installation?

---

### Post by TheFu on 2017-06-14
There are 2 major techniques commonly used.  ecryptfs and dm-crypt/LUKS.  HOME directories are usually done with ecryptfs and whole disks are usually done with md-crypt/LUKS/cryptsetup.

Both have issues.  

ecryptfs tends to be slow. It is a FUSE (user-land) file system. It encrypts each file, not the disk. Some information leaks by the file size and location.  It is slow.  System-level backups can only get the encrypted stuff, unless the userid is logged in.  Cron jobs that depend on the unencrypted HOME fail if the userid isn't logged in.  Similar issues like that.

dm-crypt is fast.  About 3% lower performance than without it.  A little faster on CPUs with AES encryption instructions built-in.  It works at the whole partition level, which means it can be used for pretty much anything if you use LVM.  This is the common way that "whole drive encryption" is setup on Ubuntu installs.  To access the disk, a passphrase must be entered - that happens at boot time normally, pre-login.  For the encrypted partition(s), there are 8 password slots, so sharing isn't required on a multi-user system.

There isn't a "short" how-to, because these things are complicated. There are community guides, Forum Posts with how-tos and how-tos on other sites.  All the how-tos that I've seen are 4+ pgs long.

So, if you can more clearly specify which of the solutions you want, someone might be able to post links. A few to get started:
[https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome)
[https://help.ubuntu.com/community/ManualFullSystemEncryption](https://help.ubuntu.com/community/ManualFullSystemEncryption)
[https://www.howtogeek.com/116032/how-to-encrypt-your-home-folder-after-installing-ubuntu/](https://www.howtogeek.com/116032/how-to-encrypt-your-home-folder-after-installing-ubuntu/)
[https://ubuntuforums.org/showthread.php?t=2357627](https://ubuntuforums.org/showthread.php?t=2357627)
Let us know what you intend.

---

### Post by HermanAB on 2017-06-15
It is actually very simple to use LUKS.  Just read the cryptsetup man page.  It is better than any howto guides I have seen.

---

### Post by TheFu on 2017-06-15
The issue with cryptsetup for HOME is that it doesn't explain the steps to mount it pre-login.
Besides that, cryptsetup is a nice tool and easily used for stand-alone data partitions.

Or did I miss the HOME directory mount stuff in the manpage?

---

