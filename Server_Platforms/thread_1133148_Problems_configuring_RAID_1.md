---
title: "Problems configuring RAID 1"
date: 2009-04-22
forum: Server Platforms
---

### Post by Nixie Pixel on 2009-04-22
Hi all, I have taken the following steps to set up software RAID 1 on two 500 GB IDE drives for my fresh Ubuntu server installation.
(I followed the [tutorial found here]("http://mywheel.net/blog/index.php/software-raid-in-ubuntu/"))

-Placed drives on separate IDE controllers

Using fdisk -l I found my 500GB drives on /dev/sdb and /dev/sdc.

I then ran:
sudo fdisk /dev/sdb

I created a new primary partition, began at cylinder 1, ended at cylinder 60800, and set it to type 83, then wrote the changes.

I repeated this for /dev/sdc

Since I didn't have it, I ran sudo apt-get install mdadm

It had me run through a "Citadel server" setup, which I had no desire for, but figured I needed it for RAID?

Then I ran this:
sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1

But now I'm stuck.  When I ran watch cat /proc/mdstat after reboot I just got the error message "at: /proc/mdstat:  No such file or directory."  I'm not sure how to check where I went wrong, or if I in fact set up RAID correctly and just don't know where to go from here.

Thanks!

---

### Post by fjgaude on 2009-04-22
I don't have any experience with **mdadm** raid1, at least not in the last three years... questions: Did you re-boot before the array had a filesystem put on it? Or even before the array had finished making itself? Did you create partitions for sdb1 and sdc1?

Can you show what this is:

```
sudo mdadm -D /dev/md0
```

Finally, you are not trying to boot from /dev/md0?

---

### Post by Nixie Pixel on 2009-04-24
> **fjgaude said:**
> I don't have any experience with **mdadm** raid1, at least not in the last three years... questions: Did you re-boot before the array had a filesystem put on it? Or even before the array had finished making itself? Did you create partitions for sdb1 and sdc1?

Can you show what this is:

```
sudo mdadm -D /dev/md0
```

Finally, you are not trying to boot from /dev/md0?
I have no idea if I rebooted at the right time or not, as I didn't know how to tell if the array had finished building.  I had created partitions for sdb1 and sdc1.  I only used mdadm because I found a tutorial for it here on the forum, I would be happy to use any other method that will work for me.

The command above returns:
mdadm: cannot open /dev/md0: No such device or address

I am booting to /sda1, where the server is installed.

Thanks!

---

### Post by fjgaude on 2009-04-24
Okay, you can use this command to watch builds:

```
sudo watch cat /proc/mdstat
```

You can see if your present create is valid with:

```
sudo mdadm --assemble --scan
```

If that doesn't work you might have to use the /dev/sdb1 and /dev/sdc1 in place of the --scan.

You need a mountpoint for the array also:

```
sudo mkdir /raid
```

You of course can use anything other than /raid for the mountpoint.

You mount the array with this:

```
sudo mount /dev/md0 /raid
```

Mount automatically at boot time you have to add a line in your /etc/fstab file:

```
/dev/md0 /raid ext3 defaults 0 2
```

Let us know how you are doing.

---

### Post by Nixie Pixel on 2009-05-06
> **fjgaude said:**
> Okay, you can use this command to watch builds:

```
sudo watch cat /proc/mdstat
```
I assume I have to do this after entering something else?  Right now, when I run this, it returns "at: /proc/mdstat: No such file or directory" over and over.

> **fjgaude said:**
> ```
sudo mdadm --assemble --scan
```
Returns "mdadm: error opening /dev/md/0: No such device or address" 
then "mdadm: No arrays found in config file or automatically"

> **fjgaude said:**
> If that doesn't work you might have to use the /dev/sdb1 and /dev/sdc1 in place of the --scan.
Using /dev/sdb1 in place of --scan returns "mdadm: error opening /dev/sdb1: No such device or address" and the same for /dev/sdc1.


> **fjgaude said:**
> ```
sudo mkdir /raid
```
Ok, thanks, done.

> **fjgaude said:**
> ```
sudo mount /dev/md0 /raid
```
Won't work until /dev/md0 exists, right?

> **fjgaude said:**
> Mount automatically at boot time you have to add a line in your /etc/fstab file:

```
/dev/md0 /raid ext3 defaults 0 2
```
Will do when I can get it working, thanks!

---

### Post by fjgaude on 2009-05-07
Wow, we work in slow motion.

Something is wrong with how you created the array... the command you gave is the correct one.

After you created the array, did you put a filesystem on it? Like:

```
sudo mkfs -t ext3 /dev/md0
```

Then watch it do it thing:

```
sudo watch cat /proc/mdstat
```

What does just doing this show:

```
sudo fdisk -l
```

---

### Post by bsmith1051 on 2009-05-07
Lot of good suggestions here on trying to diagnose the existing array, but why didn't you just use the built-in procedures during the initial setup?
[http://help.ubuntu.com/community/Installation/SoftwareRAID](http://help.ubuntu.com/community/Installation/SoftwareRAID)

If you aren't 'committed' to your current setup (especially if it's not working yet!) then maybe you can just start over?
____________

**UPDATE**

Here's a 2nd howto,
[https://help.ubuntu.com/community/Installation/FileServerWithRAID](https://help.ubuntu.com/community/Installation/FileServerWithRAID)

Also, you shouldn't need to do the extra steps to install GRUB on the 2nd drive.  That bug was fixed in 8.10.

---

### Post by Nixie Pixel on 2009-05-07
No, I'm not committed, except to learn what it was I did wrong and how to fix it in the future...

It will probably be easier to start over, just so long as I don't need to mount / on a RAID array that I set up during initial installation.

Edit:  Yes, this is a fun project, not a business one, so I have been doing it in my spare time (plus I was in L.A. for a while visiting folks, but now I'm back!)

---

### Post by Nixie Pixel on 2009-05-09
Ok, for now just to get the server up and running I'm reinstalling rather than trying to fix the problem.  I have created a new thread to deal with the problems I'm having getting this running during the install:

[http://ubuntuforums.org/showthread.php?p=7243963#post7243963]("http://ubuntuforums.org/showthread.php?p=7243963#post7243963")

Thanks!

---

