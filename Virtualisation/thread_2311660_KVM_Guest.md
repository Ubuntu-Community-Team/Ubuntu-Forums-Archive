---
title: "KVM Guest"
date: 2016-01-29
forum: Virtualisation
---

### Post by glenn_91 on 2016-01-29
Hi All,

Has any one tried to shrink the drive on a kvm guest?  Please help..
Host and guest are both same Ubuntu 12.04 

Thanks in advance..

---

### Post by MAFoElffen on 2016-01-30
Yes. And it is smart to ask the first time trying it. The documents are spotty on what to do to decrease in size. I think they did that because the answers to the 4 questions below present a multitude of variables.

Please describe what format the image is (raw, qcow2, etc)

Then if it contains mdadm and/or lvm. 

Then the filesystem type. 

Then what OS is installed on the VM image. 

*** Basically you need to shrink the filesystem, then the partitions, before you can shrink the disk image. 
I usually clone the disk for the just in cases, until I get my changes done.

After you supply some of the basic info requested above, we can get a little more specific than that.

---

### Post by glenn_91 on 2016-01-31
Thanks for reply... 
My image format is raw  (image.raw)
filesystem type is ext4 /   (without swap)
OS installed ubuntu 12.04
without [COLOR=#000000]mdadm or lvm. [/COLOR]

---

### Post by MAFoElffen on 2016-02-02
I'll give you 3 different ways. You choose which you might feel more comfortable with.


(#1) Check the disk image file to see how much you can shrink the partitions:
```

virt-df /pathTo/disk.img

```
Boot from the GParted Iso. Shrink the size of the root partition to decrease it's size safely. Move the swap partition left, so there is no un-allocated space between the end of the root partition and it...


Another way to do this same is via guestfish, but is is more complex (and step by step)...
```

guestfish -a /pathTo/disk.img


><fs> run
><fs> e2fsck-f /dev/sda1
><fs> exit


sudo virt-resize --shrink /dev/sda1 /pathTo/disk.img /pathTo/disk2.img

``` 
the filesystem within sda1 was compressed, leaving slack space between the filesystem and the partition. virt-resize using a switch to shrink the partition, then writes the new disk image with the smaller partition, creating a smaller disk image file.




(#2) While running the VM, use dd to fill the slack space of the filesystem with a file full of zeros...
```

dd if=/dev/zero of=/dummyZeroFile
rm -f /dummyZeroFile

```
deleting that file removes the filename from the filesystem, but the physical sectors of the filesystem, still has the slack written as zeros...


Shut down the VM gracefully. Make a backup of the image file
```

mv disk.img disk2.img

```
Now you can use either kvm-img or qemu-img ... with a convert switch to copy the image file to another. When it sees the unused zero file, it skips that part resulting in a smaller disk. I use qemu-img. You can do that as normal, without compression -or- compressed...
```

# Shrink without compression:
qemu-img convert -O qcow2 disk2.img disk.img
# Shrink with compression:
qemu-img convert -O qcow2 -c disk2.img disk.img

```


(#3) virt-sparsify is  newer utility that reads and zeros the slack space on it's own, then does what qemu-img does to copy the disk image file to the output disk image file, ignoring the zeroed slack space... It does it all offline.
```

mv disk.img disk2.img
virt-sparsify disk2.img disk.img

```

---

