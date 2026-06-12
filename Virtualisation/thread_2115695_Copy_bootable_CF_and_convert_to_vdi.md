---
title: "Copy bootable CF and convert to vdi"
date: 2013-02-13
forum: Virtualisation
---

### Post by Wizball on 2013-02-13
Hi

I have been struggling with this all night.
if I use 
dd if=/dev/sda1 of=/home/wizball/Desktop/access1/convert/cf.image

to copy the CF it just copies the files it seems and does nto make a boot able vdi afterwards.

If I use
dd if=/dev/sda of=/home/wizball/Desktop/access1/convert/cf-card.img

after mounting the cf to sda1 then it copies the cf and see,s to go on to the hard drive that is also mounted there.

I have looked around the Internet for solution but cannot find one.

I have managed to convert the image that is produced using 
VBoxManage convertdd cf.image cf.vdi --format VDI

but it will not boot.

I am connecting the CF card to the computer via usb.

many thanks in advance
Peter

---

### Post by lmarmisa on 2013-02-13
Hi Peter,

You are trying to create an image of a CF and then convert it to vdi format.

First step will be the copy. You do not need any virtual machine for this step. I suppose you have a physical computer running Ubuntu.

**You have to be sure that the CF device is not mounted** (umount it if necessary). I will suppose that CF device is /dev/sdc. Then you have to type this command:

```

sudo dd if=/dev/sdc of=CF.image.dd

```You have to use a virtual machine with Ubuntu or other Linux distro for the second step. 

Define an additional virtual disk (.vdi) with just the same size of CF. Do not initialize it. I will suppose that the device assigned to this new virtual disk will be /dev/sdb.

Copy the file CF.image.dd to a folder of the virtual machine and go to that folder.

Then type this command:

```

sudo dd if=CF.image.dd of=/dev/sdb

```Shutdown the virtual machine.

The file vdi will contain the image of the CF converted to vdi format.

An alternative for step 2 (raw disk image to vdi conversion) would be to use the VirtualBox tools:

[http://www.virtualbox.org/manual/ch08.html#idp14558704](http://www.virtualbox.org/manual/ch08.html#idp14558704)

---

### Post by Wizball on 2013-02-14
thanks lmarmisa

but how do I find
```

/dev/sdc

```

if the drive is not mounted

many thanks
> **lmarmisa said:**
> Hi Peter,

You are trying to create an image of a CF and then convert it to vdi format.

First step will be the copy. You do not need any virtual machine for this step. I suppose you have a physical computer running Ubuntu.

**You have to be sure that the CF device is not mounted** (umount it if necessary). I will suppose that CF device is /dev/sdc. Then you have to type this command:

```

sudo dd if=/dev/sdc of=CF.image.dd

```You have to use a virtual machine with Ubuntu or other Linux distro for the second step. 

Define an additional virtual disk (.vdi) with just the same size of CF. Do not initialize it. I will suppose that the device assigned to this new virtual disk will be /dev/sdb.

Copy the file CF.image.dd to a folder of the virtual machine and go to that folder.

Then type this command:

```

sudo dd if=CF.image.dd of=/dev/sdb

```Shutdown the virtual machine.

The file vdi will contain the image of the CF converted to vdi format.

An alternative for step 2 (raw disk image to vdi conversion) would be to use the VirtualBox tools:

[http://www.virtualbox.org/manual/ch08.html#idp14558704](http://www.virtualbox.org/manual/ch08.html#idp14558704)

---

### Post by lmarmisa on 2013-02-14
> **Wizball said:**
> thanks lmarmisa

but how do I find
```

/dev/sdc

```if the drive is not mounted

many thanks

Use this command if you wish to list the drives detected by the system:

```

sudo fdisk -l

```

---

### Post by Wizball on 2013-02-15
that is great thanks the the first part was a lot longer then I had seen before according to that command but seems to have worked.

QUOTE=lmarmisa;12510300]Use this command if you wish to list the drives detected by the system:

```

sudo fdisk -l

```[/QUOTE]

---

