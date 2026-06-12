---
title: "Securely deleting journaled files"
date: 2010-08-25
forum: Security
---

### Post by desukane on 2010-08-25
This is a very interesting conversation, I think?

Is there a very simple way to incinerate files? Commercials, old files, mistakes, etc.,?
Please leave semantics out of the language. Let's just say, to open or reopen used
drive space and then reuse it in some manner. I want to incinerate files I absolutely
do not want or see no use. With all the wit of an open source this should be quite simple.
I do understand that the MS versions of incinerate are farces, including free and paid
programs. There is a way to erase files or the spaces where they existed so they're usable for several times.
With any luck,
~TR

---

### Post by cariboo on 2010-08-26
You posted in a two year old thread. I've moved your post to it's own thread, as things have changed quite a bit since that thread was started.

---

### Post by BkkBonanza on 2010-08-26
As far as I know there's nothing wrong with **srm** and **sfill** from the secure-delete package. It works fine on journalling filesystems like ext3/4 since usually the journalling is only for file metadata not file contents. It's also easy to integrate into Nautilus if you want to avoid using the cmdline to wipe files.

---

### Post by rookcifer on 2010-08-26
> **desukane said:**
> This is a very interesting conversation, I think?

Is there a very simple way to incinerate files? Commercials, old files, mistakes, etc.,?
Please leave semantics out of the language. Let's just say, to open or reopen used
drive space and then reuse it in some manner. I want to incinerate files I absolutely
do not want or see no use. With all the wit of an open source this should be quite simple.


Yes, just overwrite the data.  Hard drives have a maximum density of data they can hold.  According to some misinformed people, data can be recovered even if it has been overwritten numerous times.  This is absurd on its face because it implies that drives have a density much larger than they actually have.  It implies some sort of layered approach (like an onion) to hard disk engineering which is totally bogus.  The truth is that once data is overwritten once it is gone forever.  Period (or as the Brits say, "Full stop.")

---

### Post by BkkBonanza on 2010-08-26
It was always claimed you'd need very special tools to get at the ghost data. Like electron microscopes and stuff that could read the variances in tracking and see magnetic residuals that weren't perfectly overwritten. I don't think it was bogus at the time originally claimed but it's well beyond any real world threat nowadays because of much tighter tolerances and higher data densities. 

People took the early ideas and extrapolated them well beyond the original merit. Nowadays it's almost certain that single pass overwrites are adequate in any circumstances where total drive destruction isn't the best option.

You do need to use srm or sfill rather than just simple file deletion but the fastest options are likely adequate. I think -vlz or even -vllz options are fine.

What's probably of more concern security wise is the unknown transient copies of data that may exist due to internal data handling in common apps. Potentially there are copies in tmp files or swap space. If truly concerned then time needs to be taken to manage these spaces as well.

---

### Post by movieman on 2010-08-26
> **BkkBonaza said:**
> Nowadays it's almost certain that single pass overwrites are adequate in any circumstances where total drive destruction isn't the best option.

However, you do need to ensure that you overwrite it; there's no guarantee that if you write to a file that already exists, the filesystem will actually overwrite the same block and not write to a different block, though that should be the case with ext3 and maybe ext4. Physical ovewriting is pretty much guaranteed not to happen with a copy-on-write filesystem like ZFS or BTRFS, for example.

So to be really secure you need to overwrite all the free space on the disk, and not just one file. And you need to ensure that the writes actually get to the disk and aren't just sitting in the cache because you didn't flush them out before deleting your file.

---

### Post by BkkBonanza on 2010-08-26
@movieman,
You're right about that. I run **sfill** from time to time to clean up any unknown bits that may have been left behind in free space. Especially if I'm worried about something in particular being left around.

---

