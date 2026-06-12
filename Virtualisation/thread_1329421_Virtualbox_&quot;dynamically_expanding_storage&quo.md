---
title: "Virtualbox &quot;dynamically expanding storage&quot; disk running out of space?"
date: 2009-11-17
forum: Virtualisation
---

### Post by khughitt on 2009-11-17
Hello,

Does anyone know whether the virtualbox "dynamically expanding storage" virtual partitions are supposed to expand automatically, or if you need to do so manually?

I had always assumed that they would automatically expand once they start to fill up, however, I had never actually come close to running out of space until recently. When expanding a large archive, the action was unable to complete because space ran out. I restarted the system, but there is still only a little free space (50mb) available. I could not find an option anywhere in the media manager or OS settings to resize the partition, and I'd like to avoid having to reinstall everything. The guest OS is CentOS 5.4 (64-bit), running in Karmic. The initial virtual drive size was set to 8Gb.

Any ideas?

---

### Post by cgb on 2009-11-17
The dynamic expanding drive just starts off using only a part of the size you specified during creation.  It will expand until it fills the space you specified, not more.  The only way you can expand this now would be with creating a new virtual disk and using cloning tools to clone the drive to the new.

---

### Post by khughitt on 2009-11-17
Okay, that explains things. In that case I think I will just create a second virtual drive to use for additional storage. Thanks for clearing things up! :)

---

