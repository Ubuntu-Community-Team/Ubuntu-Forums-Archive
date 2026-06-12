---
title: "Increase the size kvm vm with lvm?"
date: 2019-11-22
forum: Virtualisation
---

### Post by Heeter on 2019-11-22
Hi all,

Running ubuntu18 with kvm. currently running 2 vms. each vm is ubuntu 18. Both are sitting in the /dev/lvg/vmstorage on the host server. one vm is 99G and the other is 45G.

```

root@serv:/home/admin# ls -l /var/vmstorage/
total 105637884
-rw------- 1 libvirt-qemu kvm  48325984256 Nov 21 22:22 mailserv
-rw------- 1 libvirt-qemu kvm 106316892016 Nov 21 22:22 webserv

```

I would like to increase the storage space in one of the VM's using LVM.

I have already increased the size of the vm image using:
```

root@serv:/home/admin# qemu-img resize /var/vmstorage/webserv +20G
Image resized.

root@serv:/home/admin# lsblk
NAME               MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda                  8:0    0  1.7T  0 disk 
&#9500;&#9472;sda1               8:1    0  1.9G  0 part /boot
&#9500;&#9472;sda2               8:2    0    1K  0 part 
&#9492;&#9472;sda5               8:5    0  1.6T  0 part 
  &#9500;&#9472;LVG-root       253:0    0    4G  0 lvm  /
  &#9500;&#9472;LVG-usr        253:1    0    6G  0 lvm  /usr
  &#9500;&#9472;LVG-var        253:2    0    4G  0 lvm  /var
  &#9500;&#9472;LVG-tmp        253:3    0  3.5G  0 lvm  /tmp
  &#9500;&#9472;LVG-bak        253:4    0  7.5G  0 lvm  /bak
  &#9500;&#9472;LVG-srv        253:5    0  3.8G  0 lvm  /srv
  &#9500;&#9472;LVG-opt        253:6    0   52G  0 lvm  /opt
  &#9500;&#9472;LVG-home       253:7    0  1.8G  0 lvm  /home
  &#9500;&#9472;LVG-isostorage 253:8    0    5G  0 lvm  /var/isostorage
  &#9492;&#9472;LVG-vmstorage  253:9    0  170G  0 lvm  /var/vmstorage
sr0                 11:0    1 1024M  0 rom  
sr1                 11:1    1 1024M  0 rom  

```

 on the host server, and it increased from 150G to 170G.

The current size of the vm is 99G, would like to add +20G

But I can seem to increase the size on the vm guest side:

I tried:
```

root@webserv:/home/admin# lvextend -l 100%FREE -r /dev/webserv-vg/root
  New size of 0 not permitted.

root@webserv:/home/admin# lsblk
NAME                   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sr0                     11:0    1 1024M  0 rom  
vda                    252:0    0  119G  0 disk 
&#9492;&#9472;vda1                 252:1    0   99G  0 part 
  &#9500;&#9472;webserv--vg-root   253:0    0   98G  0 lvm  /
  &#9492;&#9472;webserv--vg-swap_1 253:1    0  980M  0 lvm  [SWAP]

root@webserv:/home/admin# lvextend -L+20G -r /dev/webserv-vg/root
  Insufficient free space: 5120 extents needed, but only 0 available

root@webserv:/home/admin#

```

But it is not letting me

What do I need to do?

---

### Post by Dennis N on 2019-11-22
> The current size of the vm is 99G, would like to add +20G

You need to resize the virtual disk. I have used the directions given here:
[https://fatmin.com/2016/12/20/how-to-resize-a-qcow2-image-and-filesystem-with-virt-resize/](https://fatmin.com/2016/12/20/how-to-resize-a-qcow2-image-and-filesystem-with-virt-resize/)

---

### Post by TheFu on 2019-11-22
So you are using LVM on the hostOS which provides a file-based VM storage area 
and
you are using LVM inside the guest OS.

In this storage setup, the storage changes on the host doesn't directly impact the guest.  When you resized using the qemu-img tool, that was like making a larger physical disk, but inside the VM, until you force it to see the new size, you are stuck.

I would run **sudo -H gparted** inside the guest to have it see the new storage.  Then reboot the guest so the OS really sees it.
Next you should post the output from these commands run from inside the guest:
```
sudo parted -l
lsblk -o name,size,type,fstype,mountpoint
df -hT -x squashfs -x tmpfs -x devtmpfs
```

I suspect the easiest answer will be to add a new 20G partition, create a PV in that partition, add that PV to the existing VG, then use **sudo lvresize -r -L+20G /path/to/the/lv..... **
That will resize the file system at the same time the LV is increased in size.  1-step, like was mentioned in another thread.

Do you really want to have all that storage inside the root LV?  I'd rethink that, but it is your machine.  I keep the OS in a 25G LV and put everything else into other LVs.  It makes sense for backups and OS upgrades and OS patching to keep them separate, IMHO.
Plus you might want to leave 5G free in the VG to support snapshots for backup needs.

lvextend/lvresize/lvreduce are all really the same program with resize accepting bigger and smaller sizes.  Good on you for specifically choosing lvextend.  I need to use that for making LVs bigger for safety reasons.  Thanks.

---

### Post by Heeter on 2019-11-22
Hey Guys for the replies

I am trying to use the tutorial. I am stuck trying to figure the command for my particular situation, though.

This is what I have now:
```

root@serv:/var/vmstorage# qemu-img info webserv
image: webserv
file format: qcow2
virtual size: 119G (127775277056 bytes)
disk size: 94G
cluster_size: 65536
Format specific information:
    compat: 1.1
    lazy refcounts: true
    refcount bits: 16
    corrupt: false
root@serv:/var/vmstorage# 

```

The virtual size is now where I want it. (120G)

Then I type this in:
```

root@serv:/var/vmstorage# virt-resize -expand webserv webserv
virt-resize: error: usage is: virt-resize [--options] indisk outdisk

If reporting bugs, run virt-resize with debugging enabled and include the 
complete output:

  virt-resize -v -x [...]

```

/var/vmstorage/ is where the "webserv" vm image is located 

I am pretty sure that I am not correctly reading the tutorial.

Regards

---

### Post by TheFu on 2019-11-22
I've never used this tool.  

Take a look at the manpage.
```
SYNOPSIS
        virt-resize [--resize /dev/sdaN=[+/-]<size>[%]]
          [**--expand** /dev/sdaN] [--shrink /dev/sdaN]
          [--ignore /dev/sdaN] [--delete /dev/sdaN] [...] indisk outdisk

DESCRIPTION
       Virt-resize is a tool which can resize a virtual machine disk, making
       it larger or smaller overall, and resizing or deleting any partitions
       contained within.

       **Virt-resize cannot resize disk images in-place.**  Virt-resize should not
       be used on live virtual machines - for consistent results, shut the
       virtual machine down before resizing it.

```
If you had the correct options, it still won't do what you want.
two dashes are required for options, not one.
The infile and outfile cannot be the same. If you do that, expect corruption. The tool might allow it, still, expect corruption.
Also looks like you are missing the device inside the guest as an option to --expand.  My guests use virtio, so that would be /dev/vda[?].  If you use SATA/SCSI drivers, then /dev/sda[?]


Looks like the virtio driver doesn't matter to virt-resize:
```
$ sudo virt-filesystems --long --parts --blkdevs -h -a /dev/mapper/hadar--vg-lv--blog44--1604 
Name       Type       MBR  Size  Parent
/dev/sda1  partition  83   487M  /dev/sda
/dev/sda2  partition  05   1.0K  /dev/sda
/dev/sda5  partition  8e   15G   /dev/sda
/dev/sda   device     -    16G   -

```
inside the VM, the storage looks like this:```

$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem                Type  Size  Used Avail Use% Mounted on
/dev/mapper/blog--vg-root ext4   14G  4.8G  7.8G  38% /
/dev/vda1                 ext2  472M  160M  289M  36% /boot

$ sudo parted -l

Model: Virtio Block Device (virtblk)
Disk /dev/vda: 17.4GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  512MB   511MB   primary   ext2         boot
 2      513MB   16.1GB  15.6GB  extended
 5      513MB   16.1GB  15.6GB  logical                lvm


```

---

### Post by Dennis N on 2019-11-22
This step where you expand the filesystem isn't correct:
```
root@serv:/var/vmstorage# virt-resize -expand webserv webserv
```

First,** -expand** should be **--expand**. 
Second, the two arguments following --expand are first the **qcow2 copy** and second the **qcow2 original**. They can't be the same. 

I kept a record of actual commands used when resizing manjaro-xfce.qcow2 by +5 GB. I am omitting all the related output here. Note: **manjaro-xfce-orig.qcow2** is the copy of the original (see second command below). sda2 was the root partition that I needed to expand in this case.
```
sudo qemu-img resize manjaro-xfce.qcow2 +5G
sudo cp manjaro-xfce.qcow2 manjaro-xfce-orig.qcow2
sudo virt-resize --expand /dev/sda2 manjaro-xfce-orig.qcow2 manjaro-xfce.qcow2

```

---

### Post by Heeter on 2019-11-22
Thank you again for your responses


So if I understand correctly, there has to be enough room on the server for a second image to be created? So if it is in my case, I need room for the webserv-orig file and a new webserv+20G?

Can I put the original image into another partition and create the new image+20G into the original image's location? and use the filepath in the command?

Regards

---

### Post by Dennis N on 2019-11-22
> Can I put the original image into another partition and create the new image+20G into the original image's location? and use the filepath in the command?
Yes, the copy you make of the original in the 2nd step could be saved anyplace accessible using a path. The original gets enlarged where it is. Then the contents are copied back to the enlarged disk from the copy you made in step 2. The virt-resize command shown in 3rd step handles all the details of this.  After you are sure the resized disk is working, you can delete the copy made in step 2.

(No risk here because you have the copy of the original made in step #2 in case something fails - but, I've done this 4 times without any problems.)

---

### Post by TheFu on 2019-11-22
The manpage is explicit about the order for the input and output VM files.
```
indisk outdisk
```
The original is the 2nd from last argument and the new disk file is the last.

So, please double check that the version on your system, as the local manpage documents, show the order you expect.

---

### Post by Heeter on 2019-11-22
Hi Guys, Can't thank you enough for your assistance.

Okay, the first 2 steps went okay. The original working vm file is in the "/var/vmstorage/webserv" and the copy/backup is in the "/var/vmbackup/webserv"

I type in the third step:
```

root@serv:/var/vmstorage# virt-resize --expand /dev/sda1 webserv /var/vmstorage/webserv

```

Sorry, I still am having trouble with this.

I got the /dev/sda1 from this:
```

root@serv:/var/vmstorage# virt-filesystems -l -h --all -a webserv
Name                   Type       VFS  Label MBR Size Parent
/dev/webserv-vg/root   filesystem ext4 -     -   98G  -
/dev/webserv-vg/swap_1 filesystem swap -     -   980M -
/dev/webserv-vg/root   lv         -    -     -   98G  /dev/webserv-vg
/dev/webserv-vg/swap_1 lv         -    -     -   980M /dev/webserv-vg
/dev/webserv-vg        vg         -    -     -   99G  /dev/sda1
/dev/sda1              pv         -    -     -   99G  -
/dev/sda1              partition  -    -     8e  99G  /dev/sda
/dev/sda               device     -    -     -   119G -

```

Regards

---

### Post by Heeter on 2019-11-23
HA!!!!

It worked. 

Now I do have another slight situation. I have successfully booted into the webserv vm:

This is what I have now:
```

root@webserv:/home/admin# lsblk
NAME                   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sr0                     11:0    1 1024M  0 rom  
vda                    252:0    0  119G  0 disk 
&#9492;&#9472;vda1                 252:1    0  119G  0 part 
  &#9500;&#9472;webserv--vg-root   253:0    0   98G  0 lvm  /
  &#9492;&#9472;webserv--vg-swap_1 253:1    0  980M  0 lvm  [SWAP]

root@webserv:/home/admin# lvextend -l 100%FREE -r /dev/webserv-vg/root
  New size given (5120 extents) not larger than existing size (25098 extents)

root@webserv:/home/admin# 

```

Is there another way to maximize the /root folder?

Regards

---

### Post by Dennis N on 2019-11-23
> HA!!!! It worked. Is there another way to maximize the /root folder?
None that I'm familiar with or have used other than **lvextend**. There are various ways to express the size of course. Note that on the lvextend man page, lower case -l is shown as abbreviation for **--extents** and upper case -L is abbreviation for **--size**. I usually use **--extents** as the option. See the lvextend man page for all the variations on **--size** or **--extents**. .

---

### Post by Dennis N on 2019-11-23
Based on your information in post #10, your partition is resized, but the pv with webserv-vg isn't. So there is unaccessable space. Based on a look at it's man page and [this web page]("http://ryandoyle.net/posts/expanding-a-lvm-partition-to-fill-remaining-drive-space/"), you can expand the vg with **pvresize** and recover that space:

```
sudo pvresize /dev/sda1
```

Then you can extend the root logical volume with lvextend.

A quote from linked page where a physical disk partition was enlarged on an LVM system:
> After the reboot we use the pvresize command to fill out the extra space. As fair as I can tell, this resizes the amount of space that a LVM volume group can use on a partition and needs to be run if you resize its partition.

This extra step with pvresize is a consequence of using LVM in the VM. I've only been using standard partitions in my personal VMs*.  

*I did once set up a VM with LVM as a trial, but found it took much longer to boot (maybe twice as long) so I abandoned that idea.

---

### Post by Heeter on 2019-11-23
Hi Dennis N.

Cannot thank you enough for helping me with this, I really appreciate it. The information from post 10 has now changed since you showed me how to use those 3 steps
The host KVM server now looks like this:
```

root@serv:/var/vmstorage# virt-filesystems -l -h --all -a webserv
Name                   Type       VFS  Label MBR Size Parent
/dev/webserv-vg/root   filesystem ext4 -     -   98G  -
/dev/webserv-vg/swap_1 filesystem swap -     -   980M -
/dev/webserv-vg/root   lv         -    -     -   98G  /dev/webserv-vg
/dev/webserv-vg/swap_1 lv         -    -     -   980M /dev/webserv-vg
/dev/webserv-vg        vg         -    -     -   119G /dev/sda1
/dev/sda1              pv         -    -     -   119G -
/dev/sda1              partition  -    -     8e  119G /dev/sda
/dev/sda               device     -    -     -   119G -
root@serv:/var/vmstorage# 

```

I reread the lvetend --help over again and I figured out the proper arguments for within the guest vm:
```

root@webserv:/home/admin# lvextend -l +100%FREE -r /dev/webserv-vg/root
  Size of logical volume webserv-vg/root changed from <98.04 GiB (25098 extents) to <118.04 GiB (30218 extents).
  Logical volume webserv-vg/root successfully resized.
resize2fs 1.44.1 (24-Mar-2018)
Filesystem at /dev/mapper/webserv--vg-root is mounted on /; on-line resizing required
old_desc_blocks = 13, new_desc_blocks = 15
The filesystem on /dev/mapper/webserv--vg-root is now 30943232 (4k) blocks long.

root@webserv:/home/admin# lsblk
NAME                   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sr0                     11:0    1 1024M  0 rom  
vda                    252:0    0  119G  0 disk 
&#9492;&#9472;vda1                 252:1    0  119G  0 part 
  &#9500;&#9472;webserv--vg-root   253:0    0  118G  0 lvm  /
  &#9492;&#9472;webserv--vg-swap_1 253:1    0  980M  0 lvm  [SWAP]
root@webserv:/home/admin# 

``` 

So all is good now, THANK YOU!! Dennis N. For all your assistance again. I owe you one\\:D/\\:D/

---

### Post by Dennis N on 2019-11-24
I'm glad to see you have it fixed. Question: Was the command given in post #13 necessary?

---

### Post by Heeter on 2019-11-24
> **Dennis N said:**
> I'm glad to see you have it fixed. Question: Was the command given in post #13 necessary?

I didn't use that command. 

After the 3 step commands, I went into the vm itself and resized there

Regards

---

### Post by Dennis N on 2019-11-24
> **Heeter said:**
> I didn't use that command. After the 3 step commands, I went into the vm itself and resized there...
Great. This is good to know.

---

