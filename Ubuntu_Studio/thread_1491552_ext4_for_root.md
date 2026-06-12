---
title: "ext4 for root?"
date: 2010-05-23
forum: Ubuntu Studio
---

### Post by meanmrmustard on 2010-05-23
Is there a "best" choice for the root file system?
I've used both ext2 and ext3 (for Ubuntu) and can't say I ever noticed a difference.
Can someone list pros and cons for each?

Thanks

---

### Post by ibuclaw on 2010-05-23
> **meanmrmustard said:**
> Is there a "best" choice for the root file system?
I've used both ext2 and ext3 (for Ubuntu) and can't say I ever noticed a difference.
Can someone list pros and cons for each?

Thanks

Admittedly, I don't notice a difference either.

However, you may experience:
[LIST=1]
[*]Faster boot times
[*]Faster fsck times
[/LIST]
When using ext4 instead of the latter two.

Regards

---

### Post by BoneKracker on 2010-05-23
Ext3 is basically ext2 plus journaling (which helps prevent data loss).

Ext4 is ext3 with the ability to handle larger files and volumes, and with other features that make it more efficient.  Ext3 is more proven, but ext4 is better.

[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

For an end user, the main difference is reduced boot-up time (due to delayed inode allocation, which dramatically reduces the time required to complete fsck).  Probably only really meaningful if you're on a laptop.

Ext4 has pretty much replaced ext3 as the general-purpose filesystem of choice.  Btrfs is seen as a potential replacement for ext4, but it is still in development.

I, for one, use ext4 for the rootfs on all my systems (except my router/firewall, on which I use reiserfs).

Also, for some silly "one size fits all" reason, the "huge_file" feature of ext4 is enabled by default.  The "huge_file" feature increases the inode size (meaning a larger inode address must be processed each time data is accessed, kind of like extended zip (postal) codes), and it's only necessary if one wants to work with files larger than 2 Terabytes (that's _files_ larger than 2 Terabytes, not volumes).

I'm honestly not sure how much difference this makes, but you can get rid of it by simply editing the file /etc/mke2fs.conf, changing occurrences of "huge_file" to "large_file", _before_ creating filesystems.

---

### Post by sgx on 2010-05-23
Hi, if you are a frequent upgrader, with a separate /home partition, and backup all your important things immediately, a new filesystem is no big deal, as testing is pretty rigorous, and you already protect against errors on wise the side of caution. 

If those are not the case, let the early-adaptors do their job for a few more months, and stick with ext3. :)

---

### Post by BoneKracker on 2010-05-24
> **sgx said:**
> Hi, if you are a frequent upgrader, with a separate /home partition, and backup all your important things immediately, a new filesystem is no big deal, as testing is pretty rigorous, and you already protect against errors on wise the side of caution. 

If those are not the case, let the early-adaptors do their job for a few more months, and stick with ext3. :)

I would agree.

But what's an "early-_adaptor_"? :P

---

### Post by meanmrmustard on 2010-05-24
Thanks to all for the replies.
I'm going to be adventurous and go with ext4

---

### Post by BoneKracker on 2010-05-24
> **meanmrmustard said:**
> Thanks to all for the replies.
I'm going to be adventurous and go with ext4

Congratulations.  You are now officially an Early Adaptor. :)

---

### Post by sgx on 2010-05-25
> **BoneKracker said:**
> I would agree.

But what's an "early-_adaptor_"? :P

An early-adaptor is a late-adaptor who bought
a prepaid funeral plan, but has yet to use it. ;)

---

### Post by BoneKracker on 2010-05-25
:lol:

How about:

_early adaptor_: a late _adopter_ with a pre-paid funeral plan

_early adaptor_: an early adopter who mods all his hardware

_early adaptor_: a former Obama supporter with a premature eja****tion problem

---

### Post by sgx on 2010-05-25
> **BoneKracker said:**
> :lol:

How about:

_early adaptor_: a former Obama supporter with a premature eja****tion problem

They're actually not former, they just lined up at the back door
of the White House for their free healthcare. Carvill was first in line.
:)

---

### Post by BoneKracker on 2010-05-25
Hey, now.  Let's not get off-topic. :-\"

---

### Post by ibuclaw on 2010-05-25
> **BoneKracker said:**
> Hey, now.  Let's not get off-topic. :-\"
Well, the OP seems to have gotten his answer, and has acted on it (is switching to ext4).

Marking this thread as Solved and Closing.

---

