---
title: "LVM adding a disk  - is exisitng LV data retained ?"
date: 2011-06-03
forum: Server Platforms
---

### Post by leegold on 2011-06-03
Hi,

LVM question:

I need to add space to my /var. I have var as one of my logical volumes.

If done correctly will I loose data on my existing /var? 

In other words, I'm going to add a second hard disk specifically to enlarge /var. I already have all my existing partitions (including /var) as LVM logical volumes. If I add the second hard disk to extend the /var logical volume will data be destroyed in the existing /var LV on the first hard disk?

I know anything is possible. But given "normal operation" is existing data retained?

Thanks.

---

### Post by ruffEdgz on 2011-06-03
If done properly, no. You shouldn't lose any data. This is how you should do it:
[LIST]
[*]Add the new physical volume to your system
[*]Add that newly added PV to your VG
[*]Once the VG has it, extend the LV
[*]Resize LV
[/LIST]

Here is the code.
Add new physical volume:
```

pvcreate /dev/sdx

sdx = the new hdd

```

Extend VG
```

vgextend vggroup /dev/sdx

lvgroup = the vg group you want to extend
sdx = the new hdd you made into a PV

```

Extend LV:
```

lvextend -l +100%FREE /dev/mapper/vggroup-lvname
(will extend 100% available in the VG to lvname)

or

lvextend -L +50G /dev/mapper/vggroup-lvname
(will extend 50G only from the VG to lvname)

```

Resize LV:
```

resize2fs /dev/mapper/vggroup-lvname
(this will only work for ext2/3/4 file systems and it can be done while mounted)

```

Cheers!

---

### Post by sfabel on 2011-08-19
What about the data on the new PV?

We have a problem that two different servers need to be "merged" with respect to one LV (/home). Is it possible, assuming that the filenames do not overlap, of course, to extend the VG on the new server, without affecting the data at all, on any of the PVs making up the VG?

Thanks!

Stephan

---

