---
title: "Hotswap HD replacement?"
date: 2009-02-10
forum: Server Platforms
---

### Post by quad3d@work on 2009-02-10
So last week one of my PE2950s borked out some I/O errors on sdb (SAS 300GB)... mdadm automatically set sdb faulty. This is RAID5 with 4 drives.

(Bay 0 and 5 is PERC HW RAID)

Got an warning e-mail from mdadm, logged onto the server and removed sdb from md0. Since this is a production Xen, I cannot shut the server down and replace the drive.

My understanding is those SAS are all hot-swappable right? So I have bunch SAS 300GB laying around. I just yanked out sdb and insert a new drive in there.

I watched the light goes back to green. dmesg it, nothing. Try to add sdb back into md0 for rebuild, failed. Tried to dd the drive, works. I pull the drive out again, dd it again... surely it said it writes stuff to it???

At this point it's obviously to me that simply yanking out and reinsert a new drive **does not** work.

I scheduled a downtime this past weekend. Bounce the server, PERC warns about a foreign drive profile. I goes into controller config, imported the profile, restart.

** BAM!** Linux came back up with sdb recognized, so I re-added back to md0. And all was swell, it rebuilt the RAID5.

Sooo... my understanding is... if it is a regular RAID controller, you can't do hot-swappable. Unless it's a HBA. Am I right?

If it's regular RAID controller (non-HBA), and I did HW RAID and OSMA kicks out a warning. Am I able to replace the drive without shutting down the OS?

---

