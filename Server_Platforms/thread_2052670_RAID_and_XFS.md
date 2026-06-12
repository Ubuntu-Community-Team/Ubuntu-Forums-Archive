---
title: "RAID and XFS"
date: 2012-09-03
forum: Server Platforms
---

### Post by jlp_engineer on 2012-09-03
I have four disks of the same capacity that came from an old NAS box.  I don't know if there is any data on them and the NAS no longer functions.  The disks test OK and partitions on them.  I have very little information on the NAS, but I know it was running IPStor Express from FalconStor, and I think it was using XFS for the data partition.  Also, when the OS for the NAS was working, I remember that the setup for a share had a 2TB limit, but you could start at like 200GB and then grow it later to a larger size, up to the capacity of the RAID array. 

Question, how do I mount these disks in Ubuntu (or any other OS for that matter) and see if there is any data on the disks.  I believe the disks were setup as RAID 5, with four disks, and OS for the NAS is circa 2006 or 2007.

Am I looking at LVM, or MDADM.  Does the ability to grow the share correlate to a partition, or was this something else proprietary used by FalconStor?

Thanks for any information anyone can provide.

---

### Post by TheFu on 2012-09-03
Based on this [http://www.falconstor.com/products/network-storage-server/specifications](http://www.falconstor.com/products/network-storage-server/specifications) , I doubt you will access any of the data on the disks.  You don't have the hardware so there is no way to know what the underlying data structure really is.  The disks could have been iSCSI targets, AoE, or NAS. They could have been used from any OS or they could have been a remote receiver of DR data in some tape-optimized format. The ability to grow storage could have been internal or part of the OS accessing the storage.

You can't mount these disks and get data back in Linux. You need the FalconStor hardware and software.

I'm not certain that I'd even trust disks this old, definitely not for primary data, perhaps for backup data only. Heck, we have disks spinning in an array from 2007 and are actively purchasing hardware to avoid possible outages.

Sorry, I'm not much help.  Can you login to the FalconStor customer portal and read the FAQ and Knowledgebase for answers?

---

### Post by jlp_engineer on 2012-09-04
The FalconStor IPStor Express software was a special version of their software designed to run on generic Intel IOP321 hardware (such as the Sabio CM4).  If I scan the disks under Ubuntu using UFS Explorer, I get segments that seem to be EXT3 and XFS file systems, but I cannot get complete segments of data or whole files, only fragments.  That may have something to do with UFS Explorer detecting 700+ GB partitions where there is only a 250 GB partition.  It detects ~250GB partitions on two of the disks, and 700+GB partitions on the other two.  Clearly the 700+GB that it is detecting has something to do with software RAID that the FalconStor software constructed on the disks.  Or maybe I don't have UFS setup to scan the disks correctly.  Normally it is a Left-Dynamic parity with 64K chunks, but maybe I am using the wrong settings for these disks.  But I don't know what FalconStor would have set their software for.

But if you feel that FalconStor has done something to intentionally prevent the possible reconstruction of the RAID 5 array, then maybe it is time to give up now :-(

---

### Post by SeijiSensei on 2012-09-04
In [RAID5]("http://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_5") no individual drive has a complete copy of any file.  The files are striped across the data disks with one drive devoted to parity checks.  That's just the way RAID5 works.  You can only retrieve the files if you can reconstruct the array.

---

