---
title: "Fastest way to write to SCSI tape?"
date: 2007-08-28
forum: Server Platforms
---

### Post by HermanAB on 2007-08-28
Hi guys,

Does anyone know what is the fastest (most efficient) way to write to SCSI tape?

Tar seems to be the worst way...

Cheers,

Herman

---

### Post by lakris61 on 2007-08-29
> **HermanAB said:**
> Hi guys,

Does anyone know what is the fastest (most efficient) way to write to SCSI tape?

Tar seems to be the worst way...

Cheers,

Herman

The limitations are in tape speed and tar, even if compressing, can push data to tape several times faster than the tape can recieve it. I don't think You can find a faster way than tar or cat anything similar.

/Lakris

---

### Post by HermanAB on 2007-08-29
It is not that simple.  When I use tar to write a 10GB random file to a SCSI tape, I get 32MB/s.  I can hear that the tape is speeding up and slowing down, so the tape is under-running.  Top shows a processor load due to tar of 4.5%, so the processor is pretty much idle.

When I use a HP test utility to write random data to tape, the tape runs a full speed and I get 67MB/s.

I have tried a different faster machine, and got the same results.

Soooooo, since the HP test utility uses the same hardware and the same device driver but gets double the speed, the problem must lie with the way that tar sends the data to the device driver.

Any ideas?

Cheers,

H.

---

