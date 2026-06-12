---
title: "Linux dd wiping security"
date: 2022-04-27
forum: Security
---

### Post by Anquietas on 2022-04-27
Hello,

I have some questions regarding the "dd" utility, if someone can help. Please answer only if you are sure about the answer !

I have a scenario here in which I have a HDD with Bad Sectors that I need to wipe in order to archive it.
I want to decomission that respective HDD and I started to wipe it using one-pass zeros.

```

dd if=/dev/zero of=/dev/sda status=progress

```

at exactly 3.7 GB in the Wipe (the HDD has 500 GB capacity), it always throws me a "I/O Error" and the dd utility exists.

I ASUME there is a Bad Sector or something there...

Now, I have multiple questions/issues:

1. Is there a method to WIPE ALL the sectors of that respective HDD, even if there are bad sectors ? Or at least SKIP the bad ones and continue wiping the rest of the HDD which has good sectors ?...
Using "conv=noerror" in "dd" does NOT do the trick, because, as I understand, "conv=noerror" only skips information in the "if" device (input device), not on the "of" device (output device).
I read something about ddrescue and badblocks, and so on, but I did not have a clear answer in my mind...

2. I read somewhere that "dd" is not such a great tool to wipe HDDs... To be more precise, I have heard that "dd" skips some sectors that the Harddisk may have reserved if they are bad sectors, for example.
I need "DD" to access ALL my HDD space.

What I want to say is that I use "dd" for 15 years to wipe all my hdds. Very few of them threw the "I/O Error", and those HDDs were archived and never given away, exactly because of the uncertainty of full wiping... So I did not take any chance...
However, I had HDDs which I wiped completely and which didn't threw any I/O Errors.

Is there even a remote possibility that "DD" did not Wipe everything from these HDDs ?
If I used "dd" and it went ALL THE WAY, until it threw the "No space left on device" message, can I safely asume that it wiped ALL the harddisk space ?
Or even in these conditions, are there some sectors/blocks that might have been reserved and "dd" cannot touch these ? (in which case, it is a security concern)...

Thank you !

Adam.

---

### Post by #&amp;thj^% on 2022-04-27
I'm certainly no Guru on the matter, but I'll add this You want to be able to use the disk afterwards, or not?
Bad sectors cannot be "erased"...they can be noted as being unusable and (therefore) not used during formatting of the drive.  Bad sectors is a phenomenon that relates to every HDD

You can check if there were sectors reallocated with **smartctl** (look at Reallocated_Sector_Count, the last column is the raw value).

If your harddisk supports the security feature set, you can issue a SECURITY ERASE UNIT command in enhanced erase mode, which will also erase.

---

### Post by DuckHook on 2022-04-27
*dd* does **NOT** wipe your HDD. What it does is make a bit for bit copy of a source input file *on to only good sectors* of a destination. Bad sectors are skipped. This is a known security hole. I wouldn't go so far as to say it's a big security hole, but it remains one nonetheless.

There are utilities and built&#8209;ins that are better for true erasure. The utility *wipe* operates at a lower level than *dd*. But the best utility is using *hdparm* and the *--security-erase* flag. This invokes the HDD's firmware to make a true erase, which will overwrite all sectors, both good and bad. Note that a proper erase requires multiple passes and takes a lot of time, especially on large HDDs.

The reality is that none of the above are really the ultimate in security. For that, there is no better alternative than physical destruction. I use the services of a HDD shredder. The HDDs are run through serrated blades that render them so many strips of curled metal and glass fragments. There simply ain't no recovering from that. For data so sensitive that there are legal ramifications if not properly disposed of, I would recommend nothing less.

---

### Post by The Cog on 2022-04-28
I gather that thermite can be very effective - more so than a shredder. I'd like to give that a try one day, just for fun. [https://en.wikipedia.org/wiki/Thermite](https://en.wikipedia.org/wiki/Thermite)

---

### Post by TheFu on 2022-04-28
The threat to the data on the drive should always be the first consideration for what type of 'wipe' is needed.  Govts have restored about 10 layers of prior information from HDDs, so most govt-approved wiping tools require at least 10 passes, each using a different pattern, to make recovery harder.  I've heard rumors that some govts have achieved over 5x the restore layers.  The US DoD doesn't ever sell HDDs from any secure systems. They pull all of them and have them mechanically destroyed.

Now, if you want to clear a disk and keep your sister-in-law from having access, then I'd use 2 passes with /dev/urandom as the input and ddrescue for the tool doing the writing.  That should be sufficient for typical corporate needs and home users who aren't willing to spend $10K/HDD to restore more layers.

This doesn't apply to SSDs or flash storage of any sort.  For that, only physical destruction should be trusted. For paper, physical destruction means turning the paper into something like baby powder. Cross-cut shredders aren't anywhere near enough destruction.

---

### Post by QIII on 2022-04-28
> **The Cog said:**
> I gather that thermite can be very effective - more so than a shredder. I'd like to give that a try one day, just for fun. [https://en.wikipedia.org/wiki/Thermite](https://en.wikipedia.org/wiki/Thermite)

Love thermite!  Very effective and pretty glitter fountains.

---

### Post by #&amp;thj^% on 2022-04-28
> **QIII said:**
> Love thermite!  Very effective and pretty glitter fountains.

Sort of a celebration to the death of the Drive. :)

---

