---
title: "Unbuntu server resize partition"
date: 2016-02-25
forum: Virtualisation
---

### Post by caseyj on 2016-02-25
Hello,
 I use vmware to virtlz my ubuntu svr. The vHDD i use become too small, so i move to new vHDD bigger.
Initial I have only 45Go (44.91Go). I migrate to new one = 400Go. It boots and all looks fine but, the OS still see 45Go... I use gParted and all seem fine, and again after reboot I still have 45Go... :confused: ... Help!

[IMG]http://s10.postimg.org/ypsa3aoeh/Screen_Shot_2016_02_25_at_15_02_21.png[/IMG]

Still 44.91Go.... 
[IMG]http://s10.postimg.org/lkcrx6uix/Screen_Shot_2016_02_25_at_15_03_47.png[/IMG]

Why?...... :confused:  :confused:  :confused:  :confused:  :confused:

---

### Post by howefield on 2016-02-25
Thread moved to the "*Virtualisation*" forum for better support.

---

### Post by MAFoElffen on 2016-02-26
You extended the partition, but now you need to extend your lvm partition, but still need to extend the vg, lv and the contained filesystem.

```

sudo su
pvs    # will show size in the lvm pv extents 
vgextend ubuntu64-vg /dev/sda5   # will extend the volume group
vgs 
vgscan  # note under "pe free" how much is says is free, to be able to extend the lv. Say it says "18GB"...
lvextend -L +18G /dev/mapper/ubuntu64-vg/root    # extend the lv
resize2fs /dev/vg_tecmint/LogVol01    # extend the filesystem
# see the results
pvs
vgs
lvs
exit

```
The thing is... you don't have to commit it all. You can add as you need or want. LVM is flexible enough to do that on the fly. You can save room for a rainy day. 

I like installing VM's with LVM. That way I can add additional VDisk images, add then to the extents, then have that new disk in pool, all on the fly.

---

### Post by caseyj on 2016-02-26
Hi,

 done by enter this 
> 
[FONT=Verdana]lvresize --resizefs --extents +100%FREE /dev/mapper/ubuntu64--vg-root[/FONT]
all fine now. Thanks!

---

### Post by MAFoElffen on 2016-02-26
You are welcome.

Please return to this thread > use the Thread tools link to the top-right of your first post... and Mark this thread as "Solved". This helps other searching on the same problem to find your solution.

---

### Post by caseyj on 2016-02-26
ok! I looked for that but not be able to find how make topic solved ;D

---

