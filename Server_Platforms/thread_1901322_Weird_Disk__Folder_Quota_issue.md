---
title: "Weird Disk / Folder Quota issue"
date: 2011-12-28
forum: Server Platforms
---

### Post by kembar4 on 2011-12-28
Hey guys,

So I installed Torrentflux B4rt on my server and want to set different disk quota limits for each folder.

The default directory for downloads is :/usr/local/torrentflux/downloads

For example, lets say there are 3 users on the server. Their default directories would be:

/usr/local/torrentflux/downloads/user1
/usr/local/torrentflux/downloads/user2
/usr/local/torrentflux/downloads/user3

Now, i know there isn't any way (I couldn't really find it) to apply quota limits on folders, So i had this idea. Create a different user on the server and then change the ownership of the folder to that particular user and then apply the quota through webmin.

So i made a user in ubuntu, user1 and setup his password. 

Then, i navigated to /usr/local/torrentflux/downloads/ using root and issued this command:

> chown -hR customer /usr/local/torrentflux/downloads/user1

Then i issued this command to make sure that the folder is writeable

> chmod 777 user1

Then i issued this command to check the ownership of the folder

> 

root@km33133:/usr/local/torrentflux/downloads# ls -l | awk '{print $3}'

user1
www-data


This shows that the other existing file, is owned by www-data by default and the other file has its owner changed to user1. 

Now, i went over to Disk Quota on Webmin and it displayed the current usage for the user user1 correctly. I applied the hardlimit quota to 1GB and then proceeded to download files to that directory. Torrenflux continued to download well over 1GB and there wasn't any issue. On webmin, it shows that the allowed quota has been exceeded but thats about it.

If i were to apply a quota to the user www-data, and once it exceeds it, torrentflux wouldn't be able to download anything until the quota rule has been lifted or the disk space has been cleared.

Why is this happening? :S

---

### Post by rubylaser on 2011-12-28
You could create quotas fairly easily if you wanted.  You just need a partition to apply quotas to.  You could use LVM or something like [this]("http://www.linuxquestions.org/questions/linux-server-73/directory-quota-601140/").  The second method is easy to implement and manage.

---

### Post by kembar4 on 2011-12-28
> **rubylaser said:**
> You could create quotas fairly easily if you wanted.  You just need a partition to apply quotas to.  You could use LVM or something like [this]("http://www.linuxquestions.org/questions/linux-server-73/directory-quota-601140/").  The second method is easy to implement and manage.

Thank you

The second method works.

However, When the torrent is currently downloading, and halts at say, 22.6% because of insufficient disk space, it would freeze at that. Even if the other files are deleted and there is ample space left, the status of the torrent would remain "leeching" but the progress never increases. Trying to stop / delete the torrent from torrentflux b4rt proofs to be futile. I can delete the file from the directory, but the download would still be frozen from the torrentflux interface. Is this a known issue?

---

### Post by rubylaser on 2011-12-28
I don't know about or use Torrentflux B4rt, so hopefully someone else will be able to help you out with that part.  In the past, I used to use Transmission CLI, and I don't think I ever experienced the problem you're describing with that.

---

### Post by kembar4 on 2011-12-28
> **rubylaser said:**
> I don't know about or use Torrentflux B4rt, so hopefully someone else will be able to help you out with that part.  In the past, I used to use Transmission CLI, and I don't think I ever experienced the problem you're describing with that.

Ah thank you. I'll try Transmission.

Anyways, i switched to rutorrent and i did notice something, whenever i reboot the server, the virtual disk gets unmounted.

I have to manually mount it. Its easy to do it for a user or two, but would become a hassle if more mounts are present.

How do i go about if i want to mount these virtual disks automatically after every reboot?

Command to launch upon reboot:

mount -o loop,rw,usrquota,grpquota /var/virtual_disks/MYFILE.ext3 /home/MYMOUNTPOINT

---

### Post by rubylaser on 2011-12-28
You'd want to create an [init script]("http://www.debian-administration.org/articles/28").

```
sudo -i
nano /etc/init.d/virtual_drive_mounter

```
paste in your mounts
```
#! /bin/bash
mount -o loop,rw,usrquota,grpquota /var/virtual_disks/MYFILE.ext3 /home/MYMOUNTPOINT
```
then,
```
chmod +x /etc/init.d/virtual_drive_mounter
```
And, set it up to autostart.
```
update-rc.d virtual_drive_mounter defaults
```

---

### Post by kembar4 on 2011-12-28
> **rubylaser said:**
> You'd want to create an [init script]("http://www.debian-administration.org/articles/28").

```
sudo -i
nano /etc/init.d/virtual_drive_mounter

```
paste in your mounts
```
#! /bin/bash
mount -o loop,rw,usrquota,grpquota /var/virtual_disks/MYFILE.ext3 /home/MYMOUNTPOINT
```
then,
```
chmod +x /etc/init.d/virtual_drive_mounter
```
And, set it up to autostart.
```
update-rc.d virtual_drive_mounter defaults
```

Thank you very much! I shall try this later :)

I found another issue though when creating the virtual disk if its going to be bigger than 1GB.

Say i want to create a virtual mount of 10GB,

Issuing the command

> dd if=/dev/zero of=/var/virtual_disks/directory_with_size_limit.ext3 bs=10GB count=1

Gives me the error of Out of memory.

To circumvent that, I did this:

> dd if=/dev/zero of=/var/virtual_disks/directory_with_size_limit.ext3 bs=1GB count=10

This made the mount 10GB. However, I am wondering if this is the correct way to do it or is there a better way?

---

### Post by rubylaser on 2011-12-28
Just do it this way.  It should create a 10GB file instantly :)
```
dd if=/dev/zero of=/var/virtual_disks/directory_with_size_limit.ext3 bs=1000 count=0 seek=$[1000*1000*10]
```

---

### Post by kembar4 on 2011-12-28
> **rubylaser said:**
> Just do it this way.  It should create a 10GB file instantly :)
```
dd if=/dev/zero of=/var/virtual_disks/directory_with_size_limit.ext3 bs=1000 count=0 seek=$[1000*1000*10]
```

Is the output correct?

```
sudo dd if=/dev/zero of=/var/virtual_disks/MYFILE.ext3 bs=1000 count=0 seek=$[1000*1000*10]
```

> 0+0 records in
0+0 records out
0 bytes (0 B) copied, 1.7752e-05 s, 0.0 kB/s

Edit: weird. Doing it this way, once i've mounted everything, new torrents being added to rutorrent would be queued and not download as before. Perhaps its because of the mount being 0 bytes?

---

### Post by rubylaser on 2011-12-28
Yup, you can verify the size like this...
```
ls -lh /var/virtual_disks/directory_with_size_limit.ext3
```

---

### Post by kembar4 on 2011-12-28
> **rubylaser said:**
> Yup, you can verify the size like this...
```
ls -lh /var/virtual_disks/directory_with_size_limit.ext3
```

Just found out that i had to chmod 777 the download directory.

Thank you very much. After trying, it works flawlessly.

Perhaps, a last question..

If i were to delete the mount, all i have to do is issue these commands below, right? :

```
sudo umount /path/of/mount/point
```

and

```
sudo rm -r directory_with_size_limit.ext3
```

---

### Post by rubylaser on 2011-12-28
> **kembar4 said:**
> Just found out that i had to chmod 777 the download directory.

Thank you very much. After trying, it works flawlessly.

Perhaps, a last question..

If i were to delete the mount, all i have to do is issue these commands below, right? :

```
sudo umount /path/of/mount/point
```

and

```
sudo rm -r directory_with_size_limit.ext3
```

It looks good, but you need to force the removal of a directory to actually remove it.
```
sudo rm -rf directory_with_size_limit.ext3
```

---

### Post by rubylaser on 2011-12-28
I'm glad you got it working :) Also, don't forget to mark the thread as solved under the Thread tools at the top if you'd be so kind.

---

### Post by kembar4 on 2011-12-28
> **rubylaser said:**
> I'm glad you got it working :) Also, don't forget to mark the thread as solved under the Thread tools at the top if you'd be so kind.

Sure, everything works very well now.

Thank you very much once again for your help. It wouldn't be possible without you.

I'll add the solved tag as requested.

---

