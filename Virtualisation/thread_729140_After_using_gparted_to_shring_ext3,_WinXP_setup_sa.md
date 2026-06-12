---
title: "After using gparted to shring ext3, WinXP setup says &quot;No HD detected, can't install&quot;"
date: 2008-03-19
forum: Virtualisation
---

### Post by diablo75 on 2008-03-19
I am doing a little test experiment within VMware before I do it in real life, because I don't want to screw anything up.

Here's what I'm doing:

I have installed Ubuntu in a virtual machine with an 8 Gig hard drive.  I then booted with Gparted and shrank the partition down by about 3 gigs, and left the remaining space unallocated.  (I may have had to just create an NTFS partition at this step, but didn't.  Could this be my problem?)

Anyway, with the unallocated space now in between the main ext3 partition and the swap partition, I then booted up a Windows XP install CD.  The setup utility said that it couldn't detect any hard drives in the system.

What did I do wrong?

EDIT:

I went back in with Gparted and formated the unallocated space as NTFS.  So now the hard drive structure is [ext3           |   ntfs    |swap]

Setup still says it can't detect a hard drive....

---

### Post by fedex1993 on 2008-03-19
yes there has been a sevre problem with installing ubuntu then reinstalling xp. i dont remember a fix the problem. I would backup ubuntu then reinstall windows xp then reinstall ubuntu might be the easyest

---

### Post by dcstar on 2008-03-21
> **diablo75 said:**
> I am doing a little test experiment within VMware before I do it in real life, because I don't want to screw anything up.

Here's what I'm doing:

I have installed Ubuntu in a virtual machine with an 8 Gig hard drive.  I then booted with Gparted and shrank the partition down by about 3 gigs, and left the remaining space unallocated.  (I may have had to just create an NTFS partition at this step, but didn't.  Could this be my problem?)

Anyway, with the unallocated space now in between the main ext3 partition and the swap partition, I then booted up a Windows XP install CD.  The setup utility said that it couldn't detect any hard drives in the system.

What did I do wrong?

EDIT:

I went back in with Gparted and formated the unallocated space as NTFS.  So now the hard drive structure is [ext3           |   ntfs    |swap]

Setup still says it can't detect a hard drive....

If you are trying to install XP within VMware, then you need **a VMware virtual drive** to install on, not physical drive space.

Virtual machines do not use physical drive resources, they use the virtual environment you create for them.

---

