---
title: "Prefered encryption method?"
date: 2007-05-18
forum: Server Platforms
---

### Post by Xbehave on 2007-05-18
i wondered what the preferred method for encrypting a collection of files is, most of the information i find is either outdated or from one of the makers!
im not sure if to go for an encrypted file system or encrypted containers?which is safer/faster?
which file system/method is best:
if plausible denyability is needed? and if its not?
if performance or security is critical?
if a balance is ok?

so far im looking at (in order of what i get the impression is best)
plausibly deniable:truecrypt, scramdisk
not plausibly deniable: dm-crypt/luks , loop-AES
plausibly deniable file systems(no order): magicfs, phone book, rubberbook

but ive sean places say that loop-AES is more secure ( even tho it doesn't use LRW)
Im encrypting / and /swap /home separately as they will be on separate partitions and im going to be running 7.04. which of the above should i use and could you point me in the direction of a good guide, most of the ones ive found are for LUKS on dapper or before

---

### Post by johannes on 2007-05-19
My preferred method of encryption (which I am currently using) is to encrypt /root and /swap partitions with LUKS. /home is on a separate partition and is encrypted with Truecrypt set to automatically load an outer "fake" volume (after the LUKS boot password) using only a keyfile. The real home is on a hidden volume in the /home partition (providing plausible deniability). So unless you know the first /home volume is fake you can unknowingly overwrite the hidden one. Since most user settings, history and files are stored on the home this feels quite secure.

I also have an external hard disk using Truecrypt (plausible deniability).

For single files I feel it's easier to simply use PGP encryption e.g. when making backup CD:s and DVD:s.

On all the volumes (even truecrypted) I use the ext3 file system. I'm not sure if Truecrypt really supports it but it seems to work for me. FAT systems seems just too much of a hassle for me.

I certainly see a drop in system performance with full disk encryption. Writing and reading the disks takes a few more percent CPU power. Especially when doing both at the same time. However, that's a price I'm willing to pay for security and plausible deniability.

Unfortunately, I am currently on Arch Linux and haven't found many good guides for Ubuntu. However, most Luks guides for Dapper in the wiki should work for Fiesty too. As for Truecrypt, you can find some common info in the Ubuntuforums and in these wikis:

[http://wiki.archlinux.org/index.php/Truecrypt](http://wiki.archlinux.org/index.php/Truecrypt)

[http://gentoo-wiki.com/HOWTO_Truecrypt](http://gentoo-wiki.com/HOWTO_Truecrypt)

Some parts of the should be adaptable for Ubuntu too.

---

