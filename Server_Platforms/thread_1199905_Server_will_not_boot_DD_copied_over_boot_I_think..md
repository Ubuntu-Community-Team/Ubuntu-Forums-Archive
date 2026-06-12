---
title: "Server will not boot DD copied over boot I think."
date: 2009-06-29
forum: Server Platforms
---

### Post by Raymond Day on 2009-06-29
I was on my ubuntu server typing commands. I wanted to put a Floppy image on a Floppy. But I typed the DD command wrong and when I did not hear the sound of the floppy going I press Ctrl C. All seemed good.

I got the image on the floppy. But hours leter it was not doing out DHCP address'. I rebooted it but it did not boot. So I put a monitor on it. It said something like DOS can not boot press any key. I hooked a keyboard on it and it just keeps going to that screen.

So I booted a live Ubuntu DVD. Typed fdisk -l and here is what I get:

```
root@ubuntu:~# fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb824568a

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start          End      Blocks   ID  System
/dev/sda1   ?      266489       495373  1838516058   fe  LANstep
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?      101574       223172   976729911   c0  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?       68013       179889   898645175   64  Novell Netware 286
Partition 3 does not end on cylinder boundary.
/dev/sda4   ?       14072       14072            5   6f  Unknown
Partition 4 does not end on cylinder boundary.

Parition table entries are not in disk order
root@ubuntu:~#
```

It's a 1TB green WD drive. I did have it on a 750 GB I think then used True Image backup to put it on this 1TB and it had a 80GB partition then the rest of the room the other partition. When TIB copied it from 750 GB to 1 TB it made both partitions that % bigger.

It was a DOS floppy I was DD restoring. So I think the fdisk -l is showing that. I quit it in about 5 sec. I guess. So it did not copy the hole floppy to the start of the hard drive. Only a little. I am not sure how little.

Is there a way to fix this? Could I reinstall ubuntu on top of it's slelf if that's what it takes?

What's the best way to fix this?

-Raymond Day

---

### Post by tgalati4 on 2009-06-29
On a command line:

history

See what command you actually typed.  If you did /sda1 instead of /fd0 then, yes you trashed your boot disk.

Yes, you can reinstall ubuntu using the "no format" option when going through the installation guide.  This will overwrite ubuntu-specific files but keep the user files intact.  You will loose configuration settings, but you may be able to recover.  

My guess is that critical file system information is stored within the first 1.44 MB of the partition.  There may be a copy of the superblock outside of this boundary that perhaps fsck could find.  I really don't know.  

Linux can recover from a fair amount of fs damage, but in this case it may be fatal.

I have had luck resurrecting partitions using cfdisk by rewriting the partition table with known values.  It may not work in your case because besides the partition table being overwritten, the first 1.44 MB of the partition is now a boot floppy image.  It would be a fast floppy boot though.

For future reference: writes to USB and floppies are delayed by the file system to reduce wear-and-tear on flash disks.  Don't eject them too soon!

---

### Post by Polaris96 on 2009-06-29
just a guess but i'm betting you had your infile and outfile mixed up when you called dd.

---

### Post by Raymond Day on 2009-06-30
About a year ago when it was on a 750 GB drive. I used True Image backup on that 80 GB part. of it. This has a boot on it. I can restore just the boot part. But now it's on a 1 TB drive and True Image backup copied the 750 GB to the 1 TB and expanded the 2 part.

All so it did not DD copy the hole floppy. I press Ctrl C as soon as I did not hear the USB floppy going. I guess about 5 sec. in to it.

I guess I could use True Image to back up the boot how it is now then restore the year ago one and see how that works?

-Raymond Day

I restored the old boot with True Image backup. But like I said it was on a 750 GB drive then not a 1 TB drive. It first boots like this now:

> GRUB Loading stage1.5.


GRUB loading, please wait...
Error 17

Just stays there.

Is there any program can run on it to like rebuild the partition table?

-Raymond Day

I found a old backup I did on 10/28/2008. This was on the 1TB drive. I restored the boot block but it still gives the GRUB loading, Please wait... Error 17.

I guess I can start a restore and hope it started the restore on track 0 then after about 10 sec. stop the restore. I guess that my work.

All so when I start True Image restore it says "Failed to read from the sector-13,833,612 of the hard disk 1". I just do Ignore All.

Looks like I can't just do a restore for a little. Because it ask for the target partition. But it shows the junk type ones.

I will try a full restore and stop it after a little. Hope it just restores the start part of the hard drive.

But it ask "Yes, I want to delete all the partitions on the destination hard disk drive before restoring." I just want to delete that start no all of it.

I guess I will do a backup how it is now. Then can say yes to delete and hope it don't formate and just starts to restore.

-Raymond Day

I order a 1 TB hard drive. About $80. I have the backup that is about 1 year old.

I can restore that and thinking just DD copy the first 1.44 MB of the partition from each drive.

So I don't mess up the DD command can some one post just how I would type that command?

I can use the drive then for a backup drive. I think I will set it up so it backs it up like every 48 hours with rsync. I seen something was wrong with this in about 12 hours. Rebooting it I know for sure.

-Raymond Day

---

### Post by tgalati4 on 2009-06-30
Boot  the live CD and mount the problem disk and see if your data is there.

---

### Post by Raymond Day on 2009-06-30
Would booting from a live CD and doing a e2fsck command fix it?

I should get the new 1 TB drive tomorrow and will restore a year old backup on it. Then update it and check what changed at the start of the older 1 TB drive.

-Raymond Day

---

### Post by volkswagner on 2009-06-30
If the partition table is damaged you may fix it with testdisk.

You can install testdisk after booting the live cd.

Boot live CD, then

```
sudo apt-get update
```

```
sudo apt-get install testdisk
```

You may need to edit your /boot/grub/menu.lst to have it point to the proper partition location for /.  This may be different from your backup image, due to a different disk, especially if you changed partitions or went from ATA to SATA disk.

---

### Post by boof1988 on 2009-06-30
> **volkswagner said:**
> If the partition table is damaged you may fix it with testdisk.

You can install testdisk after booting the live cd.

Another option for use of *testdisk*...

The [GPartEd LiveCD](http://gparted.sourceforge.net/livecd.php) has [*testdisk*](http://en.wikipedia.org/wiki/TestDisk) included with it.

The GPartEd LiveCD even has a load to RAM option, so that the optical drive can be freed-up (after start-up of the OS) if needed.

---

### Post by windependence on 2009-06-30
Hehe, we don't call dd "disk destroyer" for nothing. Be very very careful of your command syntax. ;-)

-Tim

---

### Post by Raymond Day on 2009-07-04
Thanks for all the help people.

I order a 1 TB drive and copied my about 1 year old backup to it. Then boot that with the other none boot hard drive on the other SATA port. DD copied the start of the year old hard drive, the size of the floppy image to a file named **good1474560-mbr.bin** Then did this command:

```
dd if=good1474560-mbr.bin of=/dev/sdb bs=1 count=1474560 skip=446 seek=446
```

Powerd off and unhooked the backup. It booted but not all they way. It said I could press control C to go on or password to do maintenance. I did password and ran this command:
 
```
e2fsck -y -f -v /dev/sda1
```
 
At first I just did it to sda and it said e2fsck not found. I rebooted it and the 2nd time the e2fsck command worked. Because I did it on sda1 not sda. It took about 20 minutes. Lots of messages scrolling by.

Then I rebooted again. It said file system has errors and this time at lest it auto checked it. I did not have to run the command by hand.
 
It took about 20 minutes to check it this time too.
 
It booted up and all looks good but any web page that uses the data base can not be display! Ran a update on it and it had some updates to do.
 
Went in Webmin and backed up all the databases on it to the backup folder in another server I have. Webmin sees all the databases very good.

I have Wordpress. Going to the web link it just says page can not be displayed!

I just go to it's IP and /blog and it should go there. Apache Aliases directory for wordpress is from /blog to /usr/share/wordpress and that's right where wordpress still is. All the files there still look good but Apache just will not run it! Or seems like any thing else that uses the database.

Web pages that just have text and photos display right.

I just don't know what could be wrong any one know what I could do to fix this?

At lest it's booting and running again.

-Raymond Day

Ran the TestDisk 6.9 like a post said in here. But that's after it booted. Looks like it could of fixed the partitions. It just scans the hole drive to see were they are.

It came back saying "Structure: Ok."

I need something that can see what web pages don't come up that use the database now.

-Raymond Day

I don't think my php is working. That my be what is wrong now. I made that little test file. phpinfo.php but when I went to it Internet Explorer just says cannot display the webpage.

Is there a way to fix php or reinstall it? I guess the little phpinfo.php was a test for it. But it don't work.

Still looking on google if there is a way to reinstall or fix it.

-Raymond Day

I gave up and using the year old backup. Trying to copy all the changes to it. Copied the data base files and now some folders.

Working good.

-Raymond Day

What is the best way to copy? I like to make a list of just files that are older then the backup. Then pick from that list what to copy. To only tell it changed or new files.

I am thinking to use:

cp -rpfu SOURCE DEST

But I don't think cp has a way to copy only changed or new files.

Is there a way to do it with scp ?

I am just copying from one drive to the other on the same system.

-Raymond Day

---

### Post by windependence on 2009-07-05
rsync.

-Tim

---

### Post by Raymond Day on 2009-07-05
I am not sure how to do rsync. I am testing it but get errors.

I have a folder named mystuff. It has a lot of the same things in it and a lot of new things too. So I did this rsync command:

```
rsync -avn /root/tmp/oldp3/mystuff /home/part2/mystuff .
```

It made a long list looks right to me so I will take out the -n that shows what would happend.

Does this look right?

-Raymond Day

It looks like it's copying over the same files that are all ready there. Is there a way to tell rsync to only copy new and changed files? It would be a lot faster then copying every thing.

-Raymond Day

It was copying but got this error:

```
rsync: writefd_unbuffered failed to write 4 bytes [sender]: Broken pipe (32)
rsync: write failed on "/root/mystuff/acer-atom-laptop3.tib": No space left on device (28)
rsync error: error in file IO (code 11) at receiver.c(259) [receiver=2.6.9]
rsync: connection unexpectedly closed (969926 bytes received so far) [generator]
rsync error: error in rsync protocol data stream (code 12) at io.c(454) [generator=2.6.9]
rsync: connection unexpectedly closed (724 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(454) [sender=2.6.9]
```

So looks like it ran out of space! Some how it looks like it's putting it on the 1st part. It's about a 95 GB and the other Part. is the rest of the 1 TB drive.

Here is a df of it now after it got the error:

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             98702380  96457936         0 100% /
varrun                  500096       308    499788   1% /var/run
varlock                 500096         4    500092   1% /var/lock
udev                    500096        48    500048   1% /dev
devshm                  500096         0    500096   0% /dev/shm
/dev/sda3            873435420 590581388 282854032  68% /home/part2
/dev/sdb1             98702380  73665940  20018944  79% /root/tmp/oldp1
/dev/sdb3            873435420 626368620 247066800  72% /root/tmp/oldp3
```

The /root/rmp/oldp1 is the old drive that was not booting and it's Part. 1 The /root/tmp/oldp3 is Part. 3 of it.

So /root/tmp/oldp3 should go to /home/part2

I am not sure why rsync got an error and filled up the 1st Part.

-Raymond Day

I seen what was wrong it copied it to /root/mystuff that's on the 1st Part.

So I did: rm -rf /root/mystuff

I got to find out just how to do the rsync right. What am I doing wrong?

-Raymond Day

I think I got it. Looks like this line worked:

> rsync -avu /root/tmp/oldp3/mystuff  /home/part2/

Looks like it only copied the new and changed files. From /root/tmp/oldp3/mystuff folder to /home/part2/ in the mystuff folder there. It's the / or no slash at the end it looks like.

Now to find out were I have other folders with new and updates in them.

-Raymond Day

I am not sure about this can any one tell me if this would be the right command to copy the 2nd big part part to the new one?

rsync -avu /root/tmp/oldp3  /home/part2

I guess I should of name the oldp3 to part2 so it would be the same.

I want to make sure of this command before I do it. It's a big one. I hop some one can tell me.

After I tested it with the -n it came back and said this:

```
sent 5397366 bytes  received 1029158 bytes  34458.57 bytes/sec
total size is 640532123739  speedup is 99670.07
```

So I hope some one will know if it's right?

-Raymond Day

---

### Post by windependence on 2009-07-06
Looks OK to me, but make sure you check the man page for switch options. The whole idea behind rsync is only to write changed information after the first replication. It's perfect for what you want to do.

-Tim

---

### Post by Raymond Day on 2009-07-06
What I copied as now is this:

```
rsync -avu /root/tmp/oldp3/mystuff  /home/part2/

rsync -avu /root/tmp/oldp3/raymond  /home/part2/

rsync -avu /root/tmp/oldp1/home  /

rsync -avu /root/tmp/oldp1/root  /

rsync -avu /root/tmp/oldp1/var  /
```

Some things still are not working. Like iZeit calendar. It comes back with a error like this:

```
Fatal error: Call to a member function close() on a non-object in /usr/share/cal/includes/classes.php(2) : eval()'d code(1) : eval()'d code(1) : eval()'d code on line 62
```

But most things are working. It took a long time to set all this up before all this. Now I have to see if I can get all working like it use to.

It be good if I could just use my old one still. It's just not bring up webpages use the data base. But the data base is working. I guess it's some web settings or php setting. Maybe it was something at the start of the hard drive that got messed up with the DD copy.

Thank you for all the help here.

-Raymond Day

---

### Post by windependence on 2009-07-06
Remember that if you are trying to run the files from your backup location, it may not work because they are in a new location and some of the scripts and databases won't be able to find them. You would have to restore them to their original location to do that.

-Tim

---

### Post by Raymond Day on 2009-09-09
It's been a wile now and most is working good now on it. I just hooked up the other drive set it back up as a DHCP server and copied it's config file for that over to it. I had some MAC address' in it so they keep there IP's.

I still want to set up some things yet in it. But it's working real good and it's:

root@small:/# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"

-Raymond Day

---

