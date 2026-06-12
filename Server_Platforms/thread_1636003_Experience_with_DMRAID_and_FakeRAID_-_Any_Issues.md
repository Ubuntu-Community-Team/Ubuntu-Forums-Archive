---
title: "Experience with DMRAID and FakeRAID - Any Issues?"
date: 2010-12-02
forum: Server Platforms
---

### Post by bsntech on 2010-12-02
Just received the five 500 GB hard drives and RAID cage last night.

Looking to use a RAID-1 array using the built-in nVIDIA FakeRAID on the motherboard.

I've seen some bad press about the dmraid program not being able to rebuild a failed array in the past - but dmraid has been updated with Lucid 10.04 to a newer, 2009 (rc16) version.

What kind of experience has the board had with using the new version of dmraid in their FakeRAID array?  If you respond, please also note what type of FakeRAID you have (silicon image, nvidia, etc).

Before I begin to use this over the weekend, I wanted to see what comments you all have about it.

I have an external hard drive that has Ubuntu on it; going to update that to 10.04 so I can put the newest dmraid on it as well.  Take a backup image of the server using partimage - then turn on the RAID-1 array in the BIOS.  Hopefully I can then boot up again with the external hard drive seeing the new RAID array, restore the image to the RAID array, then update grub to point to the proper location.  Definitely cannot rebuild the server from scratch so I hope this technique is going to work.

Thank you all!

---

