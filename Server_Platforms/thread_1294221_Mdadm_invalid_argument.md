---
title: "Mdadm invalid argument"
date: 2009-10-18
forum: Server Platforms
---

### Post by Cl0cKw0rK on 2009-10-18
So...

I have a 5 disk raid i am trying to assemble using this command:
```

mdadm -A --verbose /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdd1 /dev/sde1 /dev/sdf1

```
And I get this
```

mdadm: looking for devices for /dev/md0
mdadm: /dev/sda1 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sde1 is identified as a member of /dev/md0, slot 3.
mdadm: /dev/sdf1 is identified as a member of /dev/md0, slot 4.
mdadm: added /dev/sdb1 to /dev/md0 as 1
mdadm: failed to add /dev/sdd1 to /dev/md0: Invalid argument
mdadm: failed to add /dev/sde1 to /dev/md0: Invalid argument
mdadm: failed to add /dev/sdf1 to /dev/md0: Invalid argument
mdadm: added /dev/sda1 to /dev/md0 as 0
mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.

```

all of the drives are in /dev, /proc/partitions, adn all have valid mdadm superbloacks. They also all passed long smart test and the dd to /dev/null test.

Im at a lose. Any help would be appreciated.

Thanks,
Clockwork

---

### Post by Cl0cKw0rK on 2009-10-18
dmesg says that the superblocks did not have valid checksums.

how do i fix this.

also from what i can tell, the superblocks are all fine

---

### Post by fjgaude on 2009-10-18
I don't have that much experience with bad drives... why not just do this and see what happens:

```
sudo mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
```

Then do an assemble:

```
sudo mdadm --assemble --scan
```

Maybe the mdadm.conf file has a wrong UUID for assemble and these commands will fix it.

Let us know what happens. Thanks!

---

### Post by Cl0cKw0rK on 2009-10-18
This is the result:

```

# mdadm --assemble --scan
mdadm: failed to add /dev/sdd1 to /dev/md0: Invalid argument
mdadm: failed to add /dev/sdf1 to /dev/md0: Invalid argument
mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.
mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy

```

Interesting tidbit, sde is no longer in that list.

---

### Post by fjgaude on 2009-10-19
Okay, what does this show:

```
sudo mdadm -E /dev/sda1
```

That will show what mdadm thinks of all the drives in the array that **sda1** is in.

---

