---
title: "expanding ubuntu 8.10 server"
date: 2012-06-09
forum: Server Platforms
---

### Post by angelochen168 on 2012-06-09
Hi,

got a ubuntu 8.10 server with 80G hard disk, space now is full, re-installing ubuntu is not an option, what easy way to expand?

1) replacing it with a bigger hard disk? is there a way to clone it from old to new hard disk?
2) mount another hard disk into server, but how to use the new hard disk as /home? 

Thanks for any tip,

Angelo

---

### Post by spynappels on 2012-06-09
You probably won't like this, but the first question is why is reinstalling not an option?

Intrepid Ibex has been out of support for 2 years, and as you will need to use a new (bigger) hard drive, the best option is to install a current LTS version on a larger hard drive and transfer settings and data across.

---

### Post by angelochen168 on 2012-06-09
re-installing will be too trouble some, that server was configured with a lot of program, all automated to handle quite a number of tasks, it will take a long time to re-configured and make it right again.

---

### Post by SeijiSensei on 2012-06-09
> **angelochen168 said:**
> 2) mount another hard disk into server, but how to use the new hard disk as /home?

While I agree with spynappels that you should really consider upgrading the operating system, I'll answer this question anyway.

First, install the disk in the computer.  It should be recognized and assigned a device like /dev/sdb.  (Run "sudo dmesg" at the prompt if you're not clear on which device the drive was assigned to.)  Next, partition the new drive with gparted or fdisk.  If the drive is simply to be used to store the home directories, you probably just want one partition, say /dev/sdb1.

Now format the partition and create an ext4 filesystem:

```

sudo mkfs -t ext4 /dev/sdb1

```

Now we're ready to migrate the /home directories and prepare for the switch over.  Create a temporary mount point like, say, /mnt/newhome, then use rsync to copy the contents of /home like this:

```

sudo mkdir /mnt/newhome
sudo mount /dev/sdb1 /mnt/newhome
cd /home
sudo rsync -av . /mnt/newhome

```

Lastly we need to edit fstab so it will mount the new drive as /home upon reboot.  Open /etc/fstab in an editor as root with sudo and add the line:

```
/dev/sdb1  /home   ext4   defaults    0 0
```

You will be left with the issue of the data in the old home directories still being stored on the original drive.  Once you're sure everything is working correctly with the new drive, boot into "recovery mode" and choose the "root shell" option when prompted.  At the "#" prompt run these commands:

```

cd /
umount /home
cd /home
rm -rf *
reboot

```

(You don't need sudo here as you already have root privileges.)

Of course, before doing any of this make sure you have a good up-to-date backup of /home stored on another device just in case.

---

### Post by volkswagner on 2012-06-09
I agree with spynapples.  I'd take the larger drive and install a long term release such as 10.04 or 12.04, then copy settings and import users, data, etc..

To accomplish what you are asking there are many options.

You can simply install the second drive and move /home to that drive.

Drive imaging is also an option.  You can use dd to image the 80gig drive to the larger drive.

Clonezilla also has a nice liveCD to allow you to direct copy the 80gig drive to the larger drive.

Again, 8.10 is not even getting security updates, I'd do what is necessary to get a current system installed.

---

### Post by angelochen168 on 2012-06-11
This is a perfect guide to my problem, thanks.

I agree with all the replies here that upgrading to a newer version is a better option, so a related question is,

How to copy all the user accounts with their data to a new PC with a newer version if I can do it?

Thanks


> **SeijiSensei said:**
> While I agree with spynappels that you should really consider upgrading the operating system, I'll answer this question anyway.

First, install the disk in the computer.  It should be recognized and assigned a device like /dev/sdb.  (Run "sudo dmesg" at the prompt if you're not clear on which device the drive was assigned to.)  Next, partition the new drive with gparted or fdisk.  If the drive is simply to be used to store the home directories, you probably just want one partition, say /dev/sdb1.

Of course, before doing any of this make sure you have a good up-to-date backup of /home stored on another device just in case.

---

### Post by SeijiSensei on 2012-06-11
> **angelochen168 said:**
> How to copy all the user accounts with their data to a new PC with a newer version if I can do it?

All the user identity information is stored in three files: /etc/passwd, /etc/group, and /etc/shadow.  Copying these three files to /etc on the new machine will migrate all the accounts.

As for migrating the home directories, you can use rsync over the network as long as you have sshd running on the new machine:

```

cd /home
sudo rsync -av . root@remote_server:/home

```

---

