---
title: "Simulating RAID failure inside VirtualBox"
date: 2010-10-13
forum: Virtualisation
---

### Post by memilanuk on 2010-10-13
Windows Vista 64 host, running latest PUEL version of VirtualBox, Linux host.

I have a guest VM running with one 'system' drive and then three 'data' drives in a RAID5 configuration. I wanted to test the response to a drive being removed from the array (failing) with the system in operation, as well as add one back in (ala 'hot swap'), and do other things to the array (grow it, change configuration to RAID6, etc.) Some of these are going to require reboots anyway, so I could shut the VM down and 'disconnect' one of the drives before booting up - but what I wanted to see is how the system reacts to the drive failing while under normal operation, not just on boot up. Also, any suggestions on the best way to abuse a disk image of one of the drives so as to simulate data corruption on the drive and see if it can be detected from the guest OS?

TIA,

Monte

---

### Post by Irregular Joe on 2010-10-20
Physically removing the drive between boots is one way.  The online way that I know of uses the mdadm command (I realize that this doesn't quite simulate a bad disk, but it is the best I know of inside a running virtual machine).


Use this command to see the status of the array:
  cat /proc/mdstat
which produces:
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdc1[1] sdb1[0]
      1060160 blocks [2/2] [UU]

unused devices: <none>
```

You can forcibly mark a drive as failed using the command:
  sudo mdadm /dev/md0 --fail /dev/sdXX
where XX is one of the physical partitions attached to the RAID array.  Looking at /proc/mdstat again shows the failed drive:

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdc1[1] sdb1[2](F)
      1060160 blocks [2/1] [_U]

unused devices: <none>

```

This command is used to remove a drive from the array (after the failure):
  sudo mdadm /dev/md0 --remove /dev/sdXX
Once the replacement has been inserted, add the new drive to the array:
  sudo mdadm /dev/md0 --add /dev/sdXX
The new drive automatically resyncs to the array.  Check /proc/mdstat for the current status of the sync process.

Hope this helps!

---

### Post by memilanuk on 2010-10-20
Well, since physically removing the 'failed' disk isn't possible in this situation, it sounds like using mdadm to remove and restore the drive is about the only option I have.  Not quite what I was looking for; I'd hoped Virtualbox had some way to simulate things like this.  I almost wonder if it'd be possible to 'corrupt' the disk image by writing to it with some other program while the virtual machine is up and running... but I'd imagine it has some sort of lock on the vdi file.

---

### Post by HighInBC on 2011-02-18
Use loop devices for your drives:

[http://blog.mybox.ro/2010/11/03/how-to-use-a-raw-disk-image-file-in-virtualbox/](http://blog.mybox.ro/2010/11/03/how-to-use-a-raw-disk-image-file-in-virtualbox/)

Then you can use "dd" as root to send random data into the disk, or you can alter the permission of the loop device to prevent vbox from accessing it.

---

