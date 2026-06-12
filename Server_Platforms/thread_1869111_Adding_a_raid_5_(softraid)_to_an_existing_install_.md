---
title: "Adding a raid 5 (softraid) to an existing install and moving home"
date: 2011-10-25
forum: Server Platforms
---

### Post by taalas on 2011-10-25
Hi,

I recently installed Ubuntu Server 11.10 on our new HP N36L and all went extremely well so far.

I used a small HD for the system itself choosing "entire disk" (but no LVM) during install.

I would now like to add another 3 HDs to the server and use them as a raid 5. The raid should later be used to host the home directories and svn repositories.

Can I use these guides:

[http://wiki.ubuntuusers.de/software-raid](http://wiki.ubuntuusers.de/software-raid)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

to accomplish this or is there any other guide I can read up on this? Also, my disks are Advanced Format drives (Samsung HD204UI), is there anything I should be doing differently with these drives?

Any help would be great, thanks alot!

---

### Post by vasile002 on 2011-10-25
Hi,

Not sure about the advanced format drives but if Ubuntu detects them I believe you can use them as usual drives. Yes, those guides are fine to use. The home partition migration is easy though, you just need to move the data to the new drive and then mount it to /home and put the necessary data in /etc/fstab

---

