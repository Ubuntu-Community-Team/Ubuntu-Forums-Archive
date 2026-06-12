---
title: "How should I partition my server drive?"
date: 2009-06-10
forum: Server Platforms
---

### Post by bryceowen on 2009-06-10
I'm setting up a small test LAMP server and was wondering how folks partition their drives for production use. I have a 40GB drive that I have two partitions on (39GB for / and 1GB for swap) and, as far as testing purposes, this configuration works fine. However, I am reaching the point where I'm ready to setup a semi-live server and was wondering two things; What benefits/drawbacks is there to partitioning the drive and what would be a good partition scheme for the drive?

As I said, it will be a basic LAMP server (with the addition of webmin) for an intranet site, so there's no need to worry about setting up ftp users or any users other than myself (for admin purposes).

Most websites I've looked at suggest, at the very least, setting up a 100MB /boot partition and some go so far as to suggest separate partitions for /tmp, /usr, and /etc. I understand that reading/writing to the MySQL database could cause fragmentation and, as a result, should be on its own partition, but I'm a little foggy as to how to set something like that up.

I'm already familiar with using the various partitioning tools available, so I don't need a 'walkthru', but rather just advice.

---

### Post by lensman3 on 2009-06-11
Put the swap file and the busiest data partitions in the middle of the drive.  Theoretically, seeks for writing or reading would be minimized when the disk head would have to go to or come from the outer edges of the disk.

Unfortunately, I don't know how you would prove the above recommendation with the amount of on-disk "smarts" that a drive has.  The "smarts" may nullify any middle of the disk data.  Also the Linux disk drivers use a "modified elevator" method to retrieve data, which again may nullify any middle of the disk data.

Anyway, putting the busiest data in the middle of the disk makes logical sense!  Hope this helps.

---

### Post by Ed_Ziffel on 2009-06-11
put the folders in order boot user root swap var home etc.  That will put the most used files on the middle of the drive.  a 40 gig is drive is probably years old no doubt, an ide (with the flat gray 40 or 80 pin connector cable) so that will help some but its not magichttp://ubuntuforums.org/images/smilies/icon_wink.gif

---

