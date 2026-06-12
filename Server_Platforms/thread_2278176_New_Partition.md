---
title: "New Partition"
date: 2015-05-14
forum: Server Platforms
---

### Post by aaron27 on 2015-05-14
I have created a new partition for my ubuntu 14.04 install but whenever i reboot i am asked to enter the admin details to mount the drive, not sure where i have gone wrong?

I am trying to mount the partition to give us a larger storage space for owncloud, can anyone offer some advice?

---

### Post by darkod on 2015-05-14
Did you make an entry for it in /etc/fstab? Post the content of that file and tell us the partition name.

---

### Post by aaron27 on 2015-05-14
I wasnt aware of the fstab entry... gedit the file and enter the new sda?

---

### Post by darkod on 2015-05-14
Yes. Lets assume the new partition is /dev/sda6 and you formatted it as ext4 (you need to format it before first use). You also need to make an empty folder to serve as mount point. For exampe:
```
sudo mkdir /mydata2
```

The folder has to be empty to be used as mount point for partitions. After that the entry in /etc/fstab would be like:
```
/dev/sda6   /mydata2   ext4   defaults   0   0
```

You can mount all entries in fstab without rebooting with:
```
sudo mount -a
```

Don't forget to edit fstab as sudo. It's a system file so you need to edit it with sudo. After that you can use the new space as /mydata2.

---

### Post by Ron_Greve on 2015-05-14
If you made one filesystem on the whole disk
blkid /dev/<disk>
then make an entry like (replace uuid with what you got from blkix):
UUID=7340ea5f-3325-466a-8e2f-62c1cf15ae94 /mymount               ext4    errors=remount-ro 0       1

---

### Post by aaron27 on 2015-05-14
> **darkod said:**
> Yes. Lets assume the new partition is /dev/sda6 and you formatted it as ext4 (you need to format it before first use). You also need to make an empty folder to serve as mount point. For exampe:
```
sudo mkdir /mydata2
```

The folder has to be empty to be used as mount point for partitions. After that the entry in /etc/fstab would be like:
```
/dev/sda6   /mydata2   ext4   defaults   0   0
```

You can mount all entries in fstab without rebooting with:
```
sudo mount -a
```

Don't forget to edit fstab as sudo. It's a system file so you need to edit it with sudo. After that you can use the new space as /mydata2.



Ok brilliant, yes I did format as ext4. 
you say i need to make an empty folder for it, I am going to be using this to store our data from ownCloud, so if i created an emprt folder with a similar name to that, i could then re-assign ownCloud to use that as a data directory?

i will give it a go now and see how i get on.

---

### Post by aaron27 on 2015-05-14
Brilliant that worked, or so it seems. Just having some issues with my owncloud data folder now but do not think that is related to anything here (hopefully)

---

### Post by darkod on 2015-05-14
Yes, you can only use empty folders as mount points. It depends on owncloud options but in most cases you can point applications to use which ever mount point you have created for that purpose.

---

### Post by aaron27 on 2015-05-14
I created a brand new one, so it was empty. just struggling to get owncloud working now, but im on their forum for that. thanks for the advice

---

