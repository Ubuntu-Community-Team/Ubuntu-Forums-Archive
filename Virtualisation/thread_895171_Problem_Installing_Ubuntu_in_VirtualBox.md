---
title: "Problem Installing Ubuntu in VirtualBox"
date: 2008-08-19
forum: Virtualisation
---

### Post by ryan_rei on 2008-08-19
Hi my name is Ryan, I have a problem in installing Ubuntu 7.10.

I try to install Ubuntu 7.10 on Virtual Box, I followed the installation step by step untill the step to Prepare disk space. There's a choice whether to use guided partition or manual partition, so choose guided partition. Then I finished the steps, The I began installing ubuntu, but after a while there's an error saying that: 
--Failed to create a swap space--
The creation of swap space in partition #5 of SCSI (0,0,0)(sda)failed

Can you guys help me, I'm really a newbie on Linux especially Ubuntu, I use ubuntu 7.10. Thanks I appreciate any help.

regards.

---

### Post by Elfy on 2008-08-20
When I've installed various buntu variants on a vbox virtual drive I have used the whole drive option - it doesn't need to be guided as it will only use the virtual drive that you created for it.

---

### Post by ryan_rei on 2008-08-20
Maybe I'll try using manual partition, but I dunno how to do that, perhaps any of you guys could help me ? Big thanks guys.:grin:

Regards.

---

### Post by pi.boy.travis on 2008-08-20
If you are partitioning manually, you need to create two partitions, one for the system, and one for swap.  When you create a partition, it will ask for a mountpoint, give the system partition: /  and there is a "use as swap" option.

Hope this helps!

BTW swap is like hard disk RAM, and is also used for the suspend to disk feature (hibernate).

---

