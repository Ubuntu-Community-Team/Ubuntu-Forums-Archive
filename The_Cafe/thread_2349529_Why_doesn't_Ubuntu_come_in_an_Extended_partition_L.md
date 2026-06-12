---
title: "Why doesn't Ubuntu come in an Extended partition LIVE USB"
date: 2017-01-15
forum: The Cafe
---

### Post by checoimg on 2017-01-15
Back in time I was trying to get a set-up with Extended partitions but I had problems. And I had a questoin about why wouldn't it be in an extended partition from the USB ?

---

### Post by Bucky Ball on 2017-01-15
Because not everyone wants to install it that way? If you choose 'Something Else' at the partitioning section you can manually partition the disk however you want, extended partitions or not.

Because you had a problem creating extended partitions is probably not a good enough reason to reinvent the wheel. If you need help with extended partitions, of course, post a thread in one of the support areas and sure you'll find plenty. :)

---

### Post by checoimg on 2017-01-16
Yes, I only thought why not use a more flexible patitioning but we can get that most systems are well defined at installation time.

---

### Post by oldfred on 2017-01-16
If you are using the old MBR(msdos) partitioning system, the installer does automatically create an extended partition. If two of the allowed primary partitions are available then it puts swap into an extended partition.
But almost all Windows 7 systems use all 4 primary partitions. Almost like they want to make it difficult to install anything else.
Windows uses two, boot & main install. And vendors use 2, a recovery & misc utilities.

But new UEFI based systems, All Mac with Intel chips & all Windows 8 or later (2012) pre-installed systems use gpt partitioning which has a limit of 128 partitions. It does not have primary, extended and logical, so in effect all partitions are primary with gpt.

       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

### Post by yoshii on 2017-01-25
I read somewhere that putting the SWAP into the extended partition supposedly makes it more secure in terms of RAM hacks.  But personally, I never used extended partitions in my entire life of computing since the 1980s.  I just find a way to just have 4 partitions or less no matter what.  I'm also scared of UEFI and secure boot.  But yeah, I'm old-fashioned and odd.  But it does simplify a lot of things to just phase out the complexity.  :D

---

