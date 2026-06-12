---
title: "SATA Hard Drive Detectivity Problem"
date: 2006-01-04
forum: The Cafe
---

### Post by cooldeepagar on 2006-01-04
Hi Everyone,

I am Deepak Agarwal from India.I have just got my new pc, whose specifications  are given below:-

AMD Athlon 3200+ 64 bit processor
Asus A8N SLI Premium motherboard
Albatron 6600gt pci exp graphics card
80 GB Seagate SATA Hard drive
250 GB Seagate Pata Hard drve
Creative Sound Blaster Audigy 2 ZS Sound Card
Sony Dual Layer 8x DVD+- Writer
Sony DVD Rom Drive

I installed win xp sp 2 yesterday and tried to install Red Hat linux Enterprise WS edition on my pc but it didn't recognize  my SATA Hard drive so i install it on my pata hard drive where it got install perfectly.But after using for 5 min my mouse got hanged and after searching for answer I found SUSE 10.0 and Ubuntu are best Linux Distros.

I want to know whether any Linux Distro is thr which recognize SATA hard drive and if not then how can we install linux on SATA Hard Drive since SATA Hard drive are popular now and most ppl prefer SATA Hard drive.

You can send personnel comments to my email id - [email]deep_agar@yahoo.com[/email]

I will be very thankful to anyone who uses Linux in this world to help me install linux on a SATA hard drive.

Regards,
Deepak

---

### Post by KiwiNZ on 2006-01-04
I am running Ubuntu 5.10 on a Sata  no problem.

---

### Post by mo_x on 2006-01-04
I assume the motherboard has a nvidia nforce chipset then sata should be fine.
I also have a sata and pata drive. After installation the drive numbers in the grub config were wrong. I worked around it by disconnecting the pata drive before installation. After installation you can reconnect it and add it to /etc/fstab.

---

### Post by audiocat on 2006-01-09
KiwiNZ,
You stated that you installed Ubuntu 5.10 with no problems...
Here is my setup, and I so far haven't gotten any Linux Distro to recognize the drives. I only downloaded 5.10 today and will try it out...
Anything special you had to do? Install additional drivers...etc?

Brand - BIOSTAR 
Series - iDEQ Model - iDEQ 350G 
Motherboard - Intel i945G-S7
CPU  - Intel Pentium 4 650 Prescott 800MHz FSB LGA 775 
FSB - 800/1066MHz 
Chipset North Bridge - INTEL 945G 
South Bridge - ICH7R 
Memory - OCZ Gold Series 2GB  240-Pin DDR2 SDRAM DDR2 667 (PC2 5400)
PCI Express - SAPPHIRE 100600SR Radeon X800PRO 256MB  Video Card 
Storage - IDE ATA 1x ATA100 (I have DVD Dual Layer installed) 
Serial ATA - 2x SATAII 300  - Western Digital Caviar SE WD1200JS 120GB 7200 RPM SATA 3.0Gb/s
Serial ATA Controller - Intel 82801GH   ICH7

Audiocat

---

### Post by audiocat on 2006-01-09
I installed Ubuntu 5.10 and it found my SATA Drives just fine...Thanks!

---

