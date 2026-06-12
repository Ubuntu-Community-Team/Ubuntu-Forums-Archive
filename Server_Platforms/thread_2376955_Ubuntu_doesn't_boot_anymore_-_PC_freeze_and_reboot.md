---
title: "Ubuntu doesn't boot anymore - PC freeze and reboot after kernel panic"
date: 2017-11-07
forum: Server Platforms
---

### Post by zoobie on 2017-11-07
Hi Everyone,

I'm seeking actively some help, my DIY NAS (4 HDD with Raid 5 and Raid 1) after this weekend doesn't boot anymore. The PC either freeze or reboot but even with the recovery mode it is not working. (It's seems that potentially there are some issue with the Raid disks generating kernel panic error.

In order to seek some help I have used the application Ubuntu Boot-repair in order to log the issue.

Please find the link of the boot-repair log:

[http://paste.ubuntu.com/25913248/](http://paste.ubuntu.com/25913248/)

Thanking you in advance for any direction you can provide to help to sort out this problem.

Regards,

Mouche15

---

### Post by oldfred on 2017-11-07
Do not run any auto-fix with Boot-Repair when you have multiple drives. It just installs one grub to all drives.
Use advanced mode and select an install and the drive you want to have as default boot.

Boot-Repair has these:
 SecureBoot maybe enabled.
GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again. 

Make sure you have CSM/Legacy/BIOS set in UEFI, if UEFI hardware.
And with gpt drives you need a bios_grub partition. Grub does not normally install correctly without it, so not sure how you booted before?
Create that before re-installing grub to MBR.

---

### Post by zoobie on 2017-11-08
Thanks Oldfred

I have created a new unformated partition under /dev/sda9 and added a boot-grub flag and then in boot-repair I have selected a GRUB installation on /dev/sda

I have the following log from boot-repair:

[http://paste.ubtunu.com/25920671/](http://paste.ubtunu.com/25920671/)

Unfortunately when I reboot I still have the PC that freeze with no ability to take control on the ubuntu logging screen.

I have even launch a recovery mode and I'm ending with this fatal kernel error:

[URL="http://pix.toile-libre.org/?img=1510179831.jpg"][IMG]http://pix.toile-libre.org/upload/img/1510179831.jpg[/IMG]

Zoobie
[/URL]

---

### Post by oldfred on 2017-11-08
Link not working.

Did you also check to uninstall grub & to install latest kernel as part of grub reinstall.

---

### Post by zoobie on 2017-11-09
Sorry here is the correct link

[http://paste.ubuntu.com/25920671/](http://paste.ubuntu.com/25920671/)

Yes I have uninstall grub, however I'm not sure that I have ticked to install latest kernel (I think I have not done it - let me retry tonight)

Thanks

mouche15

---

### Post by oldfred on 2017-11-09
I do not see anything else out of order.
If RAID issue I can move thread to server sub-forum where those who know RAID can help.

Checked UUIDs in fstab as sometimes that is an issue, if not valid, but cannot see anything.
But you did change two entries from UUID to device.

I have had issues with device as on my system I skipped a port when plugging drives into motherboard. And if I reboot with flash drive plugged in my device enumeration changes in grub - hd1 becomes hd2, but sdb is still sdb.

---

### Post by zoobie on 2017-11-09
Clearly there is something with the different disks:

[[img]http://pix.toile-libre.org/upload/img/1510262606.jpg[/img]](http://pix.toile-libre.org/?img=1510262606.jpg)

I have commented all the partitions from the fstab file except for /, /tmp, /home and swap

It seems that some partitions have issue with their structure (I have quickly seen that when the live session was logging.

Another odd thing is the fact that I don't have anymore the array devices (related to my raid disks, i.e. md0, md1, md2 and md3) under the /dev folder.

definitely there is something wrong but I don't know I can fix it.

---

### Post by oldfred on 2017-11-09
Moved to Server sub-forum as may be RAID issue.

---

