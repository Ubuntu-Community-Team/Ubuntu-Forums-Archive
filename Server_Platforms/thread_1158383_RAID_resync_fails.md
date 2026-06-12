---
title: "RAID resync fails"
date: 2009-05-13
forum: Server Platforms
---

### Post by andyrowe on 2009-05-13
I'm sorry folks but I'm really struggling here. I have ubuntu server loaded on a box I hope to use as a file server on an MS Win AD domain. I posted an earlier thread how I thought the power was being lost to the machine causing the RAID1 disc array to drop to degraded mode. Here's a link to that thread: [http://ubuntuforums.org/showthread.php?t=1158019](http://ubuntuforums.org/showthread.php?t=1158019)
The box has two brand new 1TB seagate hard drives and uses mdadm to create software RAID.
At least once the machine definitly lost power (no UPS at the time) and the RAID dropped to degrade mode. Since then I've removed and readded the failed drive and it began resyncing. Now I've been sitting next to it all day and this comes up on the screen
[442373.528726] ata3.00: irq_stat 0x40000001
[442373.528743] ata3.00 cmd ea/00:00:00:00:00:00:00:00:00:00a0 tag 0
[442373.528744] res 51/04:00:00:00:00:00:00:00:00:00a0 Emask 0x1 (device error)
[442373.528782] ata3.00: status: { DRDY ERR }
[442373.528795] ata3.00: error: { ABORT }
[442373.749681] end_request: I/O error, dev sdb, sector 1953519866
[442373.749704] raid1: disk failure on sdb2, disabling device
[442373.749705] raid1: operation continuing on 1 devise
 
I'm almost certain the machine didn't lose power. What happened here? Did the resync just fail? Is one drive physically damaged (brand new) Why doesn't it just mark that sector as bad and not use it? Can I rscan the disc to remove the bad sector from the file allocation table? Am I thinking to Windowsy here?
thanks in advance
andy

---

### Post by a9k3d on 2009-05-14
I also had a Seagate 1TB drive do this to me. It behaved like it spun up but nothing worked. It would take linux several minutes of trying to reset the drive before linux mapped it as bad. 

I replaced it with a Samsung and have had no problems since.

I read up on the error a bit - some people say it can be caused by a bad sata (data) cable. You could try swapping the drives on the ends of the cables or swapping cables. That might have been my problem because I mounted the new drive on a different cable and port.

---

### Post by Lampi on 2009-05-14
@andyrowe: if it's the 1TB Baracuda series check the firmware this drive using. This can by done with "smartctl -i /dev/<devicename>"

Seagate had a couple of Baracuda series with bad firmware inside, causing the disc to fail - just make sure you don't have one of them.

And you could read out the S.M.A.R.T Data of the drive ("smartctl -a /dev/<devicename>") to check the healthy of your disc in general.

If you think the values look fine you could run the long S.M.A.R.T healthy test (which will take several hours to complete) and then read out the S.M.A.R.T data again.

Util then I wouldn't reassign the drive to your array since there is no use in that, it will possibly break again - so run the S.M.A.R.T checks with the drive unassigned.

---

### Post by andyrowe on 2009-05-14
Thanks for the help guys!
I checked the seagate website and neither drive is one of the ones effected by the firmware issue. I do have another cable I can swap to see if the cable is the issue. What scan tools can I use in Linux to check and repair bad sectors on this drive?

---

### Post by fjgaude on 2009-05-14
Well, normally use this:

```
sudo fsck /dev/sd[nn]
```

The usually fixes what might be wrong with a drive.

---

### Post by andyrowe on 2009-05-14
sudo fsck /dev/sdb2 returns
fsck.mdraid: not found
Error 2 while executing fsck.mdraid for /dev/sdb2
 
looks like it's trying to find a multi disc array
the drive (RAID) is in use. MDADM has already removed the bad H/D and marked it as a faulty spare. How can I check a single disc? Will it repair bad partitions. If a partition is marked as bad, will the drive (now with slightly less capacity) still be able to be part of this RAID?

---

### Post by Lampi on 2009-05-14
@andyrowe: I strongly recommend to check the S.M.A.R.T. data first! If the drive is showing symptoms of malfunction I would NOT reassign it to your working array. You risk corrupting your data on the healthy drive(s) if something goes wrong.

Could you post here the output of smartctl -a /dev/<devciename> ?

If S.M.A.R.T Data turns out fine you should not correct errors using fsck on a single drive, but sync the whole partition from the intact raid device to the Seagate in question (Make sure it syncs the right way!!) Eventually you can run a filecheck AFTER the sync is complete on the raid array to make sure you filesystem is still intact.

Concerning corrupted sectors on your Seagate drive: the drive has a built-in logic to mark corrupted sectors on his own and reallocate them to a pool of unused sectors.

But I really would have a look at your SMART data - if a disc starts showing symptoms of malfunction (e.g. PREFAIL attributes rise fast, reallocated sector start showing up) I usually replace it right away. It's not that expensive anymore to risk your data.

---

### Post by andyrowe on 2009-05-14
I had to install the smart tools. When I run the command you specified, some of the info scrolls off the screen. The first line that is visible at the top of the screen is:
commands leading to the command that caused the error were:
CR FR SC SN CL CH DH DC  Powered_Up_Time Command/Frature_Name
ea  00 00 00  00  00 a0  00   00:01:06.803        FLUSH CACHE EXIT
and so on. Do you need more? How can I see the whole results?

---

### Post by Lampi on 2009-05-14
```
sudo smartctl -a /dev/<devicename> | tee ~/smartdata.txt
```
This will display it on terminal and write it in a file called smartdata.txt in your home directory. Just give me the attribute values.

---

### Post by andyrowe on 2009-05-14
oh boy
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less then 24 hours
 
further down the file....
Vendor Specific SMART Attributes with thresholds:
ATTRIBUTE_NAME           VALUE       WORST       THRESH
Raw_Read_Error_Rate     109           099             006
Spin_Up_Time                 095           095             000
Start_Stop_Count            100           100             020
Reallocated_Sector_Ct     001           001             036
Seek_Error_Rate             064           060             030
 
and on and on. If you need more of them, I'll post
obviously the drive is toast

---

### Post by Lampi on 2009-05-14
I'm sorry to hear that .... this means one or more of the critical S.M.A.R.T attributes have failed, so this drive IS toast.

Since I might be using the very same Baracuda type: could you attach the file anyway? After Seagate had to call back many drives of the Baracuda series last February I still feel like sitting on nails with this drive ... he's doing fine so far, but I'd like to compare your values with mine.

The drive was in a raid array, right? So you have a working copy on the other drive. You are lucky! All you can do now is erase the data on this Seagate Baracuda and then return it to the manufacturer. I hope you still can profit from warranty.

---

### Post by andyrowe on 2009-05-14
> **Lampi said:**
> I'm sorry to hear that .... this means one or more of the critical S.M.A.R.T attributes have failed, so this drive IS toast.
yeah... that was only the first 4-5 attributes, there were like 15-20 more
 
> **Lampi said:**
> Since I might be using the very same Baracuda type: could you attach the file anyway? After Seagate had to call back many drives of the Baracuda series last February I still feel like sitting on nails with this drive ... he's doing fine so far, but I'd like to compare your values with mine.
you know, I was shocked how cheap it was, now I know why. Kinda sucks, you assume you buy something and it's going to be relativly good quality. I always thought seagate was good stuff
I would be happy to send you the file if you'll tell me how to move the file from my home directory to the one I shared on the network.

---

### Post by Lampi on 2009-05-14
> **andyrowe said:**
> you know, I was shocked how cheap it was, now I know why. Kinda sucks, you assume you buy something and it's going to be relativly good quality. I always thought seagate was good stuff
I still think they are not worse than other drive manufacturers, I don't recall other issues with seagate.

> **andyrowe said:**
> I would be happy to send you the file if you'll tell me how to move the file from my home directory to the one I shared on the network.

You can create a tar archive like this:
```
tar -cvzf ~/smart.tar ~/smartdata.txt
```
This will place it in your home folder again - then you click on the "Manage Attachments" button bellow - best is you send it as a privat message to me (Or is anybody else interested in that?)

---

### Post by fjgaude on 2009-05-14
To check a drive that's been in an array, you have to stop the array, unmount it and then zero the superblock:

```
sudo mdadm --zero-superblock /dev/sdb2
```

Then you likely can use fdck on the drive. Just for future reference! <smile>

---

### Post by sloggerkhan on 2009-05-14
I always do a smart check first thing on getting new hard drives.
These days there seem to be decent odds that maybe that if you buy a set of hard disks there will be one that has some kind of issue out of the box.

I built a 4 disk mdadm RAID V array of seagate drives this spring and one of them failed smart tests out of the box. Had to send it back for replacement.

It's extra lame to start setting stuff up and then find out one of your drives is toast in the middle of everything.

My experience is that drives which fail SMART tests out of the box are really dead or close to it and shouldn't be used, but if your 3 - 5 year old drive starts failing smart, it's often got a decent stretch of use left even though it is on the way out.

---

### Post by fjgaude on 2009-05-14
I had six Seagate drives be bad, one right after another... quality control may be an issue. In my four-drive raid5, when one drive goes, I replace them all and start over. Really, all drives in such of an array get equal use, so...

Also use triple backups on two other machines... better safe than sorry!

---

### Post by sloggerkhan on 2009-05-14
> **fjgaude said:**
> I had six Seagate drives be bad, one right after another... quality control may be an issue. In my four-drive raid5, when one drive goes, I replace them all and start over. Really, all drives in such of an array get equal use, so...

Also use triple backups on two other machines... better safe than sorry!

That sounds rather expensive... you must be running some sort of critical system to warrant that. 

I believe smart test results, myself. If all my drives but one pass smart, then I believe that just that one is danger of failing. Now if a drive goes bad, and I test all 4 and the rest also show smart errors, then I think about replacing them all.

---

### Post by Lampi on 2009-05-14
@fjgaude: why should he zero-size super block? this drive is clearly over the edge. So there clearly is one thing left to do: return it to the seller, mabye try to erase the personal data first.

zero-size superblock would only make sense if the drive was okay - but it's obvious this drive is seriously damaged, isn't it?

---

### Post by fjgaude on 2009-05-15
The comment regarding superblock zeroing was for future reference, as stated.

Drives are low-cost compared to what they were just five years or less ago. I recall that 8 and 16 drives of 36GB each was required to get the array size up. All that has changed with the huge drives out these days, all for less than $129.00 each. I only use single platter drives for what I need. Right now that is 320GB. <smile>

---

