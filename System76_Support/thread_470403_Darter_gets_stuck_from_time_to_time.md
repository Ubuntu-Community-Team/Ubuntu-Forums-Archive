---
title: "Darter gets stuck from time to time"
date: 2007-06-10
forum: System76 Support
---

### Post by perce on 2007-06-10
Hello,

my Darter, from time to time, gets stuck for a while. It is nothing really serious, but a little annoying. Apparently it happens only on when pluged to AC, and it happened the first time a few days ago, after about two weeks I was using it.

This is the output of dmesg immediately after it happened:

[ 6237.900000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 6237.900000] ata1.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x0 data 0 
[ 6237.900000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[ 6244.904000] ata1: port is slow to respond, please be patient (Status 0xd0)
[ 6267.920000] ata1: port failed to respond (30 secs, Status 0xd0)
[ 6267.920000] ata1: soft resetting port
[ 6268.264000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[ 6268.272000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[ 6268.272000] ata1.00: configured for UDMA/100
[ 6268.452000] ata1.01: configured for UDMA/25
[ 6268.452000] ata1: EH complete
[ 6268.468000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[ 6268.476000] sda: Write Protect is off
[ 6268.476000] sda: Mode Sense: 00 3a 00 00
[ 6268.508000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6268.540000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[ 6268.556000] sda: Write Protect is off
[ 6268.556000] sda: Mode Sense: 00 3a 00 00
[ 6268.588000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

---

### Post by tedrampart on 2007-06-11
I had this too, try putting a cdrom in the drive, it should stop the problem.. my gazelle does that too.. also email tech support about it.

---

### Post by thomasaaron on 2007-06-11
By looking at the log, I can see it is a common problem we've dealt with on Darters and Gazelle Values.

Running the System 76 driver and rebooting should fix it.
However, once you've done that, you probably shouldn't leave a CD or DVD in the drive when you don't need to. We've had some reports of that causing freezing too. Although, when you're actually using them, it doesn't seem to freeze.

---

### Post by perce on 2007-06-11
Thank you Tom. I ran the drivers when I reinstalled. Can the problem be that I didn't run them after the last kernel upgrade in Ubuntu two days ago? I never had this problem until very recently.

---

### Post by thomasaaron on 2007-06-11
Hmmm. Yeah, I didn't download the new kernel updates till today. So far, I've not had any problems, but one can never tell.

I'd go ahead and run them again, and let us know how that affects the freezing.

---

### Post by perce on 2007-06-11
No freeze tonight; the drivers probably have fixed the problem. Thank you Tom.

---

### Post by perce on 2007-06-14
Hi Tom,

I've made a couple of test with the CDrom, as you had anticipated I experienced a couple of freezes. With one CDrom after a whole evening I was working with it on the drive, with the other one after few seconds. The freezes with the CDrom are much worse than the one I had before running the drivers: they both required me to turn power off. When the computer was stuck I could still switch between X and console, and the console was saying

hdb: device not ready for command  

every couple of seconds.

---

### Post by thomasaaron on 2007-06-14
Thanks.

Stay tuned... I'm working on a firmware update that might nip this freezing problem once and for all. It might take me another day or two.

Best,
Tom

---

### Post by atenlaugh on 2007-06-16
Not that it matters, since it seems to be being worked on as quickly as it can anyway, but I'm also getting the error:

hdb: device not ready for command    

on a 2.0.4 Darter.

---

### Post by thomasaaron on 2007-06-18
1. Did you try running your System 76 driver? If not, that might fix it.
2. If so, do you have a cd/dvd in the drive? That will cause errors if you leave it in there when you're not actually using it.

---

