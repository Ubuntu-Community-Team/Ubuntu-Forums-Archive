---
title: "reinstall on encrypted fs"
date: 2009-05-25
forum: Security
---

### Post by touchlikefire on 2009-05-25
I would like to reinstall Jaunty from the cd on an LUKS encrypted fs, created with the Intrepid installer. How to do this?

I have one encrypted lvm with all my partitions on top of it (I think).

I've been googling and checking the forums for the whole two hours I had planned on watching Superbad, so your help is quite appreciated.

---

### Post by unutbu on 2009-05-25
Here are instructions on how to setup a whole-disk encrypted system: [http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html](http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html)

Although it is called whole-disk encryption, the /boot partition must be left unencrypted so GRUB can boot the system.

The link above refers to Hardy, but it works the same in Intrepid. I assume it also works with the Jaunty Alternate Install CD.

---

### Post by touchlikefire on 2009-05-30
Thanks for the link, good information.  Will this allow me to install Jaunty on an already encrypted fs, while giving me access to my other three already encrypted partitions as well?

---

### Post by unutbu on 2009-05-30
The Alternate Install CD has the dm-crypt module loaded into the kernel by default, so
when you run the alternate installer, it should be able to recognize the LUKS-encrypted partitions that you have already made.

---

### Post by touchlikefire on 2009-06-16
first run with the Jaunty alternate CD: I get to the partitioning screen, select 'manual', and then get scared.  It shows the desired hdd with options to set it as an 'lvm' or 'encrypted lvm' (among all the usual suspects), but I don't want to commit the changes to disk and risk not being able to get into my system.

If someone could give me a step by step of exactly how to use the Alternate CD to install (reformat) Jaunty over the existing Intrepid installation on the LUKS lvm, that would ease my fears.

Particularly, I think once I get to the partitioner I should select the appropriate hdd and set it to 'use as encrypted lvm'. However, I just don't know what will happen once the changes are written to the table, and I don't want to mess it up and be locked out of my drives AND lose all the data.

Thoughts?

---

### Post by ducksun43 on 2009-06-16
this [http://sunoano.name/ws/public_xhtml/dm-crypt_luks.html](http://sunoano.name/ws/public_xhtml/dm-crypt_luks.html) is quite a good site about on-disk encryption as well

hth

---

### Post by touchlikefire on 2009-06-16
Thx ducksun. I gave that a read and wow, a bit over my head for sure. However, if I do run into a situation where my installation of Jaunty messes up my existing LUKS volume I at least have a starting point.

---

### Post by touchlikefire on 2009-07-08
Well, I hosed my partition/volume in quite the unprecedented manner.  

For those who come to this thread after me, please note:
a) it appears a google search of this domain is more accurate and fruitful than utilizing the forum's own search tools; after hosing my system, I retroactively found the answer to my initial question in post 1 by googling it.
b) you must boot the alternate cd in RECOVERY MODE. There are instructions somewhere that I will link later.

My last question before I sadly reformat the entire drive is a volume manager one.  How can I get my volumes back? I rewrote the partition table with identically sized partitions, but did NOT format any partitions. So, the data is still there and intact, I just need to make the volume manager 'see' the volumes.

In chronological order, this is what happened:
[LIST=1]
[*]I booted alternate cd
[*]not knowing that I had to go to RECOVERY MODE, i proceeded with the installation of Jaunty
[*]I went through the partition creation, making sure i did NOT format the partitions
[*]then it asked about volumes, so I attempted to create them
[*]after realizing this might hose my system, i canceled the whole operation
[*]I booted into the LiveCD, verified that my hdd appeared unformatted and empty
[*]tried to resurrect my volumes via volume manager, but no dice
[/LIST]

Not to belabor the pt, but to be clear: I created a new, identically sized (LUKS encrypted, same passphrase) partition via the Jaunty installer, and now my volumes are gone. Can I get them back?

---

