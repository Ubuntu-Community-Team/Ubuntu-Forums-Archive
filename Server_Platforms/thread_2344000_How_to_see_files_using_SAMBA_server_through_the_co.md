---
title: "How to see files using SAMBA server through the command line"
date: 2016-11-21
forum: Server Platforms
---

### Post by david472 on 2016-11-21
I have a SAMBA server that I usually see the files through MS WINDOWS (over the network).  Of late, it has not been showing up with my MSWindows network, so I need to get some files from the server directly using USB.  How can i go about copying those files using the command line directly in SAMBA? 

** Also, I have used PUTTY using MSWindows and the server is up and running and connects.
***I also rebooted the server to see if that would help, but it is still not showing up in MSWindows using networking.

I tried at the command line  : DIR and it shows me a file/folder called TEST, when I type CD TEST and go to the directory, and then DIR again, there is nothing in it. This is the only thing listed.

NOTE : I don't know linux, unix or ubuntu.  I remember short commands such as dir and cd, but that is about it.

Any help would be appreciated

---

### Post by darkod on 2016-11-21
Are you trying to copy directly to a usb stick/hdd connected to the server?

Or you want to copy from your samba server to another linux client machine?

For copying directly to usb, it won't even go through samba. Login in your putty ssh session and check all disks including the usb with:
```
sudo parted -l (small L)
```

Lets say that shows your usb stick as /dev/sdc and the first and only partition on it as /dev/sdc1. You need to mount it to any temporary mount point, and it depends if the partition on the usb is fat32 or ntfs.
```
sudo mkdir /mnt/usb   #(make temp mount point)
sudo mount -t vfat /dev/sdc1 /mnt/usb   #(mount a fat32 usb to your mount point or)
sudo ntfs-3g /dev/sdc1 /mnt/usb   #(mount ntfs usb)
```

Once you have it mounted, go to your samba share folder in the linux filesystem:
```
cd /path/sharefolder
ls   #(in linux you list contents with ls, not dir)
cp filename /mnt/usb/   #(that will copy it to your mount point where your usb is mounted)
sudo umount /mnt/usb   #(when finished unmount the usb)
```

That should be it. There are plenty basic tutorials on google how to copy files in linux. The important is to know where you samba folder is, and to correctly mount your usb.

---

