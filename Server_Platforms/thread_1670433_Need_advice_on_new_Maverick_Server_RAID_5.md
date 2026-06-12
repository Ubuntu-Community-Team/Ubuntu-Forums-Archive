---
title: "Need advice on new Maverick Server RAID 5"
date: 2011-01-18
forum: Server Platforms
---

### Post by hogfan on 2011-01-18
I am building a server I will use for storing media that I will stream across my LAN to to my XBMC HTPC.  I also plan to use this server as a web server to run Gallery and possibly Wordpress.   However the main purpose is for media storage with redundancy.

I will be installing the 64-bit version of Ubuntu Maverick on a smaller hard drive in the system.  

The Media will be stored on a mdadm software RAID5 array.  I currently have 3 x 2 TB drives that I will be using for the array giving me 4 TB of storage for the media.  I currently have all of my media on a 2 TB HDD (same make an model as the other drives I'm using to build the RAID5).  The plan is to build the RAID5 Array with the 3 new  drives.  Then I will back up all of my media  that is on the existing 2 TB drive to another location.  I then want to add the newly available 2 TB drive to my RAID5 array as a Hot Spare.

1.) Will I be able to add a hot spare to the RAID after initial setup?

2.) In the future I can easily install additional disks and simply grow the array to increase storage, correct?

3.) The RAID5 array will be setup as a single EXT4 partition.  Should I use LVM for my setup?

4.) Since I will be installing Wordpress, Gallery, etc.  (which will require MYSQL, PHP, etc.), I was thinking of creating a directory  on the RAID5 to store my Galley MYSQL database.  I this a good approach?

Basically this thing is going to be a media file server and possibly basic webserver with very low traffic.   I plan to use Gallery for storing all of my pictures while making them viewable via  the web at the same time.

I am using RAID5 for it's redundancy only (not concerned about performance).  I know this is not a substitute for backups, but it's much better than the data sitting on the single 2 TB drive. I plan to set up email notifications for monitoring the array.

Any additional suggestions or recommendations for my setup? Thanks for any suggestions, input, and answers to any of the questions above.

-hogfan

---

### Post by Vegan on 2011-01-18
LVM can be used with supported controllers.

---

### Post by hogfan on 2011-01-18
After doing some reading on LVM, I don't see a reason that I would need to implement it in my setup.  I will only be dealing with one partition on a RAID5 array, so I don't see the need for the partition resizing functionality.  When I run out of space I will simply add HDDs to the array and grow the array to gain more space......or would I need LVM to grow the existing partion on the RAID5 to gain access to the additional storage in the RAID5 array?

-hogfan

---

### Post by hogfan on 2011-01-19
Nobody has any suggestions on this setup?

-hogfan

---

### Post by hogfan on 2011-01-19
Nobody has any suggestions on this setup?

-hogfan

---

