---
title: "Router vs. External HD"
date: 2011-05-08
forum: The Cafe
---

### Post by Shibblet on 2011-05-08
I recently purchased a Western Digital My Book Essentials 3TB external USB hard drive.

I hooked this up to my Linksys E3000 router, and it registers the drive as ~750g.

I have tried everything to make this show up as a 3TB Drive.  And nothing.  I have also searched the internet for any reason as to why this is.  My only guess is that this router doesn't support a 3TB Drive.

Does anyone know what I am doing wrong?

---

### Post by CharlesA on 2011-05-08
Isn't that one of the advanced format drives?

Does it show up as 3TB if you hook it up to a computer?

---

### Post by Shibblet on 2011-05-08
> **CharlesA said:**
> Isn't that one of the advanced format drives?

Does it show up as 3TB if you hook it up to a computer?

I have to set it up GPT in Windows 7 x64 in order to see it as 3TB.

---

### Post by CharlesA on 2011-05-08
> **Shibblet said:**
> I have to set it up GPT in Windows 7 x64 in order to see it as 3TB.
I meant, is it one of those drives with 4096 byte sectors instead of 512 bytes sectors?

Most 3TB drives are that way IIRC.

---

### Post by srs5694 on 2011-05-08
The links to the spec sheet for the drive on WD's site are broken, so I can't check the critical detail of the logical sector size -- that is, whether the drive tells the computer that it's got a 512-byte sector size or a 4096-byte sector size. If the former, then 3 TB is roughly 3 x 10^12 bytes, or 5,859,375,000 sectors. This is more than 2^32 (4,294,967,296) sectors. Thus, if the E3000 router has a 32-bit limit on the number of sectors it can handle, it won't work correctly with the drive. I've heard of this sort of thing before, and one common symptom is that the first 2^32 sectors are ignored. That would leave roughly 1,564,407,704 sectors, or about 746 GiB (800 GB) visible to the device. This matches well with your observation, so I strongly suspect it's what you're seeing.

AFAIK, there's no workaround or fix possible for this, short of updating the firmware. I recommend you contact the manufacturer about the issue, or check their Web site for firmware updates. There's also an open source firmware replacement for this and many other routers called [Tomato.](http://www.polarcloud.com/tomato) I don't know much about it, though. I don't know if it supports the USB port for storage devices, for instance, and if so I don't know if it's got a 32-bit limit on disk size. It might be worth investigating, though.

---

