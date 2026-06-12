---
title: "Installing Windows on a RAID0 question"
date: 2008-12-15
forum: Windows
---

### Post by Lateforgym on 2008-12-15
I have the RAID0 setup however, when I got to Install Windows, its gives me the option only to install windows on one of the 500GB drive. Also there is a 20GB partition in there that was setup from my previous Ubuntu install (I belive thats what that is).

I though the RAID is supposed to see this as "one drive", thus it shold let me create one partition for the full terrabyte HDD, not have Windows installation showing 2 500 GB drives and a 20GB unused partition from prvious use. How do I zap all these so it just sees the RAID as one 1TB HDD? 

I dont think my system is correct as is, because on POST it shows 1TB, but if I agree to install windows to one of the 500GB partitions, once Windows is installed, its only shows that the HDD capacity is 500GB not 1TB as POST shows.

Thanks

---

### Post by justinhornberger on 2008-12-15
Are you trying to use a raid that is built into the motherboard or a raid card, or a software raid in ubuntu?

---

### Post by Lateforgym on 2008-12-15
This is an onboard RAID by Silicon image, not the Intel Matrix system (from the chipset).

This board actually has two seperate RAID system (Chipset and onboard Silicon Image, Inc).

Still though, shouldnt the RAID0 be showing up as 1TB? When I try to delete the partitions, Windows installer doesnt allow that. What Im trying to do is delete how XP OS install hows 2 500GB partitions and a 20 MB partition. It only lets me install on one of the partitions. Is that how its supposed to work? Shouldnt I be seeing one partion for 1TB?

---

### Post by justinhornberger on 2008-12-16
Ok, what do the instruction say you need to do for drivers.  Whenever I have loaded windows up on a raid I have needed to install the drivers with a floppy disk at the first part of the windows install.  You will need to press f6 when it asks you if you need to install third party raid drivers and then do so for the card to be recognized and windows to see it as one drive.  Take a look at the instructions and see what kind of drivers are needed.

---

### Post by rickyjones on 2008-12-16
> **Lateforgym said:**
> This is an onboard RAID by Silicon image, not the Intel Matrix system (from the chipset).

This board actually has two seperate RAID system (Chipset and onboard Silicon Image, Inc).

Still though, shouldnt the RAID0 be showing up as 1TB? When I try to delete the partitions, Windows installer doesnt allow that. What Im trying to do is delete how XP OS install hows 2 500GB partitions and a 20 MB partition. It only lets me install on one of the partitions. Is that how its supposed to work? Shouldnt I be seeing one partion for 1TB?

Windows does not have the proper device drivers for your RAID device. When you begin the installation it prompts you to hit F6 to load additional drivers. Do this and insert a floppy disk with the proper Windows drivers for your RAID card. If you don't have a floppy drive then you'll need to create a new installation CD that already has the drivers slipstreamed.

Once the proper drivers are loaded you'll be able to see the true array structure.

Thanks,
Richard

---

