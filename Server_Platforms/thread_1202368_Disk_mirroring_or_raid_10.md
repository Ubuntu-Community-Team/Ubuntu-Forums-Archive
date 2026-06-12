---
title: "Disk mirroring or raid 10"
date: 2009-07-02
forum: Server Platforms
---

### Post by salim.madni on 2009-07-02
dear gurus,

i do need to built a machine, that is like a HP MINI SMALL SERVER looks like pc. HP PROLIANT ML110

we have provided 
- 500GB SATA DISKS (2 pcs)

what is required
- there is folder /backup in drive A(FIRST DISK)
- soon any data writes, same time it must write the data on 2nd disk which is DRIVE B (2ND DISK)

can we achive this target on hardware or software level using linux this feature and functionality.

the main problem server has no hardware raid controller card. it is like simple low end server machine pc.

the purpose if if first disks, get failed. so we can run our operation from 2nd disks.

this will be our backup server and we need to place to remote. so from live site/office it will carry data and dump there

advise highly appreciated
regards
salim

---

### Post by Cheesemill on 2009-07-02
If you only have 2 disks then you can either do RAID 1 or RAID 0, you can't do RAID 10.

RAID 0 only offers performance gains but with no fault tolerance, this means if one drive goes you lose all of your data.

RAID 1 would mirror all information across both drives so you would end up with 500GB of space.

There are issues with booting from a software RAID 1 that will probably affect you so investigate these first.

Also remember that RAID is not a substitute for backups. You must always have a proper backup routine in place as well, with off-line and off-site backups.

---

### Post by salim.madni on 2009-07-02
dear sir thanks for ur support

there are many solutions available but mostly commercial

i am looking can i do anything on LINUX plateform please using ubuntu or any other

the best for this case will be RAID1 that can do mirroring, but how to do where to do exactly, some tips and guideline needed only

regards
salim

---

### Post by Cheesemill on 2009-07-02
[http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1](http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1)

---

