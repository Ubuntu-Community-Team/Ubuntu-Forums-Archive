---
title: "Add single data disk to existing RAID1 w LVM ?"
date: 2013-12-20
forum: Server Platforms
---

### Post by drfox on 2013-12-20
I have installed a 250GB and a 500GB (obviously only using 250GB of that drive) disk as RAID1 with LVM using mdadm on an HP N54L microserver.
I am going to migrate the data from an existing NAS to the server, and I would like to use my existing HDs. 
What I would LIKE to do is take 1 of my 2TB HDs out of the NAS, add it to the server, use the new drive for /home and /srv/samba and copy data from the NAS to the server, then take the other 2TB HD out of the NAS and establish another RAID1 with LVM with the two 2TB HDs. 
Is this possible? Are there any (easy) instructions on how to do it? 
Thanks for any help you can give, even if it's to say that what I want to do is impossible.

---

