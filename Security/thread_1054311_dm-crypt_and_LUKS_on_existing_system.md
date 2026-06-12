---
title: "dm-crypt and LUKS on existing system"
date: 2009-01-29
forum: Security
---

### Post by peppergrower on 2009-01-29
I've done some searching, but haven't found anything yet that addresses what I'd like to do.  I have a dual-boot system with three partitions: a Windows XP partition, an NTFS data partition, and an Ubuntu 8.10 (ext3) partition.

I'd like to convert the existing setup to full-disk encryption using dm-crypt and LUKS.  Most tutorials I've seen so far assume you're doing a fresh install of Ubuntu.  The one I found that addressed converting an existing system was older, and I wasn't sure what had changed with newer editions.  How do I convert existing partitions?

Additionally, I'd like the entire dual-boot setup encrypted.  Is it possible to do all the partitions at once?  (This would be ideal.)  If not, how should I go about encrypting all three separately so that it's all transparent once I boot?

---

### Post by Tubes6al4v on 2009-01-30
I don't think you can convert to a LUKS encrypted linux after it has been installed. I would back up the data, and reinstall with LUKS. 

As for the NTFS partitions, you can use Truecrypt to encrypt all of it without reinstalling. Hmm come to think of it, there was a thread on here a couple weeks ago about encrypting a linux partition without moving the data. I didn't read it though, maybe have a look.

---

### Post by hyper_ch on 2009-01-30
you can "convert" it. However you will need to have enough space available to shuffle the data around. If you rent a server somewhere that's a route you might want to take and it's not so simple.

If it's your machine where you have physical access to I'd rather say do a fresh install with encryption. It's much less hassle.

Besides, you should always have backups so wiping the actual install drives shouldn't be a problem either.

---

### Post by peppergrower on 2009-01-30
I found [the tutorial I mentioned]("https://help.ubuntu.com/community/EncryptedFilesystemHowto7"), and it has a 'luksConvert' script.  However, since the instructions are for Ubuntu 7.04, I'm a little leery of just blindly trusting them for 8.10 as well.

Installing Ubuntu has been pretty easy (I've done it quite a few times in various VMs), but I don't know the best way to keep all my customizations.  Nearly all of my personal data is on the NTFS partition, but I don't want to have to reconfigure everything.  I'm sure I can find information on preserving my configuration, but if you have any tips I'd appreciate them.

I considered TrueCrypt, and perhaps will still go that way, especially if it makes it easier to encrypt an existing volume.

---

