---
title: "mdadm raid5"
date: 2011-10-17
forum: Server Platforms
---

### Post by jhayes on 2011-10-17
i am currently building a little linux box to act as a nas. considering ubuntu server (have had a good amount of experience with similar setup in the past) and freenas. 
main question, if i setup a 5 drive raid5 array now, can i later add more drives and expand the array/partition size?
is this the best way to go?
should i wait till i have all of the drives before i create the array?
does the raid creation during the server setup actually work? (i did not have success getting desktop 10.04 to create the array during setup.)

and is it possible, advisable to boot and run from a 16gb flash drive for the primary os?

---

### Post by rubylaser on 2011-10-17
Yes, mdadm supports growing / expansion down the line.  The main problem you'll run into is if you ever want to grow your filesystem beyond 16TB.  If you do this, you won't currently be able to use EXT4 as it doesn't support > 16 TB.

I always to the RAID setup after the fact, but the one in the setup works fine too.

Finally, you can boot / run from a flash drive, but you'd want to set it up to minimize writes to the drive, so it doesn't die prematurely.  Also, it will be slower than a traditional hard drive.

---

### Post by jhayes on 2011-12-04
OK, first thanks for the response, exactly what i wanted to hear. i assume i also would be able to use gpt tools to grow the partition without to much trouble. would there be any advantages to running the server version then adding in the gui desktop, vs. just running the desktop version? note: home use only. if it were to be somewhere in a business type setting, the answer is easy. but i would also like it to hook up to the tv (tv has vga connection) and act as a media player. possibly with xbmc front-end. 16Tb is not such a bad thing for a cap, i only have 8 2TB drives right now anyway (take space from 1 for raid5 and get ~13Tb or so). also, any suggestions on ways to backup ~8Tb of data? LTO5 is prohibitively expensive. backup to dvd discs is just silly considering the sheer numbers needed. i think the only practical home user way is disk-to-disk backup.

---

### Post by rubylaser on 2011-12-04
1. To resize an EXT4 partition, you'd use e2fsprogs.  To resize an XFS partition you'd use xfs_growfs.
2. If you want the Gnome Desktop, you should just use Ubuntu Desktop instead of the server install.
3. Almost anyone on XBMC's forum is going to tell you it's better to have a separate file server from your HTPC.  8 drives + fans  make noise and you'll hear it when watching movies.  Personally, I have (2) Shuttle XS35GTs and (1) Revo 3700 that I run Openelec on with a shared MySQL database and thumbnails for my XBMC boxes.  This is a very nice way to add media players in any room in your home.
4. For home use disk to disk backup on that scale is the only affordable way to do it.

---

### Post by darkod on 2011-12-04
One point not mentioned so far: For desktop system with RAID use the alternate install cd/image, not the desktop cd. It installs the same desktop system but it has built in support for LVM and/or RAID during the install. Really makes things "out of the box".

Maybe that's the reason your try with the desktop cd wasn't successful. I guess you should have no problems with the alternate to set up a software raid during the OS install.

I just did something similar but on a much smaller scale. Two disks in RAID1 using ubuntu server. I decided I don't need a GUI and wanted to get more involved with the server version anyway. Plus my TV supports DLNA and picks up the Twonky I installed on the server without any issue. So my LAN is passing the data to the TV, no need for VGA connections.

---

