---
title: "Raid Setup"
date: 2012-03-05
forum: Server Platforms
---

### Post by skipgillespie on 2012-03-05
I am having trouble setting up a RAID array on my Ubuntu 10.04 Server.  

I have a 40GB hd that I want to install the system on connected to on-board sata.  I have a 6-port raid controller installed and want to install 4, 2TB hard drives in two separate raid 1 arrays.  If I have the 2TB drives connected to the controller, Ubuntu wants to automatically install the system on one of them; however, it does not seem to recognize the raid array as setup in the controller.  It continuously recognizes them as individual drives.   

If I disable the drives on the controller, it will then allow me to setup the system on the 40G drive that I want, but then I have all kinds of issues setting up the raid.  Again, it does not seem to recognize the raid array I have setup on the on-board card.  I have tried using the software raid available, but have had no luck setting it up once the system is already installed on the 40GB.  If I try to set it up at install; again, it wants to load the system on the 2TB raid, not the 40GB system drive.

Any help will be greatly appreciated!

PS. It might be of help to know that I have tried administering the server using both Webmin and VNC virtual desktop without any luck.

---

### Post by a2j on 2012-03-05
It does not like your fake raid controller. Is there a linux driver and/or support for it?

---

### Post by skipgillespie on 2012-03-05
> **a2j said:**
> It does not like your fake raid controller. Is there a linux driver and/or support for it?

I've been digging to see if I can find a linux driver.  I assumed since Ubuntu recognized the drives on the controller that it must have loaded appropriate drivers.

---

### Post by darkod on 2012-03-05
Have you considered software raid with mdadm?

I believe it even has advantages over cheaper hardware controllers and fakeraid.

How "good" is your controller?

---

### Post by skipgillespie on 2012-03-05
> **darkod said:**
> Have you considered software raid with mdadm?

I believe it even has advantages over cheaper hardware controllers and fakeraid.

How "good" is your controller?

I tried using mdadm software raid.  I could not get it set up after the system was installed.  When I would try to setup the raid at install, it would only let me install the system to the raid, not to the 40GB system drive that I want to use.

FYI:  My raid card is a Vantech UGT-ST310R.  From things I had read, Ubuntu was supposed to detect it without issue.

---

### Post by Pay87 on 2012-03-05
Ubuntu didn't like my fake raid, too. And I was a little bit too lazy to do a software raid by hand, so I booted up a OpenSuse Live-CD. There I used the graphical part of the Yast partition program to do the raid setup. Then I started over with the Ubuntu Server installation. Clicking on manual in partition mode and I saw all raid drives and was able to easily go on :popcorn:

---

### Post by skipgillespie on 2012-03-06
> **Pay87 said:**
> Ubuntu didn't like my fake raid, too. And I was a little bit too lazy to do a software raid by hand, so I booted up a OpenSuse Live-CD. There I used the graphical part of the Yast partition program to do the raid setup. Then I started over with the Ubuntu Server installation. Clicking on manual in partition mode and I saw all raid drives and was able to easily go on :popcorn:

I'm fairly new to Linux and not familiar with OpenSuse.  Can I run the Yast program after I have installed Ubuntu?  If not, will it allow me to install Ubuntu on the 40GB drive and still setup the raid on the 2TB drives?

---

### Post by a2j on 2012-03-06
> **skipgillespie said:**
>  will it allow me to install Ubuntu on the 40GB drive and still setup the raid on the 2TB drives?

yes, no need for a SUSE and Yast. You can setup mdadm raid when installing Ubuntu server.

---

### Post by skipgillespie on 2012-03-06
> **a2j said:**
> yes, no need for a SUSE and Yast. You can setup mdadm raid when installing Ubuntu server.

After my raid controller didn't seem to get me where I needed to go, I tried setting up mdadm raid.  If I set it up during install of the system, it kept putting the OS on the raid drives.  I don't want it on the raid, I have a separate 40GB drive for the OS.  If I disable the raid drives, I can get the OS on the 40GB drive that I wanted, but then I can't seem to set up the raid, after the fact.

Here's the configuration that I want:

_***On-board SATA***_ 
Drive 1 - 40GB - OS

_***Vantech UGT-ST310R Raid Controller***_
Drive 2 - 2TB - Storage (Raid 1 Mirror with Drive 3)
Drive 3 - 2TB - Storage (Raid 1 Mirror with Drive 2)

Drive 4 - 2TB - Storage (Raid 1 Mirror with Drive 5)
Drive 5 - 2TB - Storage (Raid 1 Mirror with Drive 4)

---

### Post by a2j on 2012-03-06
assuming Ubuntu sees 5 drives of total, just make sure that 40G drive is formatted and set / as mount point. Your other two mirror raid will have their own mount points. i.e. /raid_1 and /raid_2

also, is there a reason for two mirror arrays? I'd just make a raid10 from those four drives and call it a day. "dual" redundancy and your os can be redundant also. just my opinion. been there, done that.

---

### Post by skipgillespie on 2012-03-06
> **a2j said:**
> also, is there a reason for two mirror arrays? I'd just make a raid10 from those four drives and call it a day. "dual" redundancy and your os can be redundant also. just my opinion. been there, done that.

I've thought about Raid 10.  I've always been a bit gun shy about striping.

---

### Post by a2j on 2012-03-07
raid10 with 4 drives sounds like good logical solution. having os on single drive and two mirror arrays is not... practical? more headache. Unless, of course, setup like this required for what ever reason.

---

### Post by skipgillespie on 2012-03-07
> **a2j said:**
> Unless, of course, setup like this required for what ever reason.

The biggest issue preventing me from doing a raid 10 is that I need to migrate over data from an existing NAS.  So I need to get the first two drives set up, then copy the data from the existing NAS to them, then move the two drives out of the NAS into the server.  With all the trouble I'm having setting up the raid, I didn't want to try to move the existing drives over and risk loosing 2TB worth of data.

---

### Post by darkod on 2012-03-07
So what is the current status? Do you have the raid1 running with the first two disks?

I don't understand your post #9, you say it wants to put the OS on the raid.

It will put the OS where ever you tell it the / partition is. Just make sure you are not selecting the array as /.

Create the / and swap partitions on the 40GB disk.

Create the raid partitions on the two 2TB disks. Configure the softraid1 array from these two partitions. Select the newly created RAID1 device (probably md0) and create a single ext4 partition on it (or more partitions depending on your plans).
Then make the mount point for that partition for example /data1.

Later when you configure the second RAID1 array you can make the mount point /data2.

There is another idea, but I have never tried it and you will need to also investigate a bit if no one else jumps in.

I am not sure how configuring RAID10 goes. Whether you first configure RAID0 from two partitions (disks) and then RAID1 from these two devices, or all four disks at once.

Because there is the option to configure the array as degraded, and add the other disks later and let it sync.

The idea would be:
(I am talking only about the array, we already discussed the 40GB OS disk)
Configure RAID0 from the two disks you have available.
Then Configure RAID1 with this raid device, and tell it the second device is missing.
That should give you your 4TB space running in degraded mode.
Copy the data from the NAS onto the array.
Connect the other two disks. Make RAID0 device from them.
Add this device as the second missing device of the RAID1. Let it sync.

You should end up with a single 4TB RAID10 device. In theory...

Software raid can run degraded for months (years). I was very surprised to see that my WD My Book World Edition network disk is actually running like a degraded RAID1 device. The model I have is with one disk, not the two disk raid model. But I guess they wanted to use the same developed firmware, so the model with one disk runs from factory as a RAID1 array with one disk missing. That's how they ship it.

---

### Post by darkod on 2012-03-08
On top of the above said, one more idea: LVM.

That will also make easier any future storage upgrades.

In case you are not familiar with it, the idea would be:
Make a 2TB RAID1 device from the first two disks you have.
Instead of creating ext4 partition on this device, create a LVM partition.
Configure LVM creating the PV, VG and LV (logical volume).
Copy the NAS data.

Create another 2TB RAID1 device from the other two disks.
Again create lvm partition from this device.
Add this PV on the existing LVM configuration.
Grow the VG and LV, and you end up with 4TB single LV.

In future, you could do the same by adding more disks.

---

### Post by skipgillespie on 2012-03-08
> **darkod said:**
> So what is the current status? Do you have the raid1 running with the first two disks?



I think I may have figured out part of my problem.  I have been trying to administer the server with Webmin from another computer attached to my network.  It appears that may have been giving me some of the issues (at least in trying to set up the raid after the fact).  I decided to try set up the mdadm raid at the command level right from the server, and appear to have at least created and mounted the volume.  I am still having issues with permissions, it seems, but at least I can see the array.  Is there any tool that I can run to verify the it is keeping both drives mirrored?  Have you seen problems with Webmin administration before?

So, I think I am going to start from scratch.  I'm going to rip down all the drives and reinstall everything.  

Are there many differences/changes between Ubuntu Server 10.04 and 11.10?  Would it be worth my while to try to download 11.10 again and use it instead of 10.04?

Also, someone recommended that instead of using two raid1 arrays or even a raid10 array, that I might consider a raid5 array.  I did a little reading on it and can't quite say that I have grasped the parity concept. But he says it will give me the enhanced performance that a raid0 would and would give redundancy like a raid 1 would, but with only 3 drives.  This way I could set up the entire 4TB volume, migrate the data from the one drive remaining on my NAS and then have a spare drive to immediately throw in if one of the other three fails.

Any thoughts?

---

### Post by darkod on 2012-03-08
If you can, always try to do the initial setup on command level, either with a keyboard and monitor directly on the server or SSH session.

You can use Webmin for administration later but I wouldn't depend on it for raid creation. In fact I don't use it and have no real need for it.

As far as raid0 performance compared to raid5, I am not sure how they fare. But one clear benefit of raid5 would be that if you use all 4 disks (without spare) that would give you 6TB to use. You lose one disk for the parity but get 3 x 2TB = 6TB total for use.

Yes, it would be possible to create 4TB raid5 array with three disks, copy data and add the fourth disk, grow the array then grow the filesystem to get the 6TB.

---

### Post by skipgillespie on 2012-03-08
> **darkod said:**
> Yes, it would be possible to create 4TB raid5 array with three disks, copy data and add the fourth disk, grow the array then grow the filesystem to get the 6TB.

How difficult is it to add another drive to a raid5?  Once the drive is added, does the entire array have to be rebuilt in order to distribute the data and parity across all drives?  Future expansion is a concern.  I have installed a 5 drive hotswap backplane for later expansion.  With it I could conceivably expand to 8TB under a raid5 array.  But would adding drives after putting the volume online pose problems or cause excessive downtime while the volume rebuilds with the higher capacity?

---

### Post by darkod on 2012-03-09
This is what one old thread has in google:

----Expand section----
Unmount the array, i don't know if this is necessary, but doing so means less stuff to go wrong. 
sudo umount /dev/md0

Then you need to go and prepare the disk(s) to be added. (The prepare section of the guide)

Then tell mdadm that it can play with it:
sudo mdadm --add /dev/md0 /dev/sda2

Then tell mdadm to stop playing and use it to expand/grow your raid5  array(make sure that the number of raid devices is correct, it should be  the number of disks/partitions the grown/expanded array will have):
sudo mdadm --grow /dev/md0 --raid-devices=4

View and wait for the new array to reshape:
cat /proc/mdstat

Check the filesystem (required to resize it):
sudo e2fsck -f /dev/md0

Resize the filesystem on the new array so that you can use it for something useful.
sudo resize2fs /dev/md0

Mount the expanded/grown array with it's resized filesystem(remember to change the mount point):
sudo mount -t ext3 /dev/md0 /home/tore/raid

---

### Post by a2j on 2012-03-09
with disks larger than 500Gb, I'd not use RAID5. RAID6 or 10, otherwise risk loosing data is too high. Just IMHO. I personally use 4 1.5TB drives in RAID6. No regrets.

---

### Post by skipgillespie on 2012-03-09
> **a2j said:**
> with disks larger than 500Gb, I'd not use RAID5. RAID6 or 10, otherwise risk loosing data is too high. Just IMHO. I personally use 4 1.5TB drives in RAID6. No regrets.

Unfortunately, since I need to migrate data over from 1 of my four drives, I can't setup either a 6 of 10.  

Interestingly, last night I followed through and decided to start from scratch (as I have done 5 or 6 times already, with no luck) once again.  I booted with Partition Wizard disc and wiped all three 2TB drives that are ready, and the 40GB drive.  After low level formatting, I went into the raid card's bios and created a 4TB RAID5 array.  To my surprise, when I booted to the Ubuntu Server disc this time, it recognized the array; however, it only recognized it as a 2TB.  So I said, "to heck with it" (paraphrased of course #-o ), and figured I would see what the software RAID would do.  I rebooted, turned off the hardware RAID and low and behold, it found and acknowledged everything.  I set up RAID5 and even got the partitioning screen that allowed me to mount the volumes where I wanted (it was the first time I had seen this screen).

I have no idea what I may have done differently, or step(s) I may have missed, but it appears I am over the hump now with the RAID [-o< .  I've got Putty up and running on my desktop and can access command line from there.  This weekend will be the tell tail.  I'll start working on users and permissions.  Once that's up I should be gold \\:D/ .

Thanks for all the help guys.

---

### Post by darkod on 2012-03-09
Glad you got it going.

For argument sake, raid10 was actually possible, if I understand the concept right.

You can (could):
1. Create raid1 degraded array (1 disk present, 1 missing).
2. Create another raid1 array (1 present, 1 missing).
3. Create raid0 from these two arrays.
4. Copy NAS data.
5. Add the missing disks and let the raid1 arrays sync. The raid0 array with your data already copied shouldn't change at all.

In theory it should work. In practice, never tried it. :)

EDIT: Of course, raid5 will give you more usable space from your 4 2TB disks. Raid5 will give you 6TB total, while raid10 would only give you 4TB.

---

### Post by skipgillespie on 2012-03-12
> **darkod said:**
> For argument sake, raid10 was actually possible, if I understand the concept right.

Someone had mentioned that to me previously.  I tried to create a degraded raid set, but it just kept telling me that I didn't have enough drives installed, then would kick me back. ](*,) 

Anyway, the server is up and running. :biggrin: I got my permission issues straightened out.  The only problem I seem to have now is a DDNS issue.  I've installed ddclient and it appears to be updating properly, but I can't reach it from the outside world. :-k I believe it has to do with the way the router and modem are setup.  It is a bizarre arrangement!  But that's not a topic for this thread.

Thanks again for all your help.

---

