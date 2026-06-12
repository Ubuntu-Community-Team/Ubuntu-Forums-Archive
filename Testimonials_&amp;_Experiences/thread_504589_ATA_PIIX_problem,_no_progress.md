---
title: "ATA PIIX problem, no progress"
date: 2007-07-19
forum: Testimonials &amp; Experiences
---

### Post by trainpic on 2007-07-19
Many people have posted here and in Malone on the bug with the ata_piix module. This has caused numerous problems for many people trying to use intel chipset ATA, serial ata, etc. drives. Fortunately for me, the problem does not prevent access to my hard drive as it is scsi. However, it does prevent the live and alternate install CDs from booting. They work great on my laptops, yet on two high end HP desktops choke with the infamous and ubiqitous "cannot access tty" error. This problem affects a significant portion of ubuntu users, judging by the bug reports and Ubuntu forum posts, and is still not fixed, despite having been an issue since feisty's first test CD releases.

I plan to do some research to see if the problem is upstream in the kernel. It would seem to be as of 2.6.20, as the latest version of knoppix with 2.6.19 boots fine for most people who have tried it. If the problem is upstream in the kernel then it cannot be a criticism for the Ubuntu devs, but otherwise...

I love Ubuntu. It is a great system, and the devs do a great job of keeping it secure and operational. But this issue is going to frustrate many people to the point where they will no longer consider Ubuntu or even Linux. It already has driven some people away.

BTW, I am not making a case for leaving Linux...
Please no "windows has more serious issues..." posts, they are just to obvious:D

---

### Post by wolfen69 on 2007-07-19
you might be better served posting in the appropriate(help) forum.

---

### Post by trainpic on 2007-07-19
I have...
There are no solutions forthcoming. I am simply raising awareness of this problem.
I am an experienced user/admin and I have managed to install Ubuntu another way (netboot) but I cannot access the CDROM.

I have researched the problem and it appears to be more widespread than just ubuntu...

The ata_piix implementation is buggy. It grabs control of devices it cannot handle. I have an ICH4 chipset... This is only for my CDROM, my HD is on a separate SCSI bus. The IDE CD is grabbed by ata_piix and then ignored. Nothing I do to bypass this appears to work.

ata_piix needs to be fixed. A quick hack from the forums is not going to do it.

---

