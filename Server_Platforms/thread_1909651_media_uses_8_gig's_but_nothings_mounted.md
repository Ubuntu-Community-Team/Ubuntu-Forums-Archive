---
title: "/media uses 8 gig's but nothings mounted"
date: 2012-01-15
forum: Server Platforms
---

### Post by andru183 on 2012-01-15
I have the server edition of Ubuntu installed and can't update of install anything because the drive is 100% full. I used:

```

 sudo du -sm -x  /*

``` via ssh and it gave the output:

```

8    /bin
23    /boot
1    /dev
7    /etc
33    /home
0    /initrd.img
188    /lib
0    /lib64
1    /lost+found
1    /media
8435    /meida
1    /mnt
1    /opt
du: cannot access `/proc/21988/task/21988/fd/4': No such file or directory
du: cannot access `/proc/21988/task/21988/fdinfo/4': No such file or directory
du: cannot access `/proc/21988/fd/4': No such file or directory
du: cannot access `/proc/21988/fdinfo/4': No such file or directory
0    /proc
1    /root
8    /sbin
1    /selinux
1    /srv
0    /sys
1    /tmp
724    /usr
271    /var
0    /vmlinuz

```

From what I can tell /media is using over 8 gig's. I deleted the folders in there (I had things set up to mount in there but use /mnt for it now) but it still takes up that space. Am I misunderstanding this output? If not how the hell can I clear that space from the folder. There drive is only 10 gig's so it's too much space for it to be using.

---

### Post by volkswagner on 2012-01-15
You mention media is using 8gig.  According to your output "/meida" is using 8gig.



```
1    /media
8435    /meida
```

What is the output of

```
mount
```


and

```
ls -alt /meida
```

```
ls -alt /media
```

---

### Post by andru183 on 2012-01-15
```

biggboss@biggboss:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/USB type vfat (rw)
/dev/sda5 on /mnt/VAULT type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
biggboss@biggboss:~$ ls -alt /media/
total 12
drwxr-xr-x  3 root root 4096 2012-01-15 20:52 .
drwxr-xr-x 22 root root 4096 2012-01-14 13:03 ..
drwxr-xr-x  2 root root 4096 2012-01-06 18:06 cdrom
biggboss@biggboss:~$ 

```

---

### Post by volkswagner on 2012-01-15
I see you have a usb drive mounted on /media.

```
/dev/sdb1 on /media/USB type vfat (rw)
```

You did not post the output of the remaining commands.

---

### Post by andru183 on 2012-01-15
I noticed that after posting and tried

```

biggboss@biggboss:~$ sudo umount /dev/sdb1
umount: /dev/sdb1: not found

```

So it seems to think /dev/sdb1 is mounted there but there is no usb present physically. Using -f won't unmount it either.

I posted the output of the two commands you asked. What other command was I to post the outout of

---

### Post by volkswagner on 2012-01-15
You don't actually unmount the device.  You unmount the mount point.

so try:

```
sudo umount /media/USB
```

If that fails you can try verbose:

```
sudo umount -v /media/USB
```

or force it

```
sudo umount -f /media/USB
```

---

### Post by volkswagner on 2012-01-15
> **andru183 said:**
> 

I posted the output of the two commands you asked. What other command was I to post the outout of



This one:

```
ls -alt /meida
```

Does this directory exist?  Why is in your original post?

---

### Post by andru183 on 2012-01-15
I had to

```

sudo mkdir /media/USB

```

because I deleted the folder in an attempt to remove the 8 gig's. All I get is

```

biggboss@biggboss:~$ sudo umount /media/USB
umount: /media/USB: not mounted
biggboss@biggboss:~$ sudo umount -v /media/USB
Could not find /media/USB in mtab
umount: /media/USB: not mounted
biggboss@biggboss:~$ sudo umount -f /media/USB
umount2: Invalid argument
umount: /media/USB: not mounted
biggboss@biggboss:~$ 

```

May a logout or reboot will help

---

### Post by volkswagner on 2012-01-15
If you can before you reboot post output of this command then run it again after reboot.

```
df
```

So is /meida a folder or was that a typo in your original post?

---

### Post by andru183 on 2012-01-16
finally got a chance to restart, space is still taken up but now the command output is

```

biggboss@biggboss:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
biggboss@biggboss:~$ ls -alt /meida
total 12
drwxr-xr-x  3 root root 4096 2012-01-14 13:03 .
drwxr-xr-x 22 root root 4096 2012-01-14 13:03 ..
drwxr-xr-x  3 root root 4096 2012-01-14 13:03 VAULT

```

Now nothing mounted in /media but still

```

8    /bin
23    /boot
1    /dev
7    /etc
33    /home
0    /initrd.img
188    /lib
0    /lib64
1    /lost+found
1    /media
8435    /meida
1    /mnt
1    /opt
du: cannot access `/proc/1923/task/1923/fd/4': No such file or directory
du: cannot access `/proc/1923/task/1923/fdinfo/4': No such file or directory
du: cannot access `/proc/1923/fd/4': No such file or directory
du: cannot access `/proc/1923/fdinfo/4': No such file or directory
0    /proc
1    /root
8    /sbin
1    /selinux
1    /srv
0    /sys
1    /tmp
724    /usr
271    /var
0    /vmlinuz

```

---

### Post by andru183 on 2012-01-16
OMG......... sorted it all. I made a spelling mistake when making the mount point. I created it on /meida. That's where the space was taken, not .media. I'm real sorry, thanks for your time and sorry I wasted it

---

### Post by DukeBoxer on 2012-01-16
Look at your output, you have a directory named "/media" and one named "/meida", it's the one spelled wrong that you have 8 gigs in. cd into that directory and find out whats in there taking up all the space. It's not your /media directory and whatever is mounted in it that's the problem.

---

### Post by DukeBoxer on 2012-01-16
hmm...beat me to it

---

### Post by andru183 on 2012-01-16
Thanks anyway duke!

---

