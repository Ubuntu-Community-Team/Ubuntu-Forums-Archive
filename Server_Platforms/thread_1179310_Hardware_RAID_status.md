---
title: "Hardware RAID status?"
date: 2009-06-05
forum: Server Platforms
---

### Post by robodeath on 2009-06-05
I have a HP DL380 G3 server with 3x 74GB SCSI drives in a hardware RAID5 setup.  

Is there anyway in linux to check the status of the hardware RAIDed drives or must I do this in the hardware's setup?  I'm guessing linux can't see the status because it sees it as just one drive, but I wanna ask and make sure.

---

### Post by smileypaul on 2009-06-05
Usually the hardware supplier will supply a utility to monitor the RAID.

With 3ware, the utility is tw_cli , what type of raid card do you have?

---

### Post by robodeath on 2009-06-05
This is all I can seem to find on what type it is:

HP Integrated Smart Array 5i Plus Controller

---

### Post by apel_2804 on 2009-06-05
I'm not shure but I think it is an LSI controller, so you can use megacli to check your raid.

Here are instructions for megacli on an PERC5i (also LSI):
[http://www.tbaumi.de/blog/?p=262](http://www.tbaumi.de/blog/?p=262)

---

