---
title: "My External HDD is FAT32. Ubuntu agrees but XP says 'No yuo! It's NTFS'.. What gives?"
date: 2008-08-11
forum: Server Platforms
---

### Post by Hangul on 2008-08-11
I'm not sure how best to ask this question since I'm a Linux noob but I'm going to try. 

I recently installed Ubuntu Server (ubuntu-8.04.1). I'm trying to accomplish the following:

[list]
[*]Use the server as a file server for three Windows XP clients - I want to share media files (music, movies, pictures). I would also like to store my iTunes library here.
[*]Use the server as a media server for my PS3, eventually. (mediatomb?)
[*]Use the server as a means to access my media from any computer anywhere (eventually)
[/list]

Anyway I got started on the first task and am stuck there so my question is mainly about that. I followed **[these]("http://doc.ubuntu.com/ubuntu/serverguide/C/samba-fileserver.html")** directions for setting up a Samba file server (I realize that it's not very secure, but I am doing these things incrementally and will secure everything much more thoroughly once I learn how) and have made the following modifications to the **smb.conf** file:

```
workgroup = WORKGROUP
...
security = user

...
[share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755

```

The drive that I am storing my media files on is a WD My Book (500 GB) external usb HDD. I attached it to my server box and used fdisk to determine that it is being listed as sdb1 with a format of "W95 FAT32 (LBA)". I then mount the drive remotely (using Putty) like so:

```
sudo mount /dev/sdb1 /srv/samba/share
```

I navigate, via putty, to /srv/samba/share and see the drive and it's contents. I can create and delete existing directories with no problem from the putty command line. 

I then go into windows to map my drive. 

Tools > Map Network Drive > etc.

The drive maps fine and again, I can see the drive's contents. The only problem though is that I cannot write to the drive at all. Additionally I selected the drive from Explorer and checked it's properties - it's showing up as an NTFS drive. If you recall I said that fdisk from putty recognizes it as a FAT32 drive. I then unmount the drive, disconnect it and attach it directly to the XP client and check it's format and it's being recognized as a FAT32 drive as it should... 

Can anyone tell me what gives? I'll need to write to this drive if I am going to add albums via iTunes or any other cd ripping program. Why does Ubuntu see it as a FAT32 drive but XP see it as NTFS. What have I done wrong?

---

