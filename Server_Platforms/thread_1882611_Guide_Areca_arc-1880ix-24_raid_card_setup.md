---
title: "Guide: Areca arc-1880ix-24 raid card setup"
date: 2011-11-17
forum: Server Platforms
---

### Post by david.garceau on 2011-11-17
Just got done setting up my areca arc-1880ix-24, ran into some issues, so i figured i would post a little howto on how i did it, i am not sure if this is the best way to get this all working, but its working for me.


```
apt-get update
apt-get dist-upgrade
reboot
apt-get install build-essential
apt-get install linux-headers-$(uname -r)
reboot
apt-get install unzip
wget ftp://ftp.areca.com.tw/RaidCards/AP_Drivers/Linux/DRIVER/SourceCode/arcmsr.1.20.0X.15-110622.zip
unzip arcmsr.1.20.0X.15-110622.zip
cd /home/david/arcmsr.1.20.0X.15-110622
make
insmod arcmsr.ko
nano /etc/init/mountall.conf
	change the bottom to this...
	
post-stop script
    rm -f /forcefsck 2>dev/null || true
    exec insmod /home/david/arcmsr.1.20.0X.15-110622/arcmsr.ko
end script

mkdir "/media/Raid 01"
mkdir "/media/Raid 02"
mkdir "/media/Raid 03"
mkdir "/media/Raid 04"
mkdir "/media/Raid 05"
mkdir "/media/Raid 06"
mkdir "/media/Raid 07"
mkdir "/media/Raid 08"
mkdir "/media/Raid 09"
mkdir "/media/Raid 10"


nano /etc/fstab

add this to the bottom

/dev/sdb1 /media/Raid\04001/ ext4 defaults 0 1
/dev/sdc1 /media/Raid\04002/ ext4 defaults 0 1
/dev/sdd1 /media/Raid\04003/ ext4 defaults 0 1
/dev/sde1 /media/Raid\04004/ ext4 defaults 0 1
/dev/sdf1 /media/Raid\04005/ ext4 defaults 0 1
/dev/sdg1 /media/Raid\04006/ ext4 defaults 0 1
/dev/sdh1 /media/Raid\04007/ ext4 defaults 0 1
/dev/sdi1 /media/Raid\04008/ ext4 defaults 0 1
/dev/sdk1 /media/Raid\04009/ ext4 defaults 0 1
/dev/sdk1 /media/Raid\04010/ ext4 defaults 0 1

```



Here is an updated version, decided to use a raid 10 on all of the drives, this time i included the directions on how to format the drive, i also had to switch to xfs file system due to the ext4 not being 100% tested with 16tb+ capacities.

```

## Driver howto for areca raid card

## Updating and loading pre reqs
sudo su
apt-get update
apt-get dist-upgrade
reboot
sudo su
apt-get install build-essential
apt-get install linux-headers-$(uname -r)
reboot
sudo su
apt-get install unzip

## Downloading and unzipping the driver for areca raid card
wget ftp://ftp.areca.com.tw/RaidCards/AP_Drivers/Linux/DRIVER/SourceCode/arcmsr.1.20.0X.15-110622.zip
unzip arcmsr.1.20.0X.15-110622.zip

## Building driver
cd /home/david/arcmsr.1.20.0X.15-110622
make
insmod arcmsr.ko
parted -l
######### Make sure that your hard drive is listed there

## Setting up driver to startup at boot
nano /etc/init/mountall.conf
	change the bottom to this...
	
post-stop script
    rm -f /forcefsck 2>dev/null || true
    exec insmod /home/david/arcmsr.1.20.0X.15-110622/arcmsr.ko
end script
Press Ctrl+x
Press Y
Press Enter
reboot

## Formatting the drive
sudo su
parted /dev/sdb
mklabel gpt
unit tb
mkpart primary 0 -0
print
quit
apt-get install xfsprogs
mkfs.xfs /dev/sdb1

## Mounting the Drive
mkdir "/media/File Server"

nano /etc/fstab

add this to the bottom

/dev/sdb1 /media/File\040Server/ xfs defaults 0 1

Press Ctrl+X
Press Y
Press Enter


## Done

```

---

### Post by rubylaser on 2011-11-17
Your last two lines have the same device being mounted twice
```
**/dev/sdk1** /media/Raid\04009/ ext4 defaults 0 1
**/dev/sdk1** /media/Raid\04010/ ext4 defaults 0 1
```

And, if I may ask, why did you build 10 separate mount points?  Are you just using the card as a pass through and not using it to create a hardware RAID set?

---

### Post by david.garceau on 2011-11-18
No specific reason to be honest, and no i am not. I am using the raid card to setup 10 raid 1 arrays. Inform me as to what the difference would be if i mounted them all to the same mount point.

---

### Post by rubylaser on 2011-11-18
I was wondering why you we making so many mount points.  You couldn't mount the ten arrays at the same mount point, they're each separate block devices so they'd need a different mount point.

Is there a reason why you didn't want to make 1 big RAID10 array?  I'm just trying to understand the reason for (10) RAID1 arrays versus (1) RAID10 that would be faster, still very fault tolerant, and you'd have 1 big volume to manage rather than 10 smaller ones.  It just seems like an odd scenario to me.

Thanks for posting the setup instructions for others with that RAID card :)

---

### Post by david.garceau on 2011-11-18
Are you sure that you can use raid 10 like that? I thought if you had 3 drives, it just made the 3rd a drive that would just take over if one of the other failed. But you are correct that would be nice. I thought the raid 1s were the right way to do this without losing more storage space.

*edit*

[http://acnc.com/raidedu/10](http://acnc.com/raidedu/10)

according to here, from what i gather... you will have 4 hard drives to begin with... two sets mirroring, and then the two sets would be striped. I dont think this is the correct raid to make one big drive with the same fault tolerances as what 10 sets of raid 1 would do for me. If what you say exists i will be redoing all my raids :)

---

### Post by rubylaser on 2011-11-18
No, I didn't say it would have the same fault tolerance as 10 RAID1 arrays, but it's more than adequate.  With 20 disks, you could in theory lose a drive from every mirror in the best case scenario and still have a functional array.  In the worst case, losing 2 drives from the same mirror would cause a failure.

The main difference, is will RAID10, you'd get better performance, and have one big pool, rather than 10 smaller pools like you have now.  You'd have the same amount of storage space either way.  

If what you have works for you, that's great, but most people buy RAID cards to form a large dataset.  The way, you've done it requires to to monitor the storage space used on each volume, and when one's full, you'll need to start using another.  I guess to determine if how you've set it up is proper, I'd need to know what you use the arrays for.

---

### Post by david.garceau on 2011-11-18
I see, gonna set it up now and see what its like. My question to you... is what happens when two of the drives die (in the same mirror). 

I might even be thinking of this wrong tell me if i am right by assuming this...

Raid 10 with 20 drives is basically like 10 raid 1 arrays in a jbod. So... with that being said... in a jbod if 1 drive dies you have a catastrophic failure.


In a raid 10 there are basically 10 raid 1s inside of it so if 1 drive dies in one of the raid 1s its okay... but if both of the drives die in one of the raid 1's, what happens to the raid 10... (this is a hard question to ask... hah)

---

### Post by rubylaser on 2011-11-18
No, that's the best question to ask, and you're spot on, if you lose one of your mirrors completely, it's just like losing a drive from a RAID stripe, you lose your RAID set.  Luckily, if you set up a spare or two on your array, there are no parity calculations that need to be done, so a spare can be added very quickly, and greatly reducing the window for this possibility.

If you're using this for maximum storage, RAID10 or the (10) RAID1 arrays is not the best way to do it because you're losing so much space (RAID6 would be better).  But, if you want the best speed/tolerance and a single volume, you really can't beat RAID10.  But to really recommend the correct RAID level, it'd be nice to know what you're using it for (i.e. movie/ picture storage, virtual machines, mailboxes, etc).

---

### Post by david.garceau on 2011-11-18
It is used for storage of massive amounts of video. and basic office documents.

---

### Post by rubylaser on 2011-11-18
Personally, I would run a RAID6 if it's just video storage.  I'm going to assume you have 20 drives because you have (10) mirrors.  I would setup a ( 18 ) drive RAID6 array with (2) hot spares.  That would give 60% more storage space than you currently have and you could still lose (2) drives and be okay.

I would hate with a huge video collection to have to manage 10 shares.  I would either RAID10 or RAID6 as I said above.  But, ultimately, it's your hardware and data, so you can choose your own path :)

---

### Post by david.garceau on 2011-11-18
absolutely. Thanks for all the info always nice to get another persons point of view. Hopefully this will help someone else in the future, there isnt much support from areca for linux distros.

---

### Post by david.garceau on 2011-11-21
Posted an updated guide with a few changes.

---

### Post by rubylaser on 2011-11-21
+1 for RAID10 and more storage space :)  Good choice on XFS as e2fsprogs does not currently support the full feature set to allow for using ext4 over 16TB yet.

---

### Post by david.garceau on 2011-11-22
Yeah, i did find a way to make it work on ext4 ([http://blog.ronnyegner-consulting.de/2011/08/18/ext4-and-the-16-tb-limit-now-solved/](http://blog.ronnyegner-consulting.de/2011/08/18/ext4-and-the-16-tb-limit-now-solved/)) but i didn't really feel comfortable using something that is still not thoroughly test and officially supported.

---

