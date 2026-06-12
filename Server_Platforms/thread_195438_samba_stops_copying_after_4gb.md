---
title: "samba stops copying after 4gb"
date: 2006-06-12
forum: Server Platforms
---

### Post by Thomas Bowie on 2006-06-12
I am having a very irritating problem with copying directories over 4gb to my "new" (read, mostly recycled) backup server, which is running Dapper and samba.

The copying process appears to work fine, but after 4gb of data has been transferred, the process seems to die and i get a copy error.  Restarting the copy obviously results in the same problem. 

The problem occurs while transferring over 4gb of files from all of my "client" machines and all operating systems (Breezy,Win98 and WinXP).

Apart from this, samba seems to be working fine, and the share can be "seen", read and written to from all machines.

An edited /etc/samba/smb.conf is attached.

Tom.

---

### Post by mat1t on 2006-06-13
Fat32 doesn't support files greater than 4gb, so that would explain why it doesn't work on Win98. Is your WinXP computer formatted with Fat32 or NTFS?

Not sure why it would be doing it on Breezy though.

---

### Post by ScatterBrain on 2006-06-13
I'm not sure I understand...Are you having problems copying **individual files** larger than 4GB or when the** total amount of data copied - from many files - totals more than 4GB**?

I've never had a problem with Samba sending large amounts of data, until I tried to move a copy of my Exchange 5.5 backup file - which was 4.5GB by itself.   When the Exchange file was copied, it was truncated to 2GB.  The rest of the data - in excess of 90GB, but in thousands of files, copied fine.

I ended up pushing the data from the Windows box to a Samba share on the Linux box and that worked.

---

### Post by Thomas Bowie on 2006-06-13
Ok, let me explain some things:

--On my main "client" machine, an AMD Athlon XP-2800 w/1.25gb ram, the "shared" partition is 170gb, formatted fat32.  I did this in order to have read/write access to all my music/videos, on one partition, from WinXP and Ubuntu "Breezy" on the same machine.   The WinXP partition is ntfs, as normal, and the Breezy install is on an ext3 partition.  

--My "backup" server is an old AMD K6-2 500mhz with a 4.2gb hard disk, ext3, which has Ubuntu "Dapper" and a 500mb swap partition.  I have recently purchased a 120gb hard disk, which is the "backup" and formatted as ext3.

I have been trying to copy from my "client" backup partition (fat32) to my "backup" server, and i get a transfer error after transferring over 4gb of data.  This consists of individual mp3/ogg music files of no more than 6mb each, NOT one large file over 4gb.  

Do i need to back-up files to dvd, and re-format my fat32 partition as ext3, because of the 4gb limit already mentioned in the replies?

If so, I would really appreciate it if people could suggest a way to HAVE READ/WRITE ACCESS TO THE PARTITION FROM WINDOWS XP.  I do not use Windows often, but when i do, i really need more than just read-only access.

Tom

---

### Post by mat1t on 2006-06-14
If that's the case then my post is irrelevant. The 4gb limit only applies to files larger than 4gb, not folders.

It sounds like a problem with samba, but unfortunately it's out of my realm now.

Good luck

---

### Post by LordHunter317 on 2006-06-14
I'm not exactly sure why it is failing.  Looking at the logs owuld be a good idea on an aborted transfer.

---

