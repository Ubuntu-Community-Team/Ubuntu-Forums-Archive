---
title: "Using Ubuntu Live cd to recover data on a broken RAID5 array?"
date: 2007-12-12
forum: Server Platforms
---

### Post by Krunk_Kracker on 2007-12-12
Is it possible?? 
I read somewhere that Ubuntu Ultimate edition may do it, but I tried it and it did not see it. Do I need to slipstream the raid drivers??

---

### Post by zaber on 2007-12-12
What type of raid array?  I think the live CD can see a MD raid but may be wrong.

---

### Post by Krunk_Kracker on 2007-12-12
Oh sorry, thought I added that. 

It's a RAID5 array on a LSI Logic 1030 controller.

MD?

---

### Post by zaber on 2007-12-12
I am sorry I do not know about a LSI adapter.  MD raid is what I call a Linux software raid because the devices are /dev/mdx.

---

### Post by rsw686 on 2007-12-12
You need to use the software that comes with the RAID controller. Your best bet would be to contact LSI. This is why I tend to stay away from hardware RAID controllers and their proprietary format. If this was a software raid you could move the drives to any linux box and run mdadm --assemble.

---

### Post by Krunk_Kracker on 2007-12-13
> **rsw686 said:**
> You need to use the software that comes with the RAID controller. Your best bet would be to contact LSI. This is why I tend to stay away from hardware RAID controllers and their proprietary format. If this was a software raid you could move the drives to any linux box and run mdadm --assemble.

Basically are you telling me it can't be done on a LSI controller?


:(

---

### Post by rsw686 on 2007-12-13
I'm not saying it can't be done. I'm not sure what the LSI drivers / software allow you to do as far as recovery goes. I'm not going to make guesses on it and risk your data. I know how linux software RAID works and could tell you how to recover it. Good luck getting the data back. In the future you should always test out recovery by failing a drive, etc before putting the system into production.

---

### Post by digitalbenji on 2007-12-13
Hardware RAID is handled by a special chip on the RAID controller card.  Software RAID is handled by the kernel system.  The important difference is that software RAID is the same regardless of hardware.  Hardware RAID is hardware dependant (usually).  You should check your RAID controllers BIOS utiltiy and see if that is helpful.  You may only have 1 failed drive, which is salvagable on RAID 5.  However, if you have 2 failed drives, and you only had 1 drive available as the parity disk, your likely out of luck.  If the controller is malfunctioning, replacing it was an identical RAID card, or at least one of the same manufacturer, should be able to recover the data.  I prefer to keep two hot swappable drives in any RAID5 system, just in case.

---

### Post by Krunk_Kracker on 2007-12-13
> **rsw686 said:**
> I'm not saying it can't be done. I'm not sure what the LSI drivers / software allow you to do as far as recovery goes. I'm not going to make guesses on it and risk your data. I know how linux software RAID works and could tell you how to recover it. Good luck getting the data back. In the future you should always test out recovery by failing a drive, etc before putting the system into production.

It was brought to me in this state...it's a VERY old rack mount server and yeah, two drives are most likely toast...thanks fella's.

I'm at my wits end about this, so I was trying to find other ways to possibly recover the data.

---

### Post by rsw686 on 2007-12-13
> **Krunk_Kracker said:**
> It was brought to me in this state...it's a VERY old rack mount server and yeah, two drives are most likely toast...thanks fella's.

I'm at my wits end about this, so I was trying to find other ways to possibly recover the data.

Two drives out of how many? If it was RAID 5 you will have lost some of the data as there is only one parity drive. I know with software RAID you can still mount it read only and can recover the data from the remaining drives. I would contact LSI and see what they have to say.

---

### Post by Krunk_Kracker on 2007-12-13
> **rsw686 said:**
> Two drives out of how many? If it was RAID 5 you will have lost some of the data as there is only one parity drive. I know with software RAID you can still mount it read only and can recover the data from the remaining drives. I would contact LSI and see what they have to say.
Out of 3 :(

---

### Post by rsw686 on 2007-12-13
Well you can guarantee about half the data is lost. If the data is that important you will need to send the drives to a data recovery place. They can dissemble the drives, repair them, and recover the data. Although this isn't cheap and probably 5k +

---

