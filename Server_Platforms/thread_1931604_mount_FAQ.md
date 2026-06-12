---
title: "mount FAQ"
date: 2012-02-25
forum: Server Platforms
---

### Post by Vegan on 2012-02-25
I am looking a making a document for using linux as a file server.

I will be using SAMBA as this network will be mixed with Windows servers and clients.

so mounting everything from a USB stick to a CD/DVD to a RAID array to another linux box and finally to a windows box

contributions?

---

### Post by CharlesA on 2012-02-25
Well, everything is a file in linux, so you'd just need to know the path to the device and what file system it is running.

I mount my RAID array to /array like this:

```
sudo mount /dev/sdb1 -t ext4 -o noexec /array/
```

The fstab entry looks a little different since it uses UUIDs, but you get the idea.

You can mount USB sticks the same way because they are seen as regular hard drives -sda, sdb, etc.

CDs are a bit different but you can mount them the same way - mount /dev/cdrom /path/to/mountpoint

The device will change depending on what device you have.

---

### Post by Vegan on 2012-02-26
I was pondering a shell script to mount devices to mechanize the problem

I was thinking of using my Ubuntu VM for some development down the road

still a nuisance that I have to manually install Webmin, can management manage to get it into the repository for apt-get?

---

### Post by Vegan on 2012-02-26
also mounting a remote machine, best practices

---

### Post by CharlesA on 2012-02-26
> **Vegan said:**
> I was pondering a shell script to mount devices to mechanize the problem

I was thinking of using my Ubuntu VM for some development down the road

still a nuisance that I have to manually install Webmin, can management manage to get it into the repository for apt-get?
As far as I know Webmin won't be added back to the repos. It was removed back in 5.10 due to the way it handles config files or some such thing.

[https://help.ubuntu.com/community/WebMin](https://help.ubuntu.com/community/WebMin)

Mounting remote file systems works the same as mounting local ones, except the syntax changes - you can mount sshfs, cifs/samba and the like that way.

---

### Post by Vegan on 2012-02-27
I have used webmin fine with more recent releases and while imperfect (style is in the eye of the beholder) it gets the job done.

The [webmin page]("http://www.webmin.com/") says its in APT but evidently that is not true.

I noticed its improved considerably since I first tried it.

---

### Post by CharlesA on 2012-02-27
They have a deb package. I didn't see any mention of having their repo like they did in the past.

---

### Post by rubylaser on 2012-02-27
Webmin is not in the repos, and I can't find a PPA for it either, so I believe the .deb package is the best way to install it at this point.  

For automatically mounting the shares, you'd either want to add an entry to /etc/fstab, or use [autofs]("https://help.ubuntu.com/community/Autofs").  In the past, I've only used this with removable disks, and used fstab for all static mounts.

---

### Post by CharlesA on 2012-02-27
I've heard you can use autofs for Samba, SSHFS and NFS mounts, but I haven't tried it personally.

All my mounts are done via fstab.

---

### Post by rubylaser on 2012-02-27
Do use fstab for everything too, but autofs is pretty slick for external hard drives. It does work for Samba and NFS as well, but I've never used it that way.

---

