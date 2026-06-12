---
title: "File Server Help"
date: 2012-09-06
forum: Server Platforms
---

### Post by DownTheRoad on 2012-09-06
Okay I have a File Server with the following Setup
300gb drive (ubunutu server 12.04)
300gb drive
300gb drive
600gb raid 

I need to mount the other drives, however the all have NTFS partitions on them and I dont want to dump the files just yet. How do I mount them and then share them to the other linux machines? Thanks!

---

### Post by SeijiSensei on 2012-09-07
Make a bunch of mount points in /mnt, then mount the partitions to them.

```

sudo mkdir /mnt/test1 /mnt/test2 /mnt/test3 /mnt/test
sudo mount -t ntfs /dev/xxx /mnt/test1
sudo mount -t ntfs /dev/yyy /mnt/test1

```

Once you've mounted the drives, you'll be able to list the directories with "ls /mnt/test1" or view them from a file manager like Nautilus or Dolphin.

You would replace xxx and yyy with partition names like /dev/sdb1 or /dev/sdd2.  The boot drive is usually /dev/sda, and the remaining disks are named /dev/sdb, /dev/sdc, etc.  If you run the command "sudo blkid" it will construct a census of all "block devices" on the machine.  Here's the result from a server I have with a lot of devices attached:

```

/dev/mapper/VolGroup00-LogVol01: TYPE="swap" 
/dev/mapper/VolGroup00-LogVol00: UUID="cbed55f9-2c28-4faf-b35c-14d7872f6bde" TYPE="ext3" 
/dev/sda1: LABEL="/boot" UUID="e05e19e6-381c-48d6-84e4-88195bcc4d5f" TYPE="ext3" 
/dev/sde1: UUID="b545ec27-aa36-409b-affd-6d1c290a3ea0" TYPE="ext3" 
/dev/sdf1: UUID="87591c15-c60d-41bb-9b38-ba70ea75897b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdf2: UUID="750605cf-732c-496d-a3af-be47ccdc3bd0" TYPE="ext3" 
/dev/sdg1: UUID="87591c15-c60d-41bb-9b38-ba70ea75897b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdg2: UUID="750605cf-732c-496d-a3af-be47ccdc3bd0" TYPE="ext3" 
/dev/md0: UUID="750605cf-732c-496d-a3af-be47ccdc3bd0" TYPE="ext3" 
/dev/VolGroup00/LogVol01: TYPE="swap" 
/dev/sdb1: UUID="d8cd388a-a560-4b30-8b57-312e785c2555" TYPE="ext4" 
/dev/VolGroup00/LogVol00: UUID="cbed55f9-2c28-4faf-b35c-14d7872f6bde" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdh1: UUID="1800e808-e651-4ac0-8c9d-dc3f6d13b0c8" SEC_TYPE="ext2" TYPE="ext3" 

```

The /dev/mapper devices use [Logical Volume Management]("http://tldp.org/HOWTO/LVM-HOWTO/") which runs on top of one or more actual physical devices.  It's unlikely you'll have any of those.  The "UUIDs" are unique identifiers created during partitioning.  The /dev/sdX designators are allocated by the system as devices are discovered.  If you plug a USB mass storage device into the machine, you'll get the next letter in the /dev/sd[a-z] sequence.  The UUIDs are immutable.

The RAID device is a trickier matter.  If it's a true hardware RAID device, then it should appear as a single device with the same kind of /dev/sdX designation as a single drive would.  If it uses so-called "fake RAID" then the RAID management is actually handled in software running on the machine.  In this case the device may rely on a driver in Windows that has no Linux equivalent.  If it uses Linux software RAID, it will appear as /dev/mdX like the /dev/md0 entry above.

---

### Post by SeijiSensei on 2012-09-07
Make a bunch of mount points in /mnt, then mount the partitions to them.

```

sudo mkdir /mnt/test1 /mnt/test2 /mnt/test3 /mnt/test
sudo mount -t ntfs /dev/xxx /mnt/test1
sudo mount -t ntfs /dev/yyy /mnt/test1

```

Once you've mounted the drives, you'll be able to list the directories with "ls /mnt/test1" or view them from a file manager like Nautilus or Dolphin.

You would replace xxx and yyy with partition names like /dev/sdb1 or /dev/sdd2.  The boot drive is usually /dev/sda, and the remaining disks are named /dev/sdb, /dev/sdc, etc.  If you run the command "sudo blkid" it will construct a census of all "block devices" on the machine.  Here's the result from a server I have with a lot of devices attached:

```

/dev/mapper/VolGroup00-LogVol01: TYPE="swap" 
/dev/mapper/VolGroup00-LogVol00: UUID="cbed55f9-2c28-4faf-b35c-14d7872f6bde" TYPE="ext3" 
/dev/hda1: LABEL="/boot" UUID="e05e19e6-381c-48d6-84e4-88195bcc4d5f" TYPE="ext3" 
/dev/hde1: UUID="b545ec27-aa36-409b-affd-6d1c290a3ea0" TYPE="ext3" 
/dev/hdf1: UUID="87591c15-c60d-41bb-9b38-ba70ea75897b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdf2: UUID="750605cf-732c-496d-a3af-be47ccdc3bd0" TYPE="ext3" 
/dev/hdg1: UUID="87591c15-c60d-41bb-9b38-ba70ea75897b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdg2: UUID="750605cf-732c-496d-a3af-be47ccdc3bd0" TYPE="ext3" 
/dev/md0: UUID="750605cf-732c-496d-a3af-be47ccdc3bd0" TYPE="ext3" 
/dev/VolGroup00/LogVol01: TYPE="swap" 
/dev/sdb1: UUID="d8cd388a-a560-4b30-8b57-312e785c2555" TYPE="ext4" 
/dev/VolGroup00/LogVol00: UUID="cbed55f9-2c28-4faf-b35c-14d7872f6bde" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdh1: UUID="1800e808-e651-4ac0-8c9d-dc3f6d13b0c8" SEC_TYPE="ext2" TYPE="ext3" 

```

The /dev/mapper devices use [Logical Volume Management]("http://tldp.org/HOWTO/LVM-HOWTO/") which runs on top of one or more actual physical devices.  It's unlikely you'll have any of those.

The RAID device is a trickier matter.  If it's a true hardware RAID device, then it should appear as a single device with the same kind of /dev/sdX designation as a single drive would.  If it uses so-called "fake RAID" then the RAID management is actually handled in software running on the machine.  In this case the device may rely on a driver in Windows that has no Linux equivalent.  If it uses Linux software RAID, it will appear as /dev/mdX like the /dev/md0 entry above.

As for sharing, you can use [NFS]("https://help.ubuntu.com/12.04/serverguide/network-file-system.html") or [Samba]("https://help.ubuntu.com/12.04/serverguide/windows-networking.html").  NFS is the preferred method for file sharing among Unix-like machines, but I've never tried sharing an NTFS drive via NFS.  NTFS uses its own proprietary method for handling things like permissions which the Linux ntfs driver can handle for local access.  You'll have to experiment or get some help from others here about whether NFS will work with NTFS drives mounted in Linux.

---

### Post by DownTheRoad on 2012-09-07
Mounted everything! I was going to set up an SSH server to share locally and so I can remotely ssh in and access the shares. Is this the best way to go with it? The system is older..... Dual AMD XP 2800+ 32 bit procs, everyone still uses IDE right? lol

---

### Post by arrrghhh on 2012-09-07
> **DownTheRoad said:**
> Mounted everything! I was going to set up an SSH server to share locally and so I can remotely ssh in and access the shares. Is this the best way to go with it? The system is older..... Dual AMD XP 2800+ 32 bit procs, everyone still uses IDE right? lol

SSH would be useful for accessing and managing the **server** itself.

If you just want to access the files and are on a LAN, look at NFS or Samba to share files on a LAN.

However, SSH does have SFTP built in - so it can be used for sharing files - it's just not very efficient compared to the other protocols if you're on a LAN ;).

---

### Post by DownTheRoad on 2012-09-07
However if I am ssh-ing in from outside the LAN to securely access my files would ssh be the best?

Edit: To be more blunt, If I must pass threw a WAN cloud to get to the server, is SSH a good option to use for file transfer?
Sorry I need coffee. Thanks for the help all.

---

### Post by arrrghhh on 2012-09-07
> **DownTheRoad said:**
> However if I am ssh-ing in from outside the LAN to securely access my files would ssh be the best?

Edit: To be more blunt, If I must pass threw a WAN cloud to get to the server, is SSH a good option to use for file transfer?
Sorry I need coffee. Thanks for the help all.

Yes, it is a good option for over the WAN.  It's called 'SFTP' or secure file transfer protocol.  It's based on SSH - so if you have SSH setup, you also have SFTP setup.

---

