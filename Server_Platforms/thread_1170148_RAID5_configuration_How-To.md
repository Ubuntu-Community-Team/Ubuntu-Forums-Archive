---
title: "RAID5 configuration How-To"
date: 2009-05-25
forum: Server Platforms
---

### Post by R.Bucky on 2009-05-25
My new web server is in the mail. It has 3-250GB HD, an Intel Xeon 3050, 4GB RAM, and an embedded four (4) disk SATA controller with SATA RAID 0/1/5/10 capability. I will be installing RAID5. Can someone share links or their knowledge with this installation?

I have configured RAID1 on another box. Here is my interpretation of the RAID5 install.

HD1 - /boot 200MB RAID1
      /webserver 'remaining space' RAID5
      / 10GB RAID5
      /swap 2GB swap

HD2 - / RAID5

HD3 - / RAID5
     this will be the hot swap

Do I need a swap partition on HD2 and the hot swap? Any help would be appreciated.

---

### Post by Vegan on 2009-05-26
I suggesting you avoid software RAID as its not very reliable. If you have a controller card, those are safer. Still even with a hardware RAID card, I suggest a separate boot disk so if the OS fails the RAID is safe (more or less).

---

