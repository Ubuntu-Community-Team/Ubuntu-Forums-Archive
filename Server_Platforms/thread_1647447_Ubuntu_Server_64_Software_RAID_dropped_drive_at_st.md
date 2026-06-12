---
title: "Ubuntu Server 64 Software RAID dropped drive at start up."
date: 2010-12-17
forum: Server Platforms
---

### Post by Coder68 on 2010-12-17
I have 5 2 TB drives in software RAID 5 that I created in Webmin.  Every now and again when I start my system one of these drives does not "come up" and the RAID 5 is not active. It is still mounted as I can get to and see the data. Webmin shows it as not active and the drive space shows it is shy of 1 drive. There is no indication of which drive is missing! 

I tried mdadm -D /dev/md1 to look at which drive was not present, but it gave me an error of something like "md1 is not active so I can't look at it"

Stopping md1 and rebooting usually helps bring it back to life. 

I think it is the same drive that keeps falling out.  I would like to replace this drive while I can still get a new replacement from Newegg and not a refurb from Samsung.

By polling the drives with SMART, I know which drive is in which bay - by serial number and by" device a" "device b", etc. (I have patched my firmware to fix the issue with the HD204UI 2TB drives.) I just don't know how to tell that serial number xyz or "device x" is the one that I need to take a look at. 

How do I tell what drive has failed?

Thanks in advance!

Coder68

---

### Post by SaturnusDJ on 2010-12-17
Find out what /dev/sd* drive keeps failing and then do
```
hdparm -i /dev/sd*
```

It will tell you a SerialNo. This SerialNo should also be printed at the drive physically.

---

### Post by Coder68 on 2010-12-17
That is the issue, I do not know how to figure out which drive keeps dropping out. I know which SN is in which bay, so if I can figure out it is sdg for example, I know it is the drive in bay 4.

How do I tell if it is sda or sdb etc?

C68

---

### Post by SaturnusDJ on 2010-12-18
What does
```
cat /proc/mdstat
```
has to say?

---

### Post by Coder68 on 2010-12-19
When the drive drops, I can't pull info from mdstat since it says it is inactive.

C68

---

### Post by SaturnusDJ on 2010-12-20
Ok nasty. I don't think it is the best option but the only thing I can think of now is: unplugging each drive until you got a clean boot. Then you have the 'bad one' disconnected.

Don't you get more information at boot? Logs? There must be a kinds of error I guess.

---

### Post by Coder68 on 2010-12-20
You would think that Linux would tell you what drive has failed. How am I to know?? What if I had 30 drives in there? I must be missing something as there has got to be a way for software RAID to tell you what drive failed. 

RAID Guru's, what is your take on this?

C68

---

### Post by SaturnusDJ on 2010-12-20
Did you search for logs?

Other option: Boot to Live CD and assemble the array. This Live CD will also allow you to read S.M.A.R.T. data via Disk Utility (GUI).

---

### Post by Coder68 on 2010-12-20
Yes, I did search the logs, but I did not find anything.  I bet I am not looking in the correct log though.

C68

---

### Post by doogy2004 on 2010-12-21
What is the output of the following commands?
replace /dev/md0 with the path of your raid device.
```
sudo mdadm --detail /dev/md0
cat /proc/mdstat
```

---

