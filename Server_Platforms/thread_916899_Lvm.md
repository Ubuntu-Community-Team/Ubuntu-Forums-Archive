---
title: "Lvm"
date: 2008-09-11
forum: Server Platforms
---

### Post by Mr_Whippy on 2008-09-11
Hi all,

I recently installed a new server, I have managed to get dhcp and dns (bind9) running on it with some help, however i now cannot access my lvm drives, as they keep saying not a directory.

I have tried to mount them somewhere but have not managed to do so apparently ext3 is not a valid filesystem.

can anyone help me please.

---

### Post by windependence on 2008-09-11
This happened after you installed the packages? Can you boot the machine? Give us a bit more info about how you had the machine set up and what your LVM setup and partitioning were.

-Tim

---

### Post by trmentry on 2008-09-11
> **Mr_Whippy said:**
> Hi all,

I recently installed a new server, I have managed to get dhcp and dns (bind9) running on it with some help, however i now cannot access my lvm drives, as they keep saying not a directory.

I have tried to mount them somewhere but have not managed to do so apparently ext3 is not a valid filesystem.

can anyone help me please.


if you run things like

pvs   or   lvs

can you see your logical volumes?

I had to recover and encrypted lvm partition one time... this is what i did... excluding the crypto stuff.

```

as root

vgchange -ay kessel  (it will see the vg on the now unencrypted
section) (kessel was my VG name) (You need to know the vg name.. no way to get it otherwise.)

lvscan (gives you the device names for the mounts)

mount /dev/kessel/root /mnt/kessel  (where root was my logical volume name)

Happily copy all data off that you want.

umount /mnt/kessel

vgchange -an kessel


```

---

### Post by Mr_Whippy on 2008-09-11
Hi all, 

sorry, the drives are there as far as i can tell, if i  run vgdisplay -v i can see all the drives and what i thought would be the drive mappings for them, however i cannot mount them cd into them or anything, i get back a message saying they are not drives.

the machine is a fresh build and the lvm was setup at install i have done nothing else with it apart from that.

---

### Post by trmentry on 2008-09-11
> **Mr_Whippy said:**
> Hi all, 

sorry, the drives are there as far as i can tell, if i  run vgdisplay -v i can see all the drives and what i thought would be the drive mappings for them, however i cannot mount them cd into them or anything, i get back a message saying they are not drives.

the machine is a fresh build and the lvm was setup at install i have done nothing else with it apart from that.

are these drives from another server that you put into a new server?

---

### Post by Mr_Whippy on 2008-09-12
There is only one drive, Physical in the server, 

When I said drives I was referring to the LVM partition that I set up Logical Volumes on during installation, 

Do i need to activate them for first use or something, I have literally installed the server with the lvm on it, then setup dhcp, dns and vmware thats all that has been done on the server.

---

### Post by Mr_Whippy on 2008-09-12
> **trmentry said:**
> if you run things like

pvs   or   lvs

can you see your logical volumes?



What are pvs and lvs, not sure if i mentioned it or not, but if i run vgdisplay -v i get a full listing of the volume and the logical drives on there.

---

