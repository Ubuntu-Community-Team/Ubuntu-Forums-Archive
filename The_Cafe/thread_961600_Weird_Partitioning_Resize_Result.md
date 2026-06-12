---
title: "Weird Partitioning Resize Result"
date: 2008-10-28
forum: The Cafe
---

### Post by Vince4Amy on 2008-10-28
I have resized a Windows Drive using Mandriva (Posted here as I doubt it's distribution specific). It seemed to have successfully carried out the resize however when I tried to install Mandriva after this I went to install Mandriva into the free space on the drive and it reported that there was none. 

I rebooted into Windows and chkdisk ran as the partition had been resized. My computer recognised that the drive was now 17GB instead of 37GB that it was before.

I went into disk management and there was no free space after the 17GB which Windows was using and it was reporting that the Windows drive was still 37GB. Even though My Computer displayed the drive as 17GB

Here is a screenshot of hard disk manager: 

[[IMG]http://img217.imageshack.us/img217/5030/hddmanagersq5.th.png[/IMG]](http://img217.imageshack.us/my.php?image=hddmanagersq5.png)[[IMG]http://img217.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by GrouchoMarx on 2008-10-29
It looks like the NTFS filesystem was resized, without actually resizing the partition itself. To retrieve the missing space you may need to resize the partition to match the size of the filesystem. You should be very careful when doing this. Editing the partition tables is not rocket science, but if you shrink it too much you might wipe your data.

---

### Post by Vince4Amy on 2008-10-29
I managed to sort it using gparted.

---

