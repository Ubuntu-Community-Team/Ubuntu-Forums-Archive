---
title: "Create RAID 1 for /VAR and /HOME with mdadm"
date: 2019-09-12
forum: Server Platforms
---

### Post by giobaxx on 2019-09-12
Hello guys

I need to install an Ubuntu Workstation that t has three disk. One SSD and Two Mechanical of 2 TB. The request is to install / on  the SSD and **/Home** and /**var** on the mechanical disk in RAID1 in the two Mechanical Disk.

I wanted to try create the RAID Partition using mdadm but i need some clarification and so...basically your help. My first doubt

if i want to have in the RAID  the /VAR and /HOME if for example mt two disk are /dev/sda and /dev/sdb

[LIST]
[*]i have to create in each disk a partition for /HOME and /VAR marked as RAID and then create a volume with mdadm. Once create and md0 raid partition  can i run the normal installation from ubuntu-desktop live
[/LIST]

                                               or
[LIST]
[*]i've just simply mark the disk /dev/sda and /dev/sdb  as RAID create a raid volume and then create the partition during the installation phase?
[/LIST]

---

### Post by SeijiSensei on 2019-09-12
I create two matching partitions on each drive before running mdadm.  If you use fdisk like I do, mark the partitions as type "fd" so that the kernel will recognize them as RAID members during boot.

Usually I just run the regular installer and let it assign /var and /home to the root filesystem.  Then I create the RAID volumes, mount them to some temporary locations, and copy the contents of /var and /home to the RAID volumes.  Then I edit /etc/fstab accordingly.

The other option is to use the entire drive, bond them with mdadm, then use LVM to create two volumes.  In your case I'd go the two partitions route.  /var need not be much bigger than 100 GB unless you have some ginormous SQL databases that would reside in /var/lib. Use the rest for /home.

---

### Post by TheFu on 2019-09-12
I'm an LVM lover.  I'm addicted to the flexibility.

With LVM, I'd do a normal install with LVM selected pointing at the SSD, then reduce the size of the / LV to be 25G.  That would be completely separate from the next steps for the RAID1 parts. If a swap file was created, I'd add a swap LV, mkswap and add it to the fstab and remove the swap file from the fstab.  Use swapoff to remove the swapfile.  I don't know what choices cause a swapfile vs swap LV or swap partition.  Some swap is needed due to kernel issues. The size on a server is debatable, but for a desktop, 4.1G is the target size I setup.  More seems to be a waste and less isn't enough for modern browsers.  I don't use hibernation, ever.  This setup works great with suspended/standby power management, however.

After the install, create a partition on both spinning disks using the full amount of storage, then use LVM to create a PV and a VG that use the entire spinning disks. LVs control the use of storage.  Lastly, I'd create RAID1 LVs of 10G for /var and 10G for /home with ext4 file systems and mount each where needed (after copying over stuff).  Extending LVs is trivial and with lvm+ext4, the file system can be active during this process.  Reducing LVs always needs the file system off-line, but not for expanding if ext4 is used.

```
sudo pvcreate /dev/sd[ab]1
sudo vgcreate data    /dev/sd[ab]1
sudo lvcreate -L 10G  --mirrors 1      -n    varlv       data
sudo lvcreate -L 10G  --mirrors 1      -n    homelv     data
# then create an ext4 file system on each LV and do the normal stuff for moving data over and mounting where needed.

```
Underneath, this uses mdadm code, so it is effectively the same with the same performance, but leaving the flexibility of LVM which includes snapshots which can be used for consistent backups with zero downtime.

If you want fine control over the striping, **lvcreate     --stripes 2     --stripesize 4** can be used. Just add the options you want to the lvcreate above.

Think of LVs as partitions, just really flexible partitions, that can be created, expanded, mounted while the system is running. To extend an LV, use **lvextend  --resizefs**. That will expand both the LV **and** the file system concurrently.  If you decide that RAID1 isn't needed anymore, use lvconvert.  You can also make a normal LV into a mirror, if you like using lvconvert.  LVM has been used in production for 20 yrs. It is extremely stable.  Guides for any Linux distro with LVM will 99.9999999% work on Ubuntu too.

There are some other things you can do by splitting LV mirrors and merging them back later. I've not done these things.

Other methods are fine if you know the exact required sizes for each /var and /home today, then nothing would be gained by using LVM.  If you don't know the sizes, expanding as needed to each LV is about 10 seconds of effort.

---

### Post by TheFu on 2019-09-12
I just noticed this ... /Home is fine, but if you use /home instead, none of the useradd settings would need to be modified.  Unix is case sensitive.

---

### Post by slickymaster on 2019-09-12
*Thread moved to **Server Platforms**.*

---

### Post by giobaxx on 2019-09-12
Unfortunayely the guy want this configuration with the Raid Disk  divided for /home and  /var  (respectively  1.9 TB  and 100 GB).  the unclair question(for me) is do I have to partition the 2 drives first according to the description and then put those partitions in RAID, or can I put the drives in RAID and then partition the RAID drive afterward?

 
i tried the first method:

on sdb i have created two partition with gdisk  **sdb1(for /home) **and **/sdb2(for /var) **both signed [B]as RAID
[/B]on sdc i have created two partition with gdisk  **sdc1(for /home) **and **/sdc2(for /var) **both signed [B]as RAID

[/B]then i run
[B]
mdadm --create /dev/md0 --level=mirror --raid-devices=2 /dev/sdb1  /dev/sdc1
mdadm --create /dev/md1 --level=mirror --raid-devices=2 /dev/sdb2 /dev/sdc2

[/B]Then i started the graphical installer of ubuntu-desktop and i tried to manually create the partitions( where in addition of the raid volume **md0** and **md1** i saw also [B]sdb1 sdb2 sdc1 sdc2). 
[/B]However i have created the **/** partition on the SSD  the** /Home** Partition in **md0 **and **/var** partition on [B]/md1

[/B]but the system does not boot....i don't know if the process i did is correct or simply i made a mistake.....

any idea?

---

### Post by TheFu on 2019-09-12
A 2TB disk doesn't allow for 1.9T and 100GB of usable storage.  There is overhead.

Do the RAID work, post-install.

---

### Post by SeijiSensei on 2019-09-12
As TheFu and I said, install the system first, then partition and create the RAID devices. Don't try to do everything on the initial installation even if it it seems like you can.

I'd create the smaller partitions first, then tell the partitioner to create a second partition that spans the rest of the disk.

And it's /home, not /HOME or /Home.  Linux is case-sensitive.

---

### Post by darkod on 2019-09-12
To point out something else: the array devices /dev/md0 and /dev/md1 will serve as devices for /home and /var. You do NOT create any more partitions after you have created the arrays.

I say this because in your last post you literary say you created the arrays and then you tried creating partitions. I hope this was just a wrong expression because you don't know the terminology. After you have created the initial partitions and created the arrays, you do NOT create any partitions on it any more.

And since you are using Ubuntu Desktop, not Server, I don't know exactly how the graphic installer looks but if it hasn't changed much, in the manual partitioning step you should have options like Use As for /dev/md0 and /dev/md1. Select ext4 for filesystem and the mount point you want for each, and that's it.

Others have suggested to install the OS first but I personally disagree. Seeing how little linux experience you have, it would be more complicated for you to move the /home and /var contents onto the raid later. Because the mount point folders should be empty and sirve only as mount points. Hence, it's much better for you to do this during the install. If you do the OS install only at first, there will already be content populated in those folders.

---

### Post by SeijiSensei on 2019-09-12
On a brand new system /var and /home are tiny. If he mounts the arrays to those mount points, they will hide the underlying files in the original /home and /var.  True, those files will take up unneeded space, but they are small enough to be ignored.  If he's a fastidious sort, he can boot from an installation medium in the Try Ubuntu mode, mount the root device to /mnt, then delete the contents of the old home and var.  In practice I doubt this would ever be an issue.

Suppose he creates /dev/md0 for /var and /dev/md1 for /home with mdadm.  Copying over those directories is as simple as:
```

cd /
sudo mount /dev/md0 /mnt
sudo rsync -av var/* /mnt
sudo umount /dev/md0
sudo mount /dev/md1 /mnt
sudo rsync -av home/* /mnt
sudo umount /dev/md1

```
Next edit /etc/fstab (using nano as root with sudo, "sudo nano /etc/fstab"), and add these lines at the bottom:
```

/dev/md0     /var     ext4     defaults    0 0 
/dev/md1     /home    ext4     defaults    0 0

```

Now reboot.  /home and /var should now be using the arrays.

---

### Post by giobaxx on 2019-09-12
i know is /home and /Home.....and i have created the first partition(100 GB) then i have created a second partition spanned over the rest of the disk.  i think that it does not boot because ubuntu desktop mdadm is not installed x default. We need to install after the first boot

---

### Post by SeijiSensei on 2019-09-13
Yes, mdadm is not part of the distribution for desktop machines.  You need to install it after the initial installation.  The code to manage md devices is in the kernel, though, so it's there by default.

---

### Post by giobaxx on 2019-09-16
hello guys

at the end i used the old way installing ubuntu-server and the installing over the ubuntu-desktop. i also tried to use the new ubuntu-live-server iso that is really much simple to use then older server installer but there's was everytime a different error.

Every time it was  always failing   creating  the raid partition. Basically what i did is the  md0 paritition about 100 GB for /var and md1(/home) for the rest of the disk, but nothing everytime it failed . The only way to make it work was making the partition manually.

Basically i after i did the first partition(md0) instead of saying take the rest of the disk for the md1 i have create manually a partition of 1.7 TB instead of the 1.814 TB available.....

Some other issue using the ubuntu-live-sever it was impossible to get an ip address via DHCP and in some workstation  i had this error:

  [COLOR=#242729][FONT=Consolas]Probing for devices to install to failed[/FONT][/COLOR]-------------------------------------------------
Unfortunately probing for devices to install to failed. Please report a bug on Launchpadm and if possible include the contents of the /var/log/installer directory.....:-(

---

