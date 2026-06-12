---
title: "Ubuntu 14.04 Server MDADM add disk to Raid0 array"
date: 2016-06-06
forum: Server Platforms
---

### Post by sparticle2000 on 2016-06-06
Hi I was hoping to get some advice from the experts.

I have a 2 disk mdadm raid0 array. I want to add another disk to it. Many hours of googleing and reading man etc. led me to believe this was a perfectly acceptable thing to do. Seems logical that you might want to extend your array by adding more storage!

I am not worried about the content of the drives as I can recreate this data. It is Raid 0 for performance. It will probably end up with 4 drives as requirement grows.

I issued the following command. 
~$ sudo mdadm --grow /dev/md0 --level=0 --raid-devices=3 --add /dev/sdd1
mdadm: level of /dev/md0 changed to raid4
mdadm: added /dev/sdd1
mdadm: Need to backup 3072K of critical section..





It seems to have changed my array to Raid 4 array. 

$ cat /proc/mdstat
Personalities : [raid0] [raid6] [raid5] [raid4] 
md0 : active raid4 sdd1[3] sdb1[0] sdc1[1]
      3907025920 blocks super 1.2 level 4, 512k chunk, algorithm 5 [4/3] [UU__]
      [=>...................]  reshape =  5.3% (105329668/1953512960) finish=820.2min speed=37552K/sec
      
Man suggests that this is normal behaviour and it is  going to change to Raid 4 add the disk(s) and then change back to Raid 0.

 From 2.6.35, the Linux Kernel is able to convert a RAID0 in to a  RAID4
       or RAID5.  _mdadm_ uses this functionality and the ability to add devices
       to a RAID4 to allow devices to be added to a RAID0.  When requested  to
       do  this,  _mdadm_  will  convert the RAID0 to a RAID4, add the necessary
       disks and make the reshape happen, and then convert the RAID4  back  to
       RAID0.
Can anyone tell me if this is likely to succeed as you can see it is going to take a while to reshape to Raid 4. I presume then the same amount of time to reshape to Raid 0!

Any help appreciated. If @rublylaser is out there I would be interested in your opinion Zak.

I also noticed that the version of mdadm running on my 14.04 server is 4 years out of date! and was only installed recently. 

Cheers
Spart

---

### Post by sparticle2000 on 2016-06-07
OK so no help from here. I am writing this up in case it helps others.

The reshape eventually finished and the filesystem was as expected not expanded to fill the array. 

Before creating the 2 drive raid0 array both drives simply had a single GPT partition with a Ext4 FS and zero reserved space 

I then created the array using:
sudo mdadm --create --verbose /dev/md0 --level=0 --raid-devices=2 /dev/sdb1 /dev/sbc1
All went well
Setup /etc/mdadm/mdadm.conf
updated initramfs
sudo update-initramfs -u
Made a new FS
sudo mkfs.ext4 -b 4096 -E stride=128,stripe-width=256 /dev/md0
sudo tune2fs -m 0 /dev/md0
Setup /etc/fstab to mount the /dev/md0 array
Stopped the array
sudo mdadm --stop /dev/md0
Restarted it
sudo mdadm --assemble --scan
All was well /dev/md0 was assembled and started at boot.

Fast forward to adding another drive to the array. 
I had another 2TB drive in the system that I could use as another raid0 member it was already single partition formatted with Ext4 
So I unmounted it
sudo umount /dev/sdd1
Add it to the array
sudo mdadm --grow /dev/md0 --level=0 --raid-devices=3 --add /dev/sdd1
Wait about a day as mdadm changes your raid0 2 disk array into a raid4 3 disk array then back to a 3 disk raid0 array
Even though this system is a dual quad core Xeon with a LSI 9211-8i controller and the disks are WD RED connected at 6Gbps I could only get c.30000K throughput even after setting 
/proc/sys/dev/raid/speed_limit_min to 200000 and max to 20000000
After it completed I had a new array showing with 3 disks but the same size as the original 2 disk array
So I unmounted the array
sudo umount /dev/md0
Checked the FS
sudo fsck.ext4 -f /dev/md0
Resized the array to take advantage of the new space
sudo resize2fs /dev/md0
Rechecked it
sudo fsck.ext4 -f /dev/md0

Updated /etc/mdadm/mdadm.conf
sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf
I then edited it and # out the original ARRAY line - **This turned out to be very lucky for me!**
updated initramfs
sudo update-initramfs -u
And tried to restart the array as above
sudo mdadm --assemble --scan
IT DID NOT WORK
Then tried to restart the array using the UUID as reported by sudo blkid
sudo mdadm --assemble /dev/md0 --uuid=AS REPORTED BY sudo blkid
This did not work! At this point slight panic!
I found I could assemble it from the component parts as created
sudo mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1
But what if the /dev/sd's changed
SO I stopped it 
sudo mdadm --stop /dev/md0
Then I used the original UUID from the 2 disk array that I had # out in the /etc/mdadm/mdadm.conf file and it started fine
sudo mdadm --assemble /dev/md0 --uuid=YOUR ORIGINAL UUID OF THE ORIGINAL ARRAY
sudo update-initramfs -u
At this point I have a working 3 disk raid0 array HOWEVER

There a couple of weird things
sudo blkid shows the original 2 disks as 
/dev/sdc1: UUID="ORIGINAL UUID OF ARRAY" UUID_SUB="ORIGINAL UUID OF PARTITION" LABEL="SERVER:0" TYPE="linux_raid_member" 
/dev/sdb1: UUID="ORIGINAL UUID OF ARRAY" UUID_SUB="ORIGINAL UUID OF PARTITION" LABEL="SERVER:0" TYPE="linux_raid_member" 
And the additional disk is still showing
/dev/sdd1: LABEL="DATA2" UUID="ORIGINAL UUID OF PARTITION" TYPE="ext4" 
Same as before it was added to the array!

The /dev/md0 array is now showing a new UUID that it cannot be started with!
/dev/md0: UUID="NEW UUID THAT DOES NOT MATCH ORIGINAL UUID" TYPE="ext4"
[B]I have to start the array with the original UUID!!!
[/B]
I am a little confused by this behaviour and nervous! The additional single partition drive is clearly added to the array but is not recognised in blkid as a constituent of the array.
I am not sure of the implications of this.
I hope this help someone else, if there are any experts about who can shed some light on the odd behaviours (might be normal for all I know) that would be very helpful.

Cheers
Spart

---

### Post by lukeiamyourfather on 2016-06-07
There's practically no reason to use RAID 0 these days. SSD has made RAID 0 obsolete. If you just need expandable storage spanning many disks look at ZFS or LVM.

---

### Post by sparticle2000 on 2016-06-07
'SSD has made raid0 obsolete' - This is news to me how a Disk technology had made raid0 obsolete. SSD's re still expensive I can get WD RED's for a quarter or less of the price in the TB range. I would need a remortgage to recreate the arrays using enterprise class SSD's. Raid0 is extremely performant across multiple drives and is it seems the simplest solution. LVM does not give me any advantages when all I want is a large single storage device to mount and adds complexity. If I had lots of volumes and differing sized disks it might be useful! ZFS comes with its own resource issues and again offers no advantages and lots of complexities. 

My use case as posted is to create a large performant array that can be extended, maximising available space. I don't care about redundancy. This data can all be recreated if necessary from our main Raid6 array in another system, although it would be nice to avoid that given the time it takes to restore.

Spart

---

### Post by darkod on 2016-06-07
And there within lies the "problem"... Raid0 is not really raid (hence the 0) so I am not sure at all it can be expanded like other SW raid levels. And honestly, I am too busy now to search for that info on raid0.

If you are not worried about redundancy and you have a copy of the data, what I would have done is destroy that two member raid0 and create new three member raid0. That way you will get your expanded raid0 array without all the fuss above...

The fact that it "converted" the array to raid4 and then back to raid0 might have something to do with the changed UUID. On the other hand, maybe it didn't do the reshape correctly...

---

### Post by sparticle2000 on 2016-06-07
The array reshaped fine it seems. Just took a while. Passes all tests I can think of to run on the filesystem etc. Is noticeably snappier to access than individual shares of separate drives over the network. It seems the conversion to raid4 is because it cannot add a drive to raid0. After a further cold boot of the server the added disk showed up correctly in the output of sudo blkid
/dev/sdd1: U[COLOR=#000000]UID="ORIGINAL UUID OF ARRAY" UUID_SUB="ORIGINAL UUID OF PARTITION" LABEL="SERVER:0" TYPE="linux_raid_member" 
So I am a little happier. 
Maybe need a drive extender type of approach for linux. Something like this [/COLOR]https://www.greyhole.net/[COLOR=#000000]

Cheers
Spart[/COLOR]

---

### Post by lukeiamyourfather on 2016-06-07
Here's what you do with ZFS to add more drives. No waiting for reshaping or other nonsense like you have with RAID because it dynamically stripes to drives or VDEV with empty space. You could even do this while the pool is in heavy use.

```
sudo zpool add -f -o ashift=12 tank ata-ST4000DM000-7777
```

Replace the last argument with the ID of the drive you actually want to add. Typically ZFS pools are made of VDEV (like mirrors or RAID Z/Z2/Z3) but if you don't need redundancy you can just add individual drives. ZFS is a lot more elegant and higher performance than Greyhole and a lot more flexible than LVM. Since ZFS is copy on write all of the writes are sequential. If you're working with compressible data then you can compress the data on the fly with LZ4 compression which is usually faster and higher performance than working with the uncompressed raw data. I still think RAID 0 is obsolete.

---

### Post by sparticle2000 on 2016-06-07
Looks like ZFS needs a lot of resources 16GB ram min. Looks interesting though. I'll need to so some reading.

Cheers
Spart

---

### Post by sparticle2000 on 2016-06-08
[COLOR=#DD4814][COLOR=#000000]@[lukeiamyourfather]("http://ubuntuforums.org/member.php?u=774656")[/COLOR][/COLOR][COLOR=#000000] I think you have convinced me to look at ZFS for this use case.

I can retask and existing server currently it is a Dual Quad Xeon 24GB ram. 14.04.1 LTS running off Raid 1. 3 8 Drive slots for data drives.

Initially I wold like to move the now 3 disk Raid0 array to a new ZFS pool. I would like to mount this pool on a single top level mount point etc /media/analysis-pool 
I would then like to create a number of (datasets??? or filesystems) in that pool e.g. type1 type2 type3 etc. and have them accessible as /media/analysis-pool/type1 ....etc. The reason for the different filesystems is that I would want to turn on compression for only some of them.
I would then like to share the top level mount /[/COLOR][COLOR=#000000]media/analysis-pool over the network using samba. So a normal samba share.

In simple terms if I have understood correctly I can do something like this to create the pool

[/COLOR][COLOR=#333333]sudo zpool create analysis-pool [/COLOR][COLOR=#333333][FONT=&quot]/dev/disk/by-id/  (this would create a single disk pool 
[/FONT][/COLOR][COLOR=#000000]Then
[/COLOR]sudo zfs create analysis-pool/type1

sudo zfs create analysis-pool/type2[COLOR=#000000]etc.

Then I can add drives to this pool on the fly...
[/COLOR][COLOR=#000000]
[/COLOR]sudo zpool attach analysis-pool /dev/disk/by-id/

And the extra capacity will be available to all constituents of  analysis-pool

[COLOR=#000000]I am definitely a little confused about how to mount these storage pools. A few articles saying these are automagically mounted at boot and other saying that a more usual fstab line is needed 
[/COLOR]e.g. /media/analysis-pool  zfs defaults 0 0
I could then share this as a normal samba share right?

In essence I only need one top level share to /media/analysis-pool 

Any advice or guidance appreciated.

Cheers
Spart

---

### Post by darkod on 2016-06-08
Luke can tell you more about adding more disks after the first one, but until he replies I can comment what I know about zfs mount points. Personally I would create the pool straight away with the 3 disks if you can move their data elsewhere temporarily. No need to create pool with one disk and then add two more right away.

If you create the zpool like:
```
sudo zpool create <poolname>...
```

the mount point will automatically be /poolname. And as far as I know you don't need to manually configure it in fstab, it should be automatic.

To create a zpool with custom mount point you will need to use (among other parameters):
```
sudo zpool create -m /media/analisys-pool analisys-pool...
```

The parameter for custom mount point is -m /mountpoint.

Also, you should be able to add disks like /dev/sdX format, no need for the format Luke posted in port #7. At least that worked when I was doing some testing with 14.04 and ubuntu-zfs package. Now in 16.04 zfs is included.

---

### Post by sparticle2000 on 2016-06-08
@darkod  thank you for the reply. Yes I saw that you could use /dev/sdx but having been bitten by controllers moving hda around in the past I thought it wise to do it the more definitive way. The -m option is exactly what I was looking for. After that I should be able to share this mount point and then access /media/analysis-pool/type1 etc. I think...maybe...hmmmm.

Cheers
Spart

---

### Post by sparticle2000 on 2016-06-08
@darkod thanks for the reply. Yes I saw that you could use the usual /dev/sdx but having been bitten by controllers changing HDA's around a definitive identifier approach appeals! Thanks for the -m option that should work I think...maybe...possibly...

There are a lot of options see man zpool. So a bit more learning before diving in. I did manage to install zfs easily enough and get this when checking the kernel support
~$ sudo dmesg | grep ZFS
[   13.805779] ZFS: Loaded module v0.6.5.7-1~trusty, ZFS pool version 5000, ZFS filesystem version 5

So good to go!

Cheers
Spart

---

### Post by lukeiamyourfather on 2016-06-09
The default mount is /poolname/filesystem (or dataset instead of filesystem) which I'd stick with for ZFS because anyone who might pickup the work will expect that. Like pointed out, you can change the mount point if you want to but I'd make note of it somewhere for others.

You're correct that any drives or VDEV added will be available to any filesystem in that pool. Note that if you add single drives it will be similar to RAID 0 with no redundancy and very high performance. This is usually not recommended but if it meets your needs then it's an option. Mostly point that out for other folks who come across this and are new to ZFS.

I recommend using disk ID because drives can get plugged back in anywhere and it will work, it's easy to find failed drives, and if other drives get removed it all still works. You can change this anytime by exporting the pool and importing it again with a different kind of label (like port instead of disk ID). Different label types work better for different configurations, use what's best for your situation.

You can turn compression or whatever on and off for any filesystem. By default they inherit the behaviors of the parent. If there's no parent then it's the pool itself. No need to specify mounts for anything or edit /etc/fstab, it will mount everything for you even if you create more filesystem and pool.

When you create the initial pool or add drives I'd use the command I posted previously for reference. The "-o ashift=12" option forces 4K sectors which are standard on modern drives. The default is ashift=9 which is 512B sectors which will still work but won't perform quite as good.

This might be helpful. Some has changed since I taught the class but much of it is still applicable. When I get some free time I'll probably do another class on it and update the materials.

[http://whenpicsfly.com/wp-content/uploads/2014/09/Intro-to-ZFS-on-Linux.pdf](http://whenpicsfly.com/wp-content/uploads/2014/09/Intro-to-ZFS-on-Linux.pdf)

I'd try turning on LZ4 compression and see how it goes. I think you'll be surprised how little CPU it uses and how fast it really is. ZFS uses LZ4 compression under the hood for the L2ARC for the reasons I already stated, it's faster than not using compression!

---

### Post by sparticle2000 on 2016-06-10
Luke,

Many thanks for the note. I have been playing around with a file based pool just to get familiar with some of the concepts. Sharing is a little weird, as it is obviously managing smb sharing outside of the normal smb.conf share definitions which I have a number already defined. The share shows up if I browse for it. Need to understand permissions, it seems they are inherited. So after I create a filesystem I need to set ownership/permissions so that the share is usable. I did find a useful Webmin module for ZFS which is in dev but is good for showing the pools options filesystems etc. 

I must admit it does seem really simple at first glance but there is a lot of complexity beneath the surface, I have that horrible feeling that I could screw things up really fast...just a learning curve I guess. Not a lot of help in the commands for newbies. e.g -r -R -d switches and their contextual meaning.

I do like the file system concept and being able to control options - Compression, Sharing etc.  at a more granular level than the overall FS like EXT4 and it seems a very logical way of organising things. Just ordered a bunch of new Red's so will post my plan for implementing here if you are will to take a look.

Cheers
Spart

---

### Post by lukeiamyourfather on 2016-06-10
If you'd rather use the smb.conf file you can. The Samba features in ZFS are just convenience, there's nothing special or unique about how they function. I think most people use the smb.conf since it's been around for a very long time and most people have existing configurations that they can copy and paste.

There are ways to screw things up really fast, like adding a single drive to a pool rather than a VDEV with some redundancy. This is the most common mistake I've seen which causes people to have to rebuild their pools to regain redundancy. You don't have to worry about that since it's what you're after! :)

If your applications don't need synchronous writes then disabling them will greatly improve performance. Most workflows don't actually need synchronous writes but most people use them anyway which really slows things down (not just ZFS but on anything).

---

### Post by sparticle2000 on 2016-06-11
Like thanks for the info. I have been playing around with zfs on a couple of spare 2TB disks.

sudo zpool create -f -o ashift=9 -O mountpoint=/media/BACKUPTEMP BACKUPTEMP ata-Hitachi_HD ata-SAMSUNG_HD

that give a 2 drive pool - essentially Raid0

I created a new smb share definition and mounted the share on my Ubuntu Desktop as a standard cifs share. All was good. I could copy to the share maxing out the Gb link at about 104MB/sec. 
I mounted the share from the NAS side and could also get about 100MB/sec.

I then rsync'd 1.7 TB of data over to it from a NAS server. The best I could get throughput wise was about 20MB/sec over a Gb network with basically nothing else happening on the ZFS server. It eventually finished!

This is what I have:
```
[TABLE="class: table table-striped table-hover table-condensed"]
[TR]
[TH]Pool Name[/TH]
[TH]Size[/TH]
[TH]Alloc[/TH]
[TH]Free[/TH]
[TH]Frag[/TH]
[TH]Cap[/TH]
[TH]Dedup[/TH]
[TH]Health[/TH]
[/TR]
[TR="class: tr_tag"]
[TD="class: td_tag"][NASBACKUPTEMP]("https://192.168.0.105:10000/zfsmanager/status.cgi?pool=NASBACKUPTEMP")[/TD]
[TD="class: td_tag"]3.62T[/TD]
[TD="class: td_tag"]1.74T[/TD]
[TD="class: td_tag"]1.89T[/TD]
[TD="class: td_tag"]28%[/TD]
[TD="class: td_tag"]47%[/TD]
[TD="class: td_tag"]1.00x[/TD]
[TD="class: td_tag"]ONLINE[/TD]
[/TR]
[/TABLE]
[TABLE="class: table table-striped table-condensed table-subtable, width: 100%"]
[TR]
[TH="class: table-title"]**Properties**[/TH]
[/TR]
[TR]
[TD][TABLE="class: sub_table_container table-hardcoded, width: 100%"]
[TR]
[TD="class: col_label"]**[allocated]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=allocated")**[/TD]
[TD="class: col_value"]1.74T[/TD]
[TD="class: col_label"]**[altroot]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=altroot")**[/TD]
[TD="class: col_value"]-[/TD]
[/TR]
[TR]
[TD="class: col_label"]**[ashift]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=ashift")**[/TD]
[TD="class: col_value"]9[/TD]
[TD="class: col_label"]**[autoexpand]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=autoexpand")**[/TD]
[TD="class: col_value"]off[/TD]
[/TR]
[TR]
[TD="class: col_label"]**[autoreplace]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=autoreplace")**[/TD]
[TD="class: col_value"]off[/TD]
[TD="class: col_label"]**[bootfs]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=bootfs")**[/TD]
[TD="class: col_value"]-[/TD]
[/TR]
[TR]
[TD="class: col_label"]**[cachefile]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=cachefile")**[/TD]
[TD="class: col_value"]-[/TD]
[TD="class: col_label"]**[capacity]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=capacity")**[/TD]
[TD="class: col_value"]47%[/TD]
[/TR]
[TR]
[TD="class: col_label"]**[comment]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=comment")**[/TD]
[TD="class: col_value"]-[/TD]
[TD="class: col_label"]**[dedupditto]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=dedupditto")**[/TD]
[TD="class: col_value"]0[/TD]
[/TR]
[TR]
[TD="class: col_label"]**[dedupratio]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=dedupratio")**[/TD]
[TD="class: col_value"]1.00x[/TD]
[TD="class: col_label"]**[delegation]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=delegation")**[/TD]
[TD="class: col_value"]on[/TD]
[/TR]
[TR]
[TD="class: col_label"]**[expandsize]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=expandsize")**[/TD]
[TD="class: col_value"]-[/TD]
[TD="class: col_label"]**[failmode]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=failmode")**[/TD]
[TD="class: col_value"]wait[/TD]
[/TR]
[TR]
[TD="class: col_label"]**[feature@async_destroy]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=feature@async_destroy")**[/TD]
[TD="class: col_value"]enabled[/TD]
[TD="class: col_label"]**[feature@bookmarks]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=feature@bookmarks")**[/TD]
[TD="class: col_value"]enabled[/TD]
[/TR]
[TR]
[TD="class: col_label"]**[feature@embedded_data]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=feature@embedded_data")**[/TD]
[TD="class: col_value"]active[/TD]
[TD="class: col_label"]**[feature@empty_bpobj]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=feature@empty_bpobj")**[/TD]
[TD="class: col_value"]active[/TD]
[/TR]
[TR]
[TD="class: col_label"]**[feature@enabled_txg]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=feature@enabled_txg")**[/TD]
[TD="class: col_value"]active[/TD]
[TD="class: col_label"]**[feature@extensible_dataset]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=feature@extensible_dataset")**[/TD]
[TD="class: col_value"]enabled[/TD]
[/TR]
[TR]
[TD="class: col_label"]**feature@filesystem_limits**[/TD]
[TD="class: col_value"]enabled[/TD]
[TD="class: col_label"]**[feature@hole_birth]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=feature@hole_birth")**[/TD]
[TD="class: col_value"]active[/TD]
[/TR]
[TR]
[TD="class: col_label"]**feature@large_blocks**[/TD]
[TD="class: col_value"]enabled[/TD]
[TD="class: col_label"]**[feature@lz4_compress]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=feature@lz4_compress")**[/TD]
[TD="class: col_value"]active[/TD]
[/TR]
[TR]
[TD="class: col_label"]**[feature@spacemap_histogram]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=feature@spacemap_histogram")**[/TD]
[TD="class: col_value"]active[/TD]
[TD="class: col_label"]**[fragmentation]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=fragmentation")**[/TD]
[TD="class: col_value"]28%[/TD]
[/TR]
[TR]
[TD="class: col_label"]**[free]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=free")**[/TD]
[TD="class: col_value"]1.89T[/TD]
[TD="class: col_label"]**[freeing]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=freeing")**[/TD]
[TD="class: col_value"]0[/TD]
[/TR]
[TR]
[TD="class: col_label"]**[guid]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=guid")**[/TD]
[TD="class: col_value"]7627867869704910783[/TD]
[TD="class: col_label"]**[health]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=health")**[/TD]
[TD="class: col_value"]ONLINE[/TD]
[/TR]
[TR]
[TD="class: col_label"]**leaked**[/TD]
[TD="class: col_value"]0[/TD]
[TD="class: col_label"]**[listsnapshots]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=listsnapshots")**[/TD]
[TD="class: col_value"]off[/TD]
[/TR]
[TR]
[TD="class: col_label"]**[readonly]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=readonly")**[/TD]
[TD="class: col_value"]off[/TD]
[TD="class: col_label"]**[size]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=size")**[/TD]
[TD="class: col_value"]3.62T[/TD]
[/TR]
[TR]
[TD="class: col_label"]**[version]("https://192.168.0.105:10000/zfsmanager/property.cgi?pool=NASBACKUPTEMP&property=version")**[/TD]
[TD="class: col_value"]-[/TD]
[TD="class: col_label"][/TD]
[TD="class: col_value"][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

 
```

Why would I have 28% fragmentation on a new clean filesystem that I just copied data into? Google search turned up a lot of negative noise about fragmentation being an issue on ZFS and no tools to fix it. i.e  no defrag utility. 

Whats your view on how to correct this problem, clearly a fragmented FS will be slower than a non fragmented one in use. Is this self healing? will this fragmentation get better? I can't see it as I just gave zfs the best possible change to layout the files!

My instinct is that fragmentation will get worse the larger the arrays. 

OAN in my reading it seems that all roads in zfs land eventually lead you to the only layout that makes sense being mirrored VDEVS as the atomic elements regardless of the size of the array if you are needing any kind of resilience and therefore 50% storage efficiency is really what you should budget to accept if you are going to use zfs in anger with large production data volumes that you care about. Future proofing I am a little unclear about as VDEV's are immutable. It seems that I can replace a drive in a VDEV with a larger one let it do its stuff then replace the other side with a larger one etc. Need a lot more reading and tutorial before this point I think.

Cheers
Spart

---

### Post by lukeiamyourfather on 2016-06-13
There's a lot of FUD out there about the fragmentation. That indicator for the amount of framgentation is a new feature just within the last year or so. I think it does more harm than good people it makes people worry about fragmentation when they don't actually have to. I personally haven't had any problems with it in production and real world use cases (a few drives to dozens and dozens of drives in a pool). Believe it or not others like ext4 also don't have defragmentation. At some point ZFS might get defragmentation and the ability to remove drives or VDEV from a pool but it requires a lot of work under the hood which may or may not be the best course of action (it's called block pointer rewrite if you want to search for it).

I'm a fan of rsync for a lot of things but speed isn't something it's known for. If you end up using ZFS elsewhere check out "zfs send" and "zfs receive" which can be used to send snapshots between systems for things like backup or replication (it's really fast). It will keep everything if you want like previous snapshots, metdata, etc. A literal copy of the file system itself rather than the files in it.

I don't see why you think all roads lead to mirror VDEV. There are lots of good options depending on your needs. I find that RAID Z2 with six to eight drives is nice and do many VDEV like that as the array size grows. It gives a good balance of performance, redundancy, and flexibility at least for my needs. Immutable isn't really the right word, you can swap out smaller drives for larger drives but the geometry of the VDEV can't change so a six drive RAID Z2 will always be a size drive RAID Z2. Unless of course you blow it away and start over, there's always that option.

---

