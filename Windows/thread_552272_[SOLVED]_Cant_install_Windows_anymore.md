---
title: "[SOLVED] Cant install Windows anymore"
date: 2007-09-16
forum: Windows
---

### Post by david2007 on 2007-09-16
Hi , i have a strange problem and i was wondering if someone could help me ..
I am  trying to reinstall windows , actually to make a clean installation but when i boot in to the configuration window from the windows cd and i choose the partitiion i want , i can format it but afterwards i get a message that the following disk is either damaged or corrupted . This is strange because on the same disk i have two other partitions with data which i can access ofcourse from Ubuntu  and Ubuntu i have on a different disk installed .
Now when i try to install windows taking the hard disk out which has the Ubuntu , after i insert the windows cd i see the message : setup is now inspecting your HW configuration ..and after this i see a black screen with nothing going on :confused:
I tried from Ubuntu formatting the partition which i would install windows  in Ntfs format but nothing is changing .  The mbr was corrupted but ofcourse i could fix this easily with the Live cd .
I never had this problem before and i did thousand installations before. 
How is this possible , before i started the installation the partition with the older windows was perfecty fine , any suggestions :confused:
Because this is my 500gb disk i cant fix new partitions and reformat it because i have data on ..and dont have an external 500GB:(

---

### Post by exploder on 2007-09-16
The only solution I have ever found for this problem is to use fdisk.

I used a Windows ME disk to fix this.

I booted off the ME disk and pressed F5 to get to a command prompt.

Switched to D:\ and type fdsk

Remove all partitions, starting with the last one first

Exit from fdsk and at the prompt type fdsk /mbr

Windows should install without any problems now.

I wrote down the steps from memory. The problem is that Grub is on the mbr and Windows doesn't like anything there when it loads. These steps will make Windows see the disk as "New Unformatted".

Hope this gets you going.

---

### Post by david2007 on 2007-09-16
so the only way is to repartition the disk..then probably i have to find another HD to backup my data :(

---

### Post by exploder on 2007-09-16
Yes, back up all your data.

I wish I had a better solution but that is the only one I have ever found to work. Windows is the problem, not Ubuntu.

Also, I would fully update Windows before installing Ubuntu.

---

### Post by david2007 on 2007-09-18
found another solution and it worked .I describe the steps that i followed .
 From the gparted i could see there is something wrong with the partition . Could not delete it  . I didnt knew even if the flags were ok , i changed them to boot but the same problem  remained. After this i run PClinuxOs from a live cd and tried with a partition manager from there and could delete the partition succesfully . So windows recognize the disk and i could install it . But forgot that i had also my home drive  from ubuntu there in another partition which was deleted by accident. This happens if you have many partitions and you mix them .
Now from scratch again :lolflag:

---

### Post by K.Mandla on 2007-09-20
Moved to Windows Discussions. ;)

---

