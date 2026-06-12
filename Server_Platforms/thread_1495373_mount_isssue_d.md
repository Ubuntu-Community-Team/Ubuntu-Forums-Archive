---
title: "mount isssue d???????"
date: 2010-05-28
forum: Server Platforms
---

### Post by flandercan on 2010-05-28
Hi, 

When using the following cifs mount command, 

mount -t smbfs -o username=username,password=password //srv/shr /usr/localfolder/

and the cifs share does not exist, localfolder is mounted like 

d?????????    ? ?        ?            ?                ? localfolder

after a number of time , when umounting we get a kern <soft lock>

Is there any way to fail the mount if the destination share does not exist, ive had a quick look through man mount but can not see a solution.

Thanks
Paul

---

### Post by flandercan on 2010-05-28
A little more info, 

I have noticed in the console so errors, 

CIFS VFS: Error 0xfffffffb on cifs_get_inode_info in lookup of \share

But the share does work, 

I have approx 1000 mounts on this server am i simply asking it to do to much? 

Thanks 
Paul

---

