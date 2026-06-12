---
title: "Beginner Question:Cant access a directory even if chowned and chmodded"
date: 2008-07-03
forum: Server Platforms
---

### Post by minuxx on 2008-07-03
Hi!

I have a user called hlds and a group called gadmin.
I chowned the homedir like this:

$sudo chown -R hlds:gadmin *

and then chmodded it as well like this:

$sudo chmod -R ug+rwx *

Now I want to access a subdirectory in that home dir called valve with a user called bob. bob is member of gadmin.
When I try to access that dir called valve it tells me I have no permission.

drwxrwx--- 11 hlds gadmin    4096 2008-07-03 17:43 valve

$groups bob
bob gadmin

Whats wrong?

---

### Post by unixbills on 2008-07-03
I think it is the directory itself.  What does the homedir look like?  I am assuming this is /home/hlds. bob can't get to the file even if he has access to the file if he can't read the DIR.  Or bob would also need to be a member of the hlds group.

---

### Post by Titan8990 on 2008-07-03
You can change the permissions on a dir with chmod the same way you would a file.

---

### Post by minuxx on 2008-07-03
Wait you mean as long as hlds is not part of gadmin group it doenst matter if bob is part of gadmin?

Should I try this?:

$ sudo usermod -a -G gadmin hlds
$ cd /home/
$ sudo chown -R hlsd:gadmin hlds
$ sudo chown -R ug+rwx

---

### Post by Titan8990 on 2008-07-03
I misundertood your question at first.

Yes, Bob needs to be in the same group as the owner of the directory. If you have already issued the commands shown in your first post you should be able to just add Bob to the hlds group and be done with it.

---

### Post by minuxx on 2008-07-03
I f***ed up!

I removed bob ( was a sudoer) from the sudoers list and root is disabled.
Now someone wrote I should use a live cd and mount my / partition.
I am on the terminal of my livecd but I dont have a clue how to mount my / partition.
How do I have to put the mount command to get it right ?

---

### Post by Titan8990 on 2008-07-03
First find out which partition your file system is on by issueing the sudo fdisk -l command:

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10c310fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 250.0 GB, 250057219584 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b3151

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29920   240332368+  83  Linux
/dev/sdb2           29921       30401     3863632+  82  Linux swap / Solaris
```

My root filesystem is on sdb1.

I would issue these commands to mount sdb1.
```

sudo mkdir /media/sdb1
sudo mount /dev/sda1 /media/sb1
```

You can now view your filesystem by navigating to /media/sdb1.

---

### Post by minuxx on 2008-07-03
You are sure the syntax is right ?

---

### Post by minuxx on 2008-07-03
I got three filesystems to mount.

/dev/sda1 * [...] Linux
/dev/sda2   [...] Extended
/dev/sda5   [...] Linux LVM

I mounted all three. The first one contains only strange images? and nothing that compares to my old filesytem.
The other two filesystems only allow to mount if I issue

$ sudo mount -t proc /dev/sda2 /media/sda2


But those contain both the same stuff. Complete gibberish for me.
Please help me!
I am so p***ed off.
I invested loads of time into this and now it looks like I have to start from scratch.

---

### Post by unixbills on 2008-07-03
Do you have a grub boot menu?  Can you select "recovery mode"?

For me i can select root shell and it works fine.
I tried this from a live cd but I can't mount the root with "mount -t ext3 /dev/sda1" because it says it is "busy".  I will work on this another time but the above "recovery mode" got me to a pound sign so I could add or fix the user.

Sorry but I am pretty new to Ubuntu and have not needed to mount a root boot drive before.

Bill

---

### Post by minuxx on 2008-07-03
Its all good!
Pheew!

Those articles helped me:

[http://ubuntuforums.org/showpost.php?p=2604293&postcount=7](http://ubuntuforums.org/showpost.php?p=2604293&postcount=7)
[http://baudizm.blogsome.com/2008/06/05/retrieving-lvm-volume-data-with-ubuntu-and-backup-to-nfs-server/](http://baudizm.blogsome.com/2008/06/05/retrieving-lvm-volume-data-with-ubuntu-and-backup-to-nfs-server/)

---

