---
title: "GParted, RAID 5, Dell PowerEdge2900 = Can I expand C with Live CD using GParted?"
date: 2014-07-01
forum: Server Platforms
---

### Post by Loan_Refi on 2014-07-01
Hello,

I have a DellPowerEdge2900 with RAID 5 that has run out of space on the boot Drive C. I inherited the server when I took over as IT Admin for the small company.

The server in question is hosting;

2K3 Enterprise OS
DC1
AD
Exchange 2003
Has 3 Physical Hard Drives 140GB in RAID 5

I can not expand a Windows C partition using the Management Utility.

Question.
**Can I expand C Drive with Live CD using GParted?**
I'm not concerned with F Drive and I'm doing an NTBackup now which will take about 4 hours and it's now about 12:30am.

Here is a screenshot of what I'm working with; Your thoughts on expanding C drive using live Ubuntu CD are very much appreciated.

---

### Post by tgalati4 on 2014-07-01
No, I doubt gparted can expand an NTFS RAID.  It doesn't handle RAID, period.  It is for single-drive partitioning.  It can [access]("http://gparted.org/features.php") single drives through RAID hardware and software.  So it might be possible to expand the size of each drive individually and then tell the RAID BIOS to expand the array.

Your PowerEdge probably has a PERC hardware RAID controller and you can boot into RAID BIOS and see if there is an expansion utility.  Good luck finding larger drives that meet Dell specifications and that don't have 50K hours on them.

If your RAID5 is functioning correctly, you could, in theory, pull a drive out, put in a 300GB blank drive and rebuild the array.  Then pull the second drive, put in a 300GB, rebuild again, then pull the 3rd one and put in a bigger drive and rebuild.  Once all of the disks are swapped and rebuilt, you should have a bigger RAID.

A better plan is to simply back up to a couple of separate disks.  Put in 3 new disks, format in RAID BIOS and set up as RAID5.  Then copy your data back into the new array.  Expect breakage.

---

### Post by Loan_Refi on 2014-07-15
Okay so I chose to use AOMEI Partition Assistant Lite Edition - Free Server Partition Manager Software to expand the partition on the same drive. I expanded C into F and got rid of F partition using the AOMEI Partition Assistant.

I appreciate your feedback and like your idea;
"A better plan is to simply back up to a couple of separate disks. Put in 3 new disks, format in RAID BIOS and set up as RAID5. Then copy your data back into the new array. Expect breakage."
However the company that hired me is not looking to spend any more money  on hardware or software and I don't have any other Hard Drives laying around.

I'm attaching a snapshot of the new final Partition.

Thanks for your help,

---

