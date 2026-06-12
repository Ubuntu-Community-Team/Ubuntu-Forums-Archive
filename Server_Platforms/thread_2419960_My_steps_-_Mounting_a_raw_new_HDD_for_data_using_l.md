---
title: "My steps - Mounting a raw new HDD for data using logical partitions..."
date: 2019-05-27
forum: Server Platforms
---

### Post by aljames2 on 2019-05-27
Posting the steps I used that worked for me.  It may not be what everyone wants or needs.  In my case I was looking for a How To and eventually put this together.  This is not a RAID setup, and it is not a traditional fixed partitioned drive.  Instead, its using Ubuntu's LVM to manage my data partitions.  It may not be the best way but I like it :)

Special thanks to LHammond's Ubuntu 18.04 Installation tutorial [http://hammondslegacy.com/forum/viewtopic.php?f=40&t=244](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=244) which helped get my system installed; and, TheFu's many forum posts & responses to many of my questions helped get me in the right direction.

Experts, feel free to roast me here or suggest changes/edits to make it better.

I have my Ubuntu 18.04.2 server installed on an 250gb SSD (overkill I know but that's what I had).  At installation I installed and manually configured partitions using LVM and separated my system folders into separate logical partitions.

Next I wanted to attach a new internal HDD for data storage.  Unfortunate at start of the project I purchased the odd 3TB WD-Red drive.  I'll be sure to keep it backed up regularly.  I've learned here that odd sizes have shown higher than normal failure rates according to various online statistics.  Anyway, I've moved forward with the plan and attached the new drive.  Next follows the steps I performed from A-Z...

Entered root mode for the process, so I wouldn't have to type sudo in front of every command:
```
sudo su
```
Get intelligence on my new attached drive.  Made note of the logical name /dev/sdb
```
lshw -C disk
```

          *-disk
               description: ATA Disk
               product: WDC WD30EFRX-68N
               vendor: Western Digital
               physical id: 0.0.0
               bus info: scsi@2:0.0.0
               logical name: /dev/sdb
               version: 0A82
               serial: WD-WCC7K0FE1xxx
               size: 2794GiB (3TB)
               configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096

Enter GNU Parted utility to assist with new drive setup.  Used Parted vs. fdisk due to limitations fdisk has on drives over 2TB.
    ```
parted /dev/sdb

GNU Parted 3.2
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
```

Create new GPT disklabel
    ```
(parted) mklabel gpt
```
```
(parted) unit TB
```
    ```
(parted) mkpart

Partition name?  []? primary
File system type?  [ext2]? ext4
Start? 0
End? 3  
(this start/end range creates 1 partition on the 3TB drive)

```

Set LVM flag on the single partition
```
(parted) set 1 lvm on
```

View drive status
```
(parted) print
            
Model: ATA WDC WD30EFRX-68N (scsi)
            Disk /dev/sdb: 3.00TB
            Sector size (logical/physical): 512B/4096B
            Partition Table: gpt

            Disk Flags:
            Number  Start   End         Size        File system   Name          Flags
            1        0.00TB   3.00TB    3.00TB     ext4           primary        lvm

```

Save & exit Parted utility
    ```
(parted) quit

Information: You may need to update /etc/fstab.
(will do this a little later on)

```

Now that the LVM partition is created, need to initialize it as a physical volume
    ```
pvcreate /dev/sdb1
        Physical volume "/dev/sdb1" successfully created.
```

Now create the Volume Group name.  In my case I used only 1 name but you can use more than 1
    ```
vgcreate WD-vg1 /dev/sdb1
        Volume group "WD-vg1" successfully created
```

Now create your Logical Volumes & allocate some free space in the volume group.  In my case I set up 4 logical volumes
    ```
lvcreate -n projects -L 10g WD-vg1
        Logical volume "projects" created.
```
    ```
lvcreate -n media -L 50g WD-vg1
        Logical volume "media" created.
```
    ```
lvcreate -n cloudy -L 5g WD-vg1
        Logical volume "cloudy" created.
```
    ```
lvcreate -n dfay -L 200g WD-vg1
        Logical volume "dfay" created.
```

Now verify output of following commands
    ```
pvs
vgs
lvs
```

Now format each logical partition
    ```
mkfs.ext4 /dev/WD-vg1/projects
mkfs.ext4 /dev/WD-vg1/media
mkfs.ext4 /dev/WD-vg1/cloudy
mkfs.ext4 /dev/WD-vg1/dfay
```

Now make directories to mount the partitions to.  Name your directories however you want
    ```
mkdir /mnt/projects-mount  /mnt/media-mount /mnt/cloudy-mount /mnt/dfay-mount
```

Now edit the /etc/fstab to automatically mount the partitions at boot
    ```
nano /etc/fstab
```
I added the following 4 lines at the end of my /etc/fstab file and saved it.  CAUTION HERE:  make sure what you enter is right for YOU, this can cause the system to not boot.  In fact I did not enter the right stuff here at first and had to use maintenance mode to edit the file and correct.
        ```
/dev/WD-vg1/projects /mnt/projects-mount ext4 defaults 0 2 
/dev/WD-vg1/media /mnt/media-mount ext4 defaults 0 2 
/dev/WD-vg1/cloudy /mnt/cloudy-mount ext4 defaults 0 2 
/dev/WD-vg1/dfay /mnt/dfay-mount ext4 defaults 0 2 
```

Manually mount now
    ```
mount -a
```

Verify the mounts
    ```
df -h
```

Reboot
    ```
reboot now
```

After reboot, view & verify the mounts again
    ```
lsblk
```

My df -h output:
```
Filesystem                    Size  Used Avail Use% Mounted on
udev                          3.9G     0  3.9G   0% /dev
tmpfs                         787M  1.1M  785M   1% /run
/dev/mapper/LVG-root          2.0G  1.4G  452M  76% /
/dev/mapper/LVG-usr           3.0G  1.2G  1.7G  40% /usr
tmpfs                         3.9G     0  3.9G   0% /dev/shm
tmpfs                         5.0M     0  5.0M   0% /run/lock
tmpfs                         3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/mapper/LVG-tmp           984M  2.8M  932M   1% /tmp
/dev/mapper/LVG-var           2.0G  461M  1.4G  25% /var
/dev/mapper/LVG-opt           2.0G  1.1G  867M  55% /opt
/dev/mapper/LVG-bak           2.9G  3.1M  2.8G   1% /bak
/dev/mapper/LVG-srv           989M  2.7M  939M   1% /srv
/dev/mapper/LVG-home          481M  2.3M  453M   1% /home
/dev/sda2                     462M  279M  160M  64% /boot
/dev/sda1                     476M  6.1M  470M   2% /boot/efi
/dev/mapper/WD--vg1-media      49G   53M   47G   1% /mnt/media-mount
/dev/mapper/WD--vg1-projects  9.8G   37M  9.3G   1% /mnt/projects-mount
/dev/mapper/WD--vg1-dfay      196G   61M  186G   1% /mnt/dfay-mount
/dev/mapper/WD--vg1-cloudy    4.9G   20M  4.6G   1% /mnt/cloudy-mount
tmpfs                         787M     0  787M   0% /run/user/1000

```

My lsblk output:
```
NAME                 MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                    8:0    0 232.9G  0 disk
&#9500;&#9472;sda1                 8:1    0   476M  0 part /boot/efi
&#9500;&#9472;sda2                 8:2    0   477M  0 part /boot
&#9492;&#9472;sda3                 8:3    0   232G  0 part
  &#9500;&#9472;LVG-root         253:0    0     3G  0 lvm  /
  &#9500;&#9472;LVG-usr          253:1    0     4G  0 lvm  /usr
  &#9500;&#9472;LVG-var          253:6    0     3G  0 lvm  /var
  &#9500;&#9472;LVG-tmp          253:7    0     2G  0 lvm  /tmp
  &#9500;&#9472;LVG-bak          253:8    0     4G  0 lvm  /bak
  &#9500;&#9472;LVG-srv          253:9    0     2G  0 lvm  /srv
  &#9500;&#9472;LVG-opt          253:10   0     4G  0 lvm  /opt
  &#9492;&#9472;LVG-home         253:11   0     1G  0 lvm  /home
sdb                    8:16   0   2.7T  0 disk
&#9492;&#9472;sdb1                 8:17   0   2.7T  0 part
  &#9500;&#9472;WD--vg1-projects 253:2    0    10G  0 lvm  /mnt/projects-mount
  &#9500;&#9472;WD--vg1-media    253:3    0    50G  0 lvm  /mnt/media-mount
  &#9500;&#9472;WD--vg1-cloudy   253:4    0     5G  0 lvm  /mnt/cloudy-mount
  &#9492;&#9472;WD--vg1-dfay     253:5    0   200G  0 lvm  /mnt/dfay-mount
sdc                    8:32   0   2.7T  0 disk

```

As you can see, I have an sdc waiting to be set up which will be my tier 1 backup.  Then I'll use another mobile drive for another backup.

---

### Post by TheFu on 2019-05-28
Nice.  I'd do a few things slightly different, but nothing "wrong" with what is posted above.

sudo su --->   **sudo -i**  # this gets the root environment which is much safer for most needs.

For all the partitioning stuff, 2 comments.

a) **fdisk** doesn't have the 2TB limitation since around 14.04. Also fdisk works with GPT stuff now.

b) If you are on a desktop, I'd use **gparted** for all the partition needs.  Servers, without GUIs, need to use parted or fdisk.  Always choose 1MB boundaries for where partitions start. It really should be automatic, but misaligned partitions can cause performance issues on spinning disks.  fdisk will complain if partitions aren't aligned, but that might require a reboot to get the OS to refresh the partition data. I'm not certain.
fdisk -l complains like this:```

Partition 4 does not start on physical sector boundary.
Partition 5 does not start on physical sector boundary.
```
parted does not complain on the same disk. Not good.

A few items about LVs.  Only allocate what you need. LVM makes adding more storage to an LV trivial. I like to leave at least 10G free in a VG so it can be added where needed later. Gives me a little warning that more/larger storage is needed before it becomes an emergency.
SSDs should last much longer of the SSD storage isn't fully used. Extra unused storage lets the wear levelling have more working room - try for 20% unused on SSDs.

Before mounting, with ext3/4 file systems, might want to reduce the number of reserved blocks using the **tune2fs** command. Only do this on data file systems, never on the OS file system(s). The default is 5%, but 5% on 1TB partition is HUGE!  The tune2fs manpage explains why this is reserved for use only by root.  On a Unix system, having a full /var/ or /tmp/ is really, really, really, really, bad.  The OS will crash.

/mnt/ is for temporary, admin, mounting use according to the Linux File System Hierarchy Standards document.  That would be perfect for use if the admin is manually mounting things for a few hours to put data on or off the storage, but probably best to avoid using it in any fstab if the system isn't just for home use. At home, do whatever you want.

fstab entries. Many people like to use the *noatime* option on all disks to reduce wear for both.  Might want *nodev* as another option.  SSDs might want SSD specific options.  I use *errors=remount-ro,noatime* for all LV storage. If there is an issue, I'd rather have read-only access to the files than not have it mounted.

df -h  ----> **df -hT|grep '^/dev'**
I find that command gets me just a little more data for partitions/LVs I care about and removes stuff I don't need to see if I'm only dealing with storage.  I don't need to see any loop or pseudo-file systems, just those actually using physical storage. Anyway, make an alias for that command so you don't have to type it out all the time. Add this do your ~/.bash_aliases file or where ever you put your aliases.
```
alias dft="df -hT|grep '^/dev'"
```

Happy to see that backups are part of the plan.  My rule is that if I don't have a way to backup an LV/partition, then I don't bring it online. Backups are a completely different topic. ;)

Nice steps.

---

### Post by aljames2 on 2019-05-28
Thanks for the additional info.  Will make a few tweaks. :)

When I have used Gparted on my desktops it was easy to find the boundary setting and set the 1mb boundaries.  How do you do this using Parted on command line?  I think I had parted in interactive mode and it didn't seem to prompt for this.

---

### Post by TheFu on 2019-06-03
1MB boundaries are simple math.  If you always start of a 1MB boundary and make every partition an even 1MB size, then all of them will be on those boundaries.

---

### Post by aljames2 on 2019-07-01
problem with tune2fs on my spinning HDD (sdb1) for data storage...

I first unmounted the the LMVs and then deactivated the volume group with:  ```
vgchange -a n WD-vg1
```

Then, when running the following tune2fs command: ```
tune2fs -m3 /dev/sdb1
```

I get this in return:
```

tune2fs 1.44.1 (24-Mar-2018)
tune2fs: Bad magic number in super-block while trying to open /dev/sdb1
/dev/sdb1 contains a LVM2_member file system

```

Not sure if I did this correctly.  I was trying to umount the filesystem first before running the tune2fs command.

---

### Post by Dennis N on 2019-07-02
tune2fs is a tool for ext file systems. sdb1 is an lvm physical volume, so isn't formatted with an ext filesystem. Run parted -l to see this, or look at gparted display. (The error message also tells you this. "/dev/sdb1 contains a LVM2_member file system")

You should use the command on the logical volumes instead, like:

sudo tune2fs -m3 /dev/WD-vg1/media

---

### Post by aljames2 on 2019-07-04
sdb1 is a separate data storage only drive.  Is reducing reserve space (tune2fs -m) helpful if the drive is configured as an lvm?  With lvm the cap is set for the volume at first, well below the drive capacity, and is expandable as needed.

---

