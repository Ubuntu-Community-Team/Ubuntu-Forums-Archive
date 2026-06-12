---
title: "Resize main partition?"
date: 2009-09-02
forum: Server Platforms
---

### Post by Khao8 on 2009-09-02
Hey all,
I'm trying to set up my server to do virtualization using this tutorial : [http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-9.04](http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-9.04)

I want to use LVM to manage my VHDs but I need a free partition for this. However my server only has one disk and one partition taking up all the space (except for swap).
I googled and searched the forums a lot and the only answer I could find was to boot using a Live CD.
Is there any way to resize my main partition to take less space and create the partitions for this without using a Live CD? Is there any way to do this? I know on Windows some partition program will ask you to reboot for changes to take effect when you modify the main partition, and when you reboot the changes are made. Can I do this remotely or will I have to contact my host's support to do this?

Thanks!

---

### Post by nhanquy on 2009-09-02
> **Khao8 said:**
> 
Is there any way to resize my main partition to take less space and create the partitions for this without using a Live CD?

None! Even if there is one; it would be a very very bad idea to do that. How hard is it to boot from liveCD and resize it to have space for a new partition?

---

### Post by Khao8 on 2009-09-02
Well it's a dedicated server and I can only access it trough SSH, so that's is the difficult part. Will I have to ask my host's support to do this for me?

---

### Post by nhanquy on 2009-09-02
> **Khao8 said:**
> Well it's a dedicated server and I can only access it trough SSH, so that's is the difficult part. Will I have to ask my host's support to do this for me?

I'd tar it to a a backup place, delete old partition, create the new one and tar back to it.
Something like:

> [I][SIZE=5]
tar cf - -C /old . | tar xvf - -C /new[/SIZE][/I]


---

### Post by Khao8 on 2009-09-02
Well I can't possibly delete the partition while it's mounted and the server is using it.. Someone suggested to boot into recovery mode and I could do it from there. Does anyone know any more information about doing this?

---

