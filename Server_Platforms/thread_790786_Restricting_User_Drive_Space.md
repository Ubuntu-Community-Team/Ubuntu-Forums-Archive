---
title: "Restricting User Drive Space"
date: 2008-05-11
forum: Server Platforms
---

### Post by dwoody on 2008-05-11
Hello,
I currently have an FTP/Samba/Web server running with the latest Ubuntu Server edition. There are about 15 users on the machine all of which store/backup their files on the server. They are all friends so I am in no way suspicious of their behavior but I need to restrict each user to a certain amount of disk space to make sure my disk doesn't fill up. How do I do this?
Additionally, many of us have a lot of data which I will have to spread along multiple hard drives so how do I set up such a scheme where, for example, user 'A' and user 'B' get X gigabytes on my first drive while user 'C' and user 'D' get X gigabytes on my second drive (and so on)?
I am relatively new to this stuff so any help is appreciated. Thanks.

---

### Post by Monicker on 2008-05-11
You can use the quota package to limit their disk space usage.  Its in Synaptic.  Its been a while since I looked at the config file for quota, but I believe its fairly straightforward.  You can even set a warning level, where they will get notified if they are reaching their limit.

---

### Post by dwoody on 2008-05-12
ok ive got the user restrictions on drive space working using the quota thing. Thanks for the tip.
Right now I have an 80GB (say sda) drive with the server installation on it and two separate 200 GB drives (say sdb and sdc). So suppose I had four users and wanted to give them each 100 GB of space by splitting the 200 GB drives equally but not letting them save on the main 80GB drive. How do I go about this since the home folder (which contains each of the users' folder) is on sda? Do I have to mount each users' folder to the new drives and create a mount point or something? Any help is appreciated.

---

### Post by beniwtv on 2008-05-13
You could create a LVM volume. Basically, LVM lets you create a virtual drive, e.g. your two drives will show up as a single drive, where you can mount /home.

Another way (much more simple) would maybe change the user's home dir. The file /etc/passwd will let you set where the particular user's home resides.

Cheers.

---

