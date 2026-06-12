---
title: "Raid 1 data recovery"
date: 2010-10-04
forum: Server Platforms
---

### Post by sjoerdvdvis on 2010-10-04
Hi all,

At our study association we have some major issues regarding our raid 1 setup. Somehow, our raid 1 configuration stopped working and all we want now is to recover the data.

```
paradmin@paradokje: /etc/$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
unused devices: <none>
```

So no md0 config is available. When viewing the disks in Gparted they show up with the total size unallocated so I think all the partition information is lost, together with my data....

Can you help me?

---

### Post by fjgaude on 2010-10-04
For one thing **gparted** doesn't know about raid... have you tried forcing an assemble:

```
sudo mdadm --assemble -f /dev/md0
```

That may get you good results.

What does this show:

```
sudo mdadm --detail /dev/md0
```

There's a lot of study required to get **mdadm** to do what you wish.

BTW, a file manager might access one of the drives in the array and show all the files. At least it would give you an idea of what's there.

---

### Post by SeijiSensei on 2010-10-04
I've found I can simply mount the component drives in a RAID1 as normal hard drives and find all the data intact.

---

### Post by sjoerdvdvis on 2010-10-05
> **fjgaude said:**
> For one thing **gparted** doesn't know about raid... have you tried forcing an assemble:

```
sudo mdadm --assemble -f /dev/md0
```

That may get you good results.

What does this show:

```
sudo mdadm --detail /dev/md0
```

There's a lot of study required to get **mdadm** to do what you wish.

BTW, a file manager might access one of the drives in the array and show all the files. At least it would give you an idea of what's there.

```
paradmin@paradokje:~$ sudo mdadm --assemble -f /dev/md0
mdadm: no devices found for /dev/md0
```

It seems the server thinks the disks are empty. Do you know of any good data recovery software? :-(

---

### Post by fjgaude on 2010-10-05
You might try this next:

```
sudo mdadm --assemble -f --scan
```

What does your mdadm.conf file show?

I don't know of data recovery software... way over my head these days.

---

