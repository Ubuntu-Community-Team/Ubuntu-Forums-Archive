---
title: "Unable to Mount the Disk"
date: 2020-02-25
forum: Ubuntu/Debian BASED
---

### Post by vinothsankar on 2020-02-25
Dears

We are using Ubuntu 16.04 OS in our desktop.
We are unable to mount the disk which has valid data.

I need to recover the data and mount the disk. The Data is more important to us. Your help is highly appreciable. 

ntfs_mapping_pairs_decompress() failed: Input/output error
Failed to load $MFT: Input/output error
Failed to mount '/dev/sdb2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation

---

### Post by yancek on 2020-02-25
The information you posted indicates the drive you are referring to is using the proprietary microsoft ntfs filesystem.  Is there some reason why you are using that if you have Ubuntu installed on your Desktop?  Have you tried the suggestions you posted above when you got the error message?  Could be a problem with RAID (if you have it?) or having had the drive attached to a windows computer which was hibernated.  If you still have problems after trying the suggestion to run chkdskk from windows post back with specific results of that command.

---

