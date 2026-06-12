---
title: "Data recovery"
date: 2010-12-08
forum: Server Platforms
---

### Post by cf0531 on 2010-12-08
Im in class and my teacher made a statement that if you had your os on a striped array and your data being written to a mirrored array that if the os diosks failed you still would not be able to recover the data written to the mirrored disks. Is this correct or not? I thought it didn't sound right.
 
I guess the main question is whether the possibility of data recoverey is going to be a possibility, and is that possibility a difficult and expensive process or is it something that with a little know-how can be accomplished in-house.

---

### Post by dtfinch on 2010-12-08
That would not be correct. Though it's unusual to put an OS on a striped RAID. You would have to reinstall the OS, and reconfigure all the software, which would take a while and somewhat defeat the purpose of using RAID for high availability.

---

