---
title: "RAID 5 Won't boot any more"
date: 2012-09-26
forum: Server Platforms
---

### Post by rbmason on 2012-09-26
Hi all,

I have a 12.04 system with a RAID-5 disk setup across 3 disks. This was all going swimmingly, until today, when I restarted following a software update.

when I try to boot normally, I just get the GRUB bootloader then nothing further - purple screen and no further progress.

When I boot to recovery mode, I get:

mdadm: CREATE group disk not found
could not start the RAID in degraded mode

If I exit from that, it takes me to Recovery menu (filesystem state: read-only)

running fsck on the disk reveals no errors

Apologies for noob questions here, but where do I go next with this? I am able to resume and boot normally and it all works (more or less) and the filesystem seems ok. Clearly not though as I cannot boot normally....

Thanks in advance for any help and advice.
Richard

---

### Post by bart.a on 2012-10-23
After the resumed boot, did you check your array with the mdadm utility? check [this site]("https://help.ubuntu.com/12.04/serverguide/advanced-installation.html") under raid maintenance..

---

