---
title: "Adding new disc to RAID5"
date: 2008-10-31
forum: Server Platforms
---

### Post by Peque on 2008-10-31
Hey guys. 

Is it possible to add a new disc to an already existing RAID5 Drive - without loosing any data???

---

### Post by Titan8990 on 2008-10-31
I doubt you will be able to "add" a disk to the array but you could replace a disk without data loss (this is the point of a RAID5). 

Also, with three different types of RAID (fakeRAID, softRAID, RAID) it is best to say which one you are using when getting assistance.

---

### Post by fjgaude on 2008-10-31
I do believe you can add a drive to an **mdadm** raid5 array, through the use of the "grow" command. It's all in the **man** pages for mdadm. Here's other stuff to read, study:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
/usr/share/doc/mdadm/FAQ.gz  and md.txt.gz
[http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)
[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)

Let us know how you are doing.

---

### Post by Coreigh on 2008-10-31
I agree with fjgaude. Check these links, if they don't have the exact answer the'll set you in the right direction.

[http://http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html]("http://http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html")
[http://nst.sourceforge.net/nst/docs/user/ch14.html]("http://nst.sourceforge.net/nst/docs/user/ch14.html")


However ... they probably won't help you with a hardware RAID. You will have to consult the vendor documentation for adding a disk.

---

### Post by Coreigh on 2008-10-31
I agree with fjgaude. Check these links, if they don't have the exact answer they'll set you in the right direction.

[http://http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html]("http://http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html")
[http://nst.sourceforge.net/nst/docs/user/ch14.html]("http://nst.sourceforge.net/nst/docs/user/ch14.html")


However ... they probably won't help you with a hardware RAID. You will have to consult the vendor documentation for adding a disk.


Sorry for double post, I guess I'm impatient.

Can I delete ?

---

