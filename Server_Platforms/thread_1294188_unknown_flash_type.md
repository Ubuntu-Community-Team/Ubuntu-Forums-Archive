---
title: "unknown flash type"
date: 2009-10-18
forum: Server Platforms
---

### Post by coronaas on 2009-10-18
my old roomate left me his 9.04 ubuntu server. i Tried running >sudo aptitude update && sudo aptitude dist-upgrade . after completion i ran >sudo shutdown -r now. upon bootup the server hangs at acpi controller saying "unknown flash type"

everything ive read is about this error occurring after flashing the Bios which i wasnt doing so im confused what went wrong.

I tried reinstalling ubuntu and an still getting the same error

one thing of note the boot drive was a 20 gig HDD with 2 400gb drives in a raid 5 format. I can view the raid when repartitioning the drive but i cant find the 20gig boot disc

---

### Post by cariboo on 2009-10-18
What type of raid was it originally, software, fake or hardware?

If you were ruinning raid5, you also seem to be missing a parity drive. If you boot from a Live CD can you see all the drives?

---

