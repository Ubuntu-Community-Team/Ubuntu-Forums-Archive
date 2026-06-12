---
title: "recover mdadm array after accidently using --create"
date: 2008-11-30
forum: Server Platforms
---

### Post by Azzuron on 2008-11-30
Is it possible to recover an array that has accidentally been recreated using mdadm --create? The array was fine before hand, and i went to move it to a new system. I had a lapse of intelligence and ran --create instead off --assemble. I thought i remember reading that there are backup superblocks made on the disks. I have no idea how to utilize these or if it would even be possible in this case. I have a feeling today is going to be a very very bad day for me haha. I need the data on these disks. Thanks for your help.

I just wanted to add, that on top of the issue with the raid, the md0 device was luksEncrypted. Which I don't think should be an issue. just wanted to note it though.

---

### Post by fjgaude on 2008-11-30
Did you just do a --create, or did you also add a filesystem to the array?

I would try to assemble the array and see what happens before I did anything else. Use the --force of -f option if a simple --assemble /dev/md0 doesn't work.

Now if all this fails, I'd rename the /etc/mdadm/mdadm.conf file, remove mdadm, re-boot. Then re-install mdadm and do:

```
sudo mdadem --assemble --scan
```

with the mdadm.conf file being auto created.

Let us know how you are doing.

---

### Post by Azzuron on 2008-11-30
I did just do the --create. the array started to rebuild, and i realized there was an issue when i tried to run my cryptsetup luksOpen command to load the luks partition. i get an error from luks saying there is no key. and when i tried to do a luks dump there was no luks partition on the array. After i realized this, i did a mdadm --stop /dev/md0 to prevent further possible damage. 

This array was hooked up to a fresh install of ubuntu when this happened. I then thought that perhaps there was some difference in the install (it was through a VM) and that maybe somehow the VM was goofing up things with the USB emulations. I took a box i had that was pretty bored and put ubuntu on it, then mounted the array with assemble (realizing what i had done before now) and im still in the same situation. no matter how i attempt to mount the array (with or without the disk that was rebuilding) i get an unmountable luks partition.

The array mounts fine, it just appears to not have any data. I also think its rather odd, that in gparted (which i use to just grab the names of the devices quick) 2 of the drives are showing partitions, and one does not. The one that does not is the rebuilding disk. when i originally created the array i didn't use partitions at all, i just used the raw device. Reguardless I cannot assemble an array from these partitions i get no superblock errors.

> root@FileServer:~# cryptsetup luksDump /dev/md0
Command failed: /dev/md0 is not a LUKS partition

---

### Post by fjgaude on 2008-11-30
I don't have anything more to suggest... you likely are in a bind!

Hope you have backups.

---

