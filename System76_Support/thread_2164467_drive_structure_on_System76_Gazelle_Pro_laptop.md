---
title: "drive structure on System76 Gazelle Pro laptop"
date: 2013-07-31
forum: System76 Support
---

### Post by golfdiesel on 2013-07-31
I have ordered a System76 Gazelle Pro with a 240GB m-ssd and a 1TB hdd.
What is the default folder structure on a System76 laptop with this config?
I suppose the best thing to do is to leave the SSD for the OS and applications and use the HDD for the other data like the /home folder.

Another thing is that I am thinking about the rest of the data. 
In windows you have your drive letters to differentiate between the drives. Linux doesn't use drive letters which is a good thing in my opinion but you have to think better about the structure.

Assuming the SSD is allready in use for the OS and the /home folder is on the HDD.
I would like to have a folder for photo's on the hdd and a folder for mp3's as wel and let us throw in a folder for video's as well.

I can't simply create folders in the root of the drive (/) because that would cause them to be created on the SSD instead of the HDD.
I need these folders to be accessible for each user on the laptop.
One thing I was thinking about is to create the folders in my /home folder and then create symlinks to the folders of the other users that have to be able to easily access these folders. This might be an easy solution but not the best solution to my taste.
How do I go about this without resorting to creating separate partitions on the hdd. I don't want separate partitions because they are either to big and waste space or you run out of space in one of them so you have to go through the hassle to resize the partitions...

What I want is the following:

SSD -> /
HDD -> /home
HDD -> /photos
HDD -> /music
HDD -> /video

---

### Post by isantop on 2013-07-31
We use a standard Ubuntu partition scheme with the entire system on a single partition. This is easier to reinstall and upgrade (Ubuntu offers to "Reinstall Ubuntu" or "Upgrade Ubuntu XX.XX to YY.YY") without needing manual partitioning, and also ensures you don't run out of space on one parition but not the other. 

For multi-drive systems, we still recommend keeping your home folder on the main drive for two reasons:

1. If the second drive becomes unmountable, you can still log in (because all your config files are still there).
2. Putting /home on a HDD with root on an SSD negates a large part of the performance gain associated with the SSD. You'll get much faster performance with the whole system on one drive.

---

### Post by golfdiesel on 2013-07-31
Ah ok. Thanks.
How is the second drive mounted? If I would keep the /home folder on the ssd then a simple /data mountpoint would suffice for the HDD I guess. Within /data I  can then create whatever folder I need.

---

### Post by isantop on 2013-07-31
The second drive basically acts like a really big flash drive that's always connected. When you click on it the first time, it'll mount to /media/{your username} and stay mounted till you shut down. You can certainly add an entry to /etc/fstab to mount the drive automatically on boot, but it wouldn't show up in Unity or Nautilus as a drive. You would have to actually navigate to the mount point.

---

### Post by golfdiesel on 2013-07-31
Thanks!

---

### Post by golfdiesel on 2013-08-03
I did some experimentation on my current PC with a Ubuntu installation and it seems that I do need to create a fixed mountpoint for my HDD.
If you store pictures on the second drive and you open them in Darktable for example you will run into the problem that the Darktable library can't find the pictures after a reboot because it can't find the drive even if you open the drive before you start the software. The dynamic "mounting" is nice for a flash drive but not for storage that needs to be in the same place for apps to be able to access it after a reboot.

---

### Post by isantop on 2013-08-05
Fair enough. You'll want to create a static mountpoint:

```
sudo mkdir -p /media/static/extra-drive
```

Then add an entry to /etc/fstab to have the partition mount automatically:

```
echo "/dev/sdb1   /media/static/extra-drive   ext4   errors=remount-ro   0        1" | sudo tee -a /etc/fstab
```

Note that you may need to adjust the first item in the above command if "/dev/sdb1" isn't the name of the partition you're setting up. you can double check it by clicking on it to mount it, then running this command:

```
mount
```

which should give you something like this:

```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
/dev/sdb1 on /media/ian/Extra Drive 1 type ext4 (rw)
```

Note that last line; that's what you're looking for. Just make sure there are no flash drives plugged into the system, then run this command and look for the partition that's mounted on "/media/{your user name}/Extra Drive". Plug that line into the second command above.

---

### Post by golfdiesel on 2013-08-05
Thanks for the anwser! Great support!

---

