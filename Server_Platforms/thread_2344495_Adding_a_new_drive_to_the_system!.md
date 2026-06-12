---
title: "Adding a new drive to the system!"
date: 2016-11-25
forum: Server Platforms
---

### Post by agarwaldvk on 2016-11-25
Hi Everyone


I now have set up a Ubuntu Desktop 16.04 LTS machine to server as home (file and media) server. This is the setup :-

One (1) SSD with the OS
Two (2) physical HDD's, each 2TB capacity - one dedicated to media and other dedicated to data files

The physical HDD's are laid out like so :-
/sharedfiles/media - media share (/dev/sda1)
/sharedfiles/data - data share (/dev/sdb1)

/dev/sdc1 is the OS SSD!

The media share currently has about 1.6 TB of content. I am expecting to fill it up soon enough. To avoid running out of space, I would like to add another 2 tb HDD as additional storage for media content with the share configuration changed to appear like so :-
/sharedfiles/media
/sharedfiles/media/english
/sharedfiles/media/other

This will mean that I would need to move about 800 Gb of data from the existing '/sharedfiles/media' share to the '/sharedfiles/media/other' share.

The current '/sharedfiles/media' share definition is as follows :-
[media]
path = /sharedfiles/media
browsable = yes
writable = yes
guest ok = yes
public = yes
guest account = nobody
admin users = agarwaldvk

The existing mounting point definition in fstab file for the media drive is 
/dev/sda1 /sharedfiles/media ext4 defaults 0 0 
/dev/sdb1 /sharedfiles/media ext4 defaults 0 0  (this is the data share - nothing is to be changed for this)

I was looking at doing this :-

1. create 2 directories like so :-
  /sharedfiles/media/english
  /sharedfiles/media/others

2. Create 2 shares like so :-
[mediaenglish]
path = /sharedfiles/media/english
browsable = yes
writable = yes
guest ok = yes
public = yes
guest account = nobody
admin users = agarwaldvk

[mediaothers]
path = /sharedfiles/media/others
browsable = yes
writable = yes
guest ok = yes
public = yes
guest account = nobody
admin users = agarwaldvk

3. Delete the existing share '[media]'

I was looking at modifying the existing mounting points in the fstab file as following :-
/dev/sda1 /sharedfiles/media/english ext4 defaults 0 0
/dev/sdd1 /sharedfiles/media/other ext4 defaults 0 0 (assuming that the new drive has been formatted to ext4 format prior)


Is this going to work?


Best regards


Deepak

---

### Post by darkod on 2016-11-26
What you are planning will work, but there are also few different options.

1. A very good thing is linux is that you can have a mount point (because that's basically just an empty folder) inside another mount point. In such case, you can create an empty folder /sharedfiles/media/other and keep sda1 mounted on /sharedfiles/media and mount sdd1 at /sharedfiles/media/other.
This way everything you save in /other will go to one 2TB disk but everything you save in /media outside of /other will go to the other 2TB disk. You just have to remember this setup for the future when making changes, not to forget how you set it up.
And you also don't need to modify your share in any case. You can share the path /sharedfiles/media even when the disks are actually mounted one level below. Just make sure /other folder has adequate permissions.

2. The second option, and the one preferred I would say, is to think about introducing LVM. That will give you much more flexibility and better use of the storage space. You might not even need to buy any new disk soon.
With LVM you assign physical partitions and then use Logical Volumes (LVs) which are very flexible and can be expanded online when needed.
For example your media disk is 1.6TB full but together with the data disk if you have 2.5-3TB total data out of 4TB total space, why buying new disk? When you were rearranging your storage a week ago you managed to put all your data on one disk while formatting the other. That means there should be plenty of space. If you mentioned the new disk idea that time you could have used the process to intriduce LVM then.

Basically the idea would be to put again all data on one of the disks, add the other as LVM device, create Volume Group and two LVs (data and media), then move the data to them. After the first disk is empty, add it to the LVM too. So you end up with VG of 4TB and with LV size as much as you need, which can easily be expanded online (without unmounting or shutting down).

So, those are the options, now you have to make a decision...

---

### Post by agarwaldvk on 2016-11-27
Hi darkod


I did read about LVM's and I was very much interested in using it but the following warning (reproduced below) 


Quote
Warning: Make sure that you double-check that the devices you intend to use with LVM do not have any important data already written to them. Using these devices within LVM will overwrite the current contents.
If you already have important data on your server, make backups before proceeding.
UnQuote

made me slightly apprehensive given that we are talking about existing data to the tune of of 1.6 tb and potentially more if we were to add physical drives of the order of 2 tb each time.

My interpretation of the warning is as follows (correct me if I am wrong) :- 

Each time I intend to add a new physical drive to the system, it will need to be marked as LVM physical volume - and in doing so all existing data on all existing drives (new would be empty anyway so nothing lost) would be overwritten, Hence, say in stage 3, where I have 2 physical HDD's that are now full and I am intending to add another 2 tb drive, I would be required to :-

1. first copy the entire 4 tb of data elsewhere
2. add the new drive as a part of the existing volume group
3, recopy the 4 tb of my original data to 2 of the 3 physical HDD's in the volume group with the 3rd empty as this point


Seems like a lot of work and risk to realize not a lot, don't you think? Or am I missing something?

The other thing that I came across on one of the 'HowtoGeek' sites is this warning (and that was also my initial concern) :-

Quote
Note that merging multiple disks into a single volume can be a bad idea if you’re not creating backups. It’s like with RAID 0 — if you combine two 1 TB volumes into a single 2 TB volume, you could lose important data on the volume if just one of your hard disks fails. Backups are crucial if you go this route.
UnQuote

If, in your opinion, either of the above concerns are valid, then I would rather stay with the original proposition of mine with :-

1. Recreating new shares as required and deleting now redundant shares
2. Create the appropriate directories and delete now redundant ones as required
3. Altering the fstab file to mount all existing and new drives at the appropriate mount points

This would only apply to the media share(s) for me as I don't expect my data share to ever likely to occur with current content in the vicinity of 200 gb inclusive of massive duplication of files.


Let me know what you think.


Best regards


Deepak

---

### Post by darkod on 2016-11-27
Do it however looks easier and better to you.

But you understood the LVM warning wrong. The warning is ONLY about the disk you are introducing to the LVM, not about already exosting data (inside or outside LVM). So, if you move all data to one disk, you can configure the second as LVM without losing any data. Then move the data onto the LVM and add the first disk to it. From this point on, you have both your disks as LVM. If you add a third disk, you don't need to move any data anywhere...

But as far as a higher risk is involved, that's true. Joining more disks in one logical volume is dangerous if a disk fails. But even in such case I'm not sure whether you will lose all data or only the data on the failed disk.

The upside of LVM is much better utilization of your storage space, and flexibility to expand storage easily. The downside is you need to take more care about backups, but that is also needed for big amounts of data regardless if you use LVM or not...

---

### Post by agarwaldvk on 2016-11-27
Hi darkod



In hindsight, that would make a lot of sense. They couldn't have built a system where you would be required to do what I thought you had to - that would be a pretty awful system, wouldn't it? But my interpretation could one of the ones that could be made and since I didn't know any better I thought I will work on the worst case scenario.


On further reading, it appears that I can create a new volume group using just one (1) disk - my existing drive containing my media data by this command :-


sudo vgcreate volume_group_name /dev/sda 

And then extend the volume group create above by :-

sudo vgextend volume_group_name /dev/sdd    (if I am at a point where I need to add another physical drive , say 2 tb capacity)

So, in this case I would I lose my data as this drive would be introduced to the LVM for the first time? To avoid this, I will need to copy this data to another drive and configure this drive as LVM and subsequently add drives to this volume group! I will obviously need to buy another disk then. Will try it when I have bought one when I nearly fill up this one and configure them as LVM's. I quite like the idea.

My idea is to then backup these drives on 1 or 2 external drives depending upon their capacities maybe once in 1 or 3 months as these don't change by much very often anyway!

By the way, copy data to a powered external USB HDD connected to the server computer itself would be faster than over the home network, would it?

When I was trying to copy some data from my windows PC to a powered USB HDD it was doing it at the rate of around 30 MB/sec and at around 10 MB/sec over the home network. That wouldn't necessarily hold if it were connected to my Ubuntu machine - would it be reasonable to presume that the data transfer rate would be dependent upon the computer hardware as such? Just wondering if it would be better to backup externally over the network or connecting it to the machine itself!



One other thing, can I have my media drive(s) as LVM's and the data drive not as LVM as I don't think it will get ever beyond 2 tb?


Thanks again!


Best regards


Deepak

---

### Post by darkod on 2016-11-27
For LVM you also use partitions, not whole disks. So it would be /dev/sda1, not /dev/sda. But I'm confused, why buying another disk now? You just formatted your disks one by one which means all data fitted on one disk (or one disk plus temporary external storage), yes? Or not?

Because you can do the same now.

And yes, you can keep the data disk outside the LVM but that doesn't make much sense, especially if you expect the data share to be much smaller than the 2TB. That way the rest of that disk is sitting empty and unused...

Copying over 100Mb home network will be about 10MB/s max. Copying to usb hdd could be faster, especially on usb3. But it also depends, it's not always a rule. If you had a 1Gb home network then usually copying over network would usually be faster than usb, even usb3.

You have enough info now, you only have to decide how you want to do things... Don't forget that after create volume group you also need to create logical volume(s) with lvcreate. And then you format with ext4 those LVs and mount them and use them...

---

### Post by agarwaldvk on 2016-11-27
Hi darkod


Seems like I am only helping to create more confusion - seems to become my middle name!

My data share - I don't want to touch - I have been able to get it working after a lot of pain and a lot of help from you! Also, it sits on a separate physical drive of 2 tb capacity. I do not envisage for that to go beyond that ever!

I do realize that not including in the LVM would waste some space - no two ways about it - but I guess that's the price you pay for not knowing. I wish I knew more and was better equipped technically!

I am happy to be considering LVM's to my media data - currently all of it stored on one (1) single physical internal hard disk drive of 2 tb capacity. No external HDD is used. I was just thinking about using an external HDD for backing up this media information as it doesn't change very much very often - I am only looking backup it up may be once in 1 or 3 months.

The stuff that I quoted is from here :-

[https://www.digitalocean.com/community/tutorials/how-to-use-lvm-to-manage-storage-devices-on-ubuntu-16-04]("https://www.digitalocean.com/community/tutorials/how-to-use-lvm-to-manage-storage-devices-on-ubuntu-16-04")

Is this not a good reference material?

Wouldn't that refer to the whole disk (as in /dev/sda) rather that the partitions (/dev/sda1) as you suggested - to create the volume groups? It even says, use this command to create logical volumes like so :-

sudo lvcreate -l 100%FREE -n test2 LVMVolGroup


I am not looking at buying anything now! I was thinking that when this disk gets full then I will buy one and then implement LVM as then I will have two (2) disks. But you say :-

> 
Because you can do the same now.


And I say how? How do I do it using the partitions and not the whole disk?


P.S. I will check that tonight and then decide whether its better to do it over then etwork or the external HDD directly connected to the machine (I think it does have USB3 connection)


Best regards


Deepak

---

### Post by darkod on 2016-11-28
Yes, in that tutorial they use whole disks instead of partitions. You can do it both ways. I always prefer using partitions for LVM or mdadm raid, instead of whole disk identifiers.

I said you can do it now assuming you move data around. Since you don't want to touch the data disk any more, you can't do it without getting new disk or moving the media data temporarily somewhere... So you can wait until buying new disk and implement LVM then if you want to, like you said...

---

### Post by agarwaldvk on 2016-11-29
Hi darkod


As things are relatively fresh in my mind and you also are quite aware of my set up at the moment, just so that when the time comes, I can do it then, can you please advise if this would be the right way to do it (presuming that I have bought a new drive (again a 2 tb HDD) and want to add to an existing LVM.

1. Move the entire contents of my media drive to a temporary folder on my data drive
2. Create a volume group
3. Add this now blank drive to the newly created volume group (this would erase everything on it)
4. Create a logical volume for this drive
5. Recopy the data back on to this volume

Do you think I have got this one right!

Just one more thing, how would I specify just the partition instead of the whole drive - do I  just specify '/dev/sda1' instead of '/dev/sda' and be done with it?


Best regards


Deepak

---

### Post by darkod on 2016-11-29
Yes, /dev/sda1 means partition #1 on disk sda. While /dev/sda is the whole disk. So to add the partition as LVM physical device you simply do:
```
sudo pvcreate /dev/sda1
```

The steps to move the data around and create LVM would be correct if you are doing it right now. But if you are doing the procedure after you buy new 2TB disk (let's say sdd), then you don't need to move the data twice. In such case simply do:
1. Create one big partition sdd1
2. Set it as LVM PV
3. Create one VG adding sdd1 to it
4. Create the LV inside this VG
5. Format the LV and mount it at temporary mount point
6. Copy all data (retaining permissions) from media share to this temp mount point
7. Unmount sda1 from the media mount point and mount the LV on it
8. Check if everything is good and start using this LV as your share
9. After you are happy everything is working and all data is there, add sda1 to the VG to raise the free space

That would be it... This way you move the data only once. But of course this assumes buying a new disk, like you said...

---

### Post by agarwaldvk on 2016-11-30
Hi darkod


Thanks for your assistance on this. I will now mark this as solved and hopefully when I am ready to buy another disk, hopefully I would be able to create the LVM.


Best regards


Deepak

---

