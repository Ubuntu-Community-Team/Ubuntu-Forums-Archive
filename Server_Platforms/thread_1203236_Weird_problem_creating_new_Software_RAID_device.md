---
title: "Weird problem creating new Software RAID device"
date: 2009-07-03
forum: Server Platforms
---

### Post by psypher on 2009-07-03
Hi All,

Having a strange one.

I have installed a Jaunty Desktop with root on RAID 5. I understand this is the server section of the forum but since RAID is more of a server thing i thought I'd post it here. My apologies if that's wrong.

Setup is as follows:

3 X 80GB drives split accordingly:
1 X 100MB boot partition
1 X 700MB swap partition
1 X 79GB raid partition

3 X 79GB RAID partitions in RAID 5

boot is only on one partition and each drive has a swap partition so 3 X 700MB for swap

This setup seems to be working beautifully. I am able to boot and run the server no problem. followed a howtoforge article to get the boot process to mount the md0 device so that root is accessible. With the live cd you have to chroot to the md0 device and install mdadm.

now here is the problem. I am trying to create a new md1 device from other drives I have installed in the server. I have tried raid 0, 1 and 5 and nothing will work. Creating the md1 device works fine and syncs fine as well. i am able to mount it too and write data. Problem is as soon as the server reboots that device just breaks. instead of seeing md1 as a valid raid device a new raid device gets created as md_p1 with only one valid drive and it's inactive and unmountable.

I have tried recreating the new raid from scratch, running mdadm --zero-superblock /dev/sdX1 on all drives and then deleting the partitions and starting again and still same issue occurs. Even tried dd if=dev/zero of/dev/sdX bs=1MB count=10 in case there is some md details left behind but still the same.

now here's the strange thing. When I tried this with RAID 5 and rebooted the device still came up as md1_p1. So I thought let me try do all of this with the live cd instead of using the installed OS. When I booted into the live cd suddenly the md1 device is there and synced and running fine.

So for some reason the installed OS just does not understand this new device. It's weird as I haven't even installed updates so it's essentially the same as the live cd. I had a look through the messages log but nothing shows anything going wrong. Also tried mdadm --assemble /dev/md1 as well as creating a proper /etc/mdadm.conf file, no difference.

Looked around on the net but nothing refers to this problem. few posts about md_p1 devices but it seems to refer to some other problems not related to what i am seeing

Any clues?

Thanks

---

### Post by retatkcid on 2009-07-03
Found this by a recommendation here:

[http://ubuntuforums.org/showthread.php?t=1201075&highlight=raid+fails+at+boot](http://ubuntuforums.org/showthread.php?t=1201075&highlight=raid+fails+at+boot)

I'm having a RAID issue, too. It began after applying an update to Ubuntu 9.04 kernel 2.6.28-11 to Ubuntu 9.04 kernel 2.6.28-13.  My RAID array is not recognized and at first, I received an fschk error.  I went back through the process to re-assemble the array, disabled fschk for the device, and was able to mount it as root.  However, after ensuring that mdadm.conf and fstab were correct and rebooting, the array was once again unavailable.  The array is also not available when booting into the previous kernel.

My guess at this point is that this is probably due to a bug in the kernel but, truthfully, I don't know.  I dual boot with OpenSUSE 11.0.  The array is set up to be available at boot in OpenSUSE, as well, and I've have had no problems accessing the device there.  However, I had recently grown weary with constant niggles in OpenSUSE and installed Ubuntu 9.04 to see if I would be happier, intending to make the move permanent if so.

Additionally, I am also now experiencing strange temporary system freezing in Ubuntu.  The mouse seems to work but, sometimes there is no response to any actions for as long as a minute.

I spent a long time tweaking Ubuntu to my taste and am somewhat miffed at the waste of time.  Maybe I should just chuck it all and have a Mint.

---

### Post by littlegreiger on 2009-07-03
I had a similar problem, it had to do with having the raid config in the wrong file. However, as you already have one raid set running fine I don't see how that could be the problem.
Anyways, the way I fixed it was to add the raid config to /etc/mdadm/mdadm.conf by running
```
sudo mdadm --detail --scan --verbose >> /etc/mdadm/mdadm.conf
```
This might fix your problem, can't guarantee that it will though. 
Maybe try reading my last thread about this and see if anyone's comments can help you, it's located here [http://ubuntuforums.org/showthread.php?t=1178826]("http://ubuntuforums.org/showthread.php?t=1178826")
Hope something I posted helps.

---

### Post by retatkcid on 2009-07-08
Probably not nice to do this but, I wanted to make a note here in he event I forget to do so later.

Comparing /etc/mdadm/mdadm.conf with versions on different machines, I found significantly more configuration text in the version that seemed problematic.  The other versions (openSUSE machines) contained only one line under "DEVICE partitions" that defined the array device, level and UUID.  So, I backed up the problematic version and reran the following quick set of commands I found previously written by someone else to reassemble and mount the array which created a similar file:


# Firstly, you'll need to have the mdadm package installed. This provides the /sbin/mdadm command to build, assemble, and manage md arrays. I dont know if it is by default on Ubuntu.

# Next, identify which drives/partitions are to be assembled. Do this via

```
sudo fdisk -l
```

Software raid partitions should say "software raid autodetect"

# Next, assemble the array. Example:

```
sudo mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 
```

(substitute the device names for sda1 & sdb1 for the appropriate devices on your system)

# At this point, you can check the status of the array by running 

```
cat /proc/mdstat
```

as well as mount it with 

```
sudo mount /dev/md0 /mnt/somemountpoint
```

# Configure the mdadm configuration file so that the array is assembled on boot.(If that is what you want):

```
sudo mdadm --examine --scan | sudo tee -a /etc/mdadm/mdadm.conf 
```

My mdadm.conf file now contains only one line similar (different UUID) to the following:

> ARRAY /dev/md0 level=raid1 UUID=917ac304:b146fcd7:af7a4099:d032aaee

Apparently, "DEVICE" line is not required to precede the "ARRAY" line. According to the man page for mdadm.conf, "If no DEVICE line is present, then "DEVICE partitions" is assumed."  It wasn't created when creating the file from scratch using the commands above.  However, if I still have an issue of the array not mounting after next reboot, I suppose adding it to reflect the mdadm.conf file on my openSUSE boxes can't hurt.

> DEVICE partitions
ARRAY /dev/md0 level=raid1 UUID=917ac304:b146fcd7:af7a4099:d032aaee

Anyway, it seems to now work.  The array is mounted and accessible.  I'll have to wait until I clear 40+ browser windows to see if it sticks on next reboot. [-o<

---

### Post by retatkcid on 2009-07-08
Reboot came early.  Thunderstorms, power blips, and dead UPS battery. :-({|=

Array is now available after a forced reboot.  :biggrin:

---

