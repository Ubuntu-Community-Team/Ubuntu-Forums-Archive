---
title: "New RAID.  Recommended Maintenance &amp; Back-ups"
date: 2011-02-22
forum: Server Platforms
---

### Post by mn_voyageur on 2011-02-22
I decided to create a file server for my family.  I have set up a RAID 6 (4 disk) array.  

My thoughts were to back up the array to a hard drive monthly.  Store the drive in a WiebeTech Drivebox, off site, in a "fire proof" box.  (The kind for papers sold at Staples or Office Depot.  

After a year, I would have 12 back-ups.  I would then overwrite the previous hard drive.  (ie HDD from March 2011 would be overwritten on March 2012.)

Additionally, I was wondering if there was recommended maintenance to verify the array is working properly.  

Right now, I am moving data to the array so quickly that I am backing up every few days between three hard drives.  (Back-up #4 was written to Drive #1 after Drive #1 was reformatted.)  I am aware that I could use rsync.  (Which I currently use for backing up my portable USB HDD to the RAID array.)  I am just a little (or maybe a lot) paranoid that I will lose files.

My worst nightmare would be that the array was failing, files were being lost, and I was none the wiser.

So, I am here, seeking advise from those who have walked this path.  

I appreciate help.

MarkN

---

### Post by rubylaser on 2011-02-22
The best way to verify that your array is working properly is to setup emailing you if anything goes wrong.  Also, set up smartmontools to email you if any disks in your array have problems. I don't know how well a hard drive would last in a fireproof safe.  Those are designed to prevent paper from combusting (451 degrees F).  I don't think I'd want to trust a drive that's been through heat like that :)

Have you considered using, and offsite backup via rsync to a datacenter or one of the many inexpensive backup solutions like Spideroak or Jungledisk?  That's just another option to make sure your data is backed / versioned in multiple locations. These are not as cheap as the self managed backup solution, but is much easier to manage imo.

---

