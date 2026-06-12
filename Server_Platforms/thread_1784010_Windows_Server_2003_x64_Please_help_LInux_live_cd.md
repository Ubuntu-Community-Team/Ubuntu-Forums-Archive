---
title: "Windows Server 2003 x64 Please help LInux live cd"
date: 2011-06-16
forum: Server Platforms
---

### Post by rigel4 on 2011-06-16
Hi 
I recently got  a new job for an Automation Company, and it is generally a good job.
However i am under pressure with lots of learning Plc things as well as being there IT man.

A Dell Server T100 with Raid 0 (i didn't build or Install it), has been brought back from a feed mill,, with the operating system unable to boot.

The company needs the data from the server, so i tried to boot it from a suse 32 bit live cd, that failed.
Then I tried the latest version of Debian , that booted bit was unable to see the drives.

By the way i checked in the raid array controller config and both disks are healthy.

So what i was wondering was, if i make a a x64 ubuntu cd will this allow me to get at the data and move to an external hard disk. 
I urgently need advice on this as my boss is getting impatient with me.

Thank you.

---

### Post by sanderd17 on 2011-06-16
Can't you get the drives out the computer and use another computer (without raid) to read them?

---

### Post by rigel4 on 2011-06-16
Never thought of that , as i always thought once raided, you needed the raid controller to see the disks as a logical drive.
So you are saying i could grab the disks and put both of them as slaved drives and see the data that way?
I hope you are right as this would be the easiest answer.

---

### Post by arrrghhh on 2011-06-16
> **rigel4 said:**
> Never thought of that , as i always thought once raided, you needed the raid controller to see the disks as a logical drive.
So you are saying i could grab the disks and put both of them as slaved drives and see the data that way?
I hope you are right as this would be the easiest answer.

Assuming there's no striping (which there isn't in RAID1) then you should be fine to pull out the drives.  RAID5/6 is where this becomes an issue IIRC.

---

### Post by rigel4 on 2011-06-16
> **arrrghhh said:**
> Assuming there's no striping (which there isn't in RAID1) then you should be fine to pull out the drives.  RAID5/6 is where this becomes an issue IIRC.


That's the problem though, who ever built this server, stupidly built it with Raid 0 NOT Raid 1 which would 
have been the sensible choice.

I am left with Raid 0 not booting and struggling to get at the data.

---

### Post by arrrghhh on 2011-06-16
> **rigel4 said:**
> That's the problem though, who ever built this server, stupidly built it with Raid 0 NOT Raid 1 which would 
have been the sensible choice.

I am left with Raid 0 not booting and struggling to get at the data.

RAID 0 is pointless... but I think there is block-level striping.  Any failure in a RAID 0 array will cause a failure of the entire array.

Is this hardware or software RAID?  If it's hardware RAID, should be no problem.  You shouldn't need 64-bit anything either, just get a standard 32-bit Ubuntu Desktop LiveCD and see what happens.  Might have to do some fanegaling to get the drives to mount, but it *should* work.  Again, this is for hardware RAID.  If it was a software RAID setup... I'm not sure then.  I think mdadm can take over software RAID setups from Windows, but I'm no expert on that topic.

Edit - long story short, the only way you'll be able to get that data is to rebuild that array.  You will not be able to get at the data without rebuilding the array, because of the striping.  RAID 0 really is pointless, if anything it increases the likelihood of data loss.

---

### Post by StrayEddy on 2011-06-16
Try puppy linux, fast, easy, no problem.

---

### Post by rigel4 on 2011-06-16
> **arrrghhh said:**
> RAID 0 is pointless... but I think there is block-level striping.  Any failure in a RAID 0 array will cause a failure of the entire array.

Is this hardware or software RAID?  If it's hardware RAID, should be no problem.  You shouldn't need 64-bit anything either, just get a standard 32-bit Ubuntu Desktop LiveCD and see what happens.  Might have to do some fanegaling to get the drives to mount, but it *should* work.  Again, this is for hardware RAID.  If it was a software RAID setup... I'm not sure then.  I think mdadm can take over software RAID setups from Windows, but I'm no expert on that topic.

Edit - long story short, the only way you'll be able to get that data is to rebuild that array.  You will not be able to get at the data without rebuilding the array, because of the striping.  RAID 0 really is pointless, if anything it increases the likelihood of data loss.

It is definitely  Hardware RAID, but i have no idea how to rebuild the array , as reinstalling the operating system will kill the data.
I think the error message says something like : ntoskrnl.exe is missing or corrupt.

Edit: To recap then, I think the array is undamaged, and 32 bit ubuntu should be able to see the data on the logical volume.

I thank you for your Input.

---

### Post by rigel4 on 2011-06-16
> **StrayEddy said:**
> Try puppy linux, fast, easy, no problem.

Thanks I'll download and try it.

---

### Post by crispy_420 on 2011-06-18
RAID 0 on a production server?! I hope it wasn't a critical asset because the odds are against recovery. If one drive is gone call it a loss, may as well be a single drive system.

Have you been able to perform OEM drive manufacturers diagnostics to see if it is hardware failure. I know Dell has diagnostic utilities built into BIOS, is that the case on the server? Does the RAID bios properly recognize the drives as present?

All I have to say is at least you walked into this. Hopefully they had a good backup plan off that array so you can rebuild the server right.

---

