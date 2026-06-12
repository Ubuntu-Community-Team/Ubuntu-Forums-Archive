---
title: "Raid5"
date: 2009-07-09
forum: Server Platforms
---

### Post by Cl0cKw0rK on 2009-07-09
I have a mdadm raid5 with 4 drives. I think the computer shut down oddly, and now mdadm cannot reassemble the whole raid because one of the drives has a bad super-block.

What's the best way to fix this. Is there a simple command that will recreate the super-block?

Also, the array is still functioning, just with one less drive.

Thanks,
Clockwork

---

### Post by Cl0cKw0rK on 2009-07-09
Update:doing mdadm -E on all of the devices returns this on all but one     
> Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 2930279808 (2794.53 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 1
And this on the one that mdadm had not written to or some such
>      Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 2930279808 (2794.53 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1

Also their update times are different.
Simple way to fix this? Thanks.

---

### Post by Cl0cKw0rK on 2009-07-09
Alright, nother update.
zerod all of the superblocks, reading that mdadm will recognize the array if you just recreate it.

tried receating with this command:
# mdadm --create /dev/md1 --verbose --level=5 --raid-devices=4 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1

result:
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: /dev/sdb1 appears to contain an ext2fs file system
    size=-1364687488K  mtime=Thu Jul  9 21:24:59 2009
mdadm: /dev/sdd1 appears to contain an ext2fs file system
    size=-1096252032K  mtime=Thu Jul  9 16:41:55 2009
mdadm: size set to 976759936K
Continue creating array? 

I'm at a loss, from what i can tell,this shows that mdadm is not recognizing the array.

---

### Post by fjgaude on 2009-07-10
Did you first create the array using this guide:

[http://www.hscripts.com/tutorials/linux-services/mdadm.html](http://www.hscripts.com/tutorials/linux-services/mdadm.html)

Do you have valuable data on the array presently?

---

