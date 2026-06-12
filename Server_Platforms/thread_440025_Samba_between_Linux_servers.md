---
title: "Samba between Linux servers"
date: 2007-05-11
forum: Server Platforms
---

### Post by yeoheric on 2007-05-11
Hi all,

I have seen many posts on Linux and Windows file sharing but question is a little off the beaten track.

I have 2 Linux servers that need to share files between them using Samba. One is a Gentoo and the other is a Ubuntu 6.06 server.

On the Gentoo server I added the following in the fstab and it worked like a charmed

[SIZE="1"][FONT="Courier New"]//10.1.5.189/localq     /opt/share/peanuts/localq  cifs    auto,credentials=/root/smb,uid=1004,nodev,noatime               1 2[/FONT][/SIZE]

On the Ubuntu server I put this in :
[FONT="Courier New"][SIZE="1"]
//10.1.5.230/localq     /opt/share/stitch/localq   cifs    auto,credentials=/home/joe/smb,uid=1003,nodev,noatime   1 2[/SIZE][/FONT]

And did I a sudo mount -a 

I get a **[FONT="Courier New"]Cannot open file on /home/joe/smb [/FONT]**error message. I even chmod 777 the file! And I did try several other places and it all had the same error message sans the location.

I ended up doing a manual mount :

[FONT="Courier New"][SIZE="1"]sudo mount -t cifs //10.1.5.230/localq /opt/saas/share/stitch/localq/ -o username=bimbo,password=foopass,iocharset=utf8,file_mode=0777,dir_mode=0777[/SIZE]
[/FONT]

What did I do wrong?

TIA 

Eric

---

