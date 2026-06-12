---
title: "Power went out, Now system is read only"
date: 2011-06-15
forum: Server Platforms
---

### Post by 1serveyou on 2011-06-15
I've done a lot of search and already kind of fixed part of the problem, so this is where the fun comes in. I went away for the week, and not until the day I got back I lost power while out, and my computer rebooted after the power outage to Mac osx, which it's supposed to do as I'm using a Mac Pro and have a regular version of OSX 10.5 on there and my ubuntu server. I restart my computer and I get a few errors and my raid5(3 1tb drives) doesn't mount and says read only for everything else. I finally found a way to remount that raid which while in root I could create new folders and move folders, but only on that raid. I wasn't able to do anything with my boot drive. The weird part is, that now I can't ssh into the server and webmin won't even load. I'm still relatively new(little over a year, but honestly, not much has gone wrong to need to troubleshoot) to ubuntu server, so I'm not that best at troubleshooting it. Any help would greatly be appreciated, I won't be home till later tonight, but any tips/tricks/ideas I can try when I get home would be great, or if you need any info, I can get it to you. Thanks in advance!

---

### Post by SeijiSensei on 2011-06-15
If Linux will only mount the root partition as read-only, its filesystem contains errors that need correcting.  You should try booting from the Ubuntu CD, go to a root shell, and run "fsck /dev/sda1" or wherever the partition the filesystem root ("/") is mounted.

---

### Post by ruffEdgz on 2011-06-15
> **SeijiSensei said:**
> If Linux will only mount the root partition as read-only, its filesystem contains errors that need correcting.  You should try booting from the Ubuntu CD, go to a root shell, and run "fsck /dev/sda1" or wherever the partition the filesystem root ("/") is mounted.
 I agree with SeijiSensei on this but if you need to get something before rebooting, you could try and remount your root (/) file system:
```

sudo mount -n -o remount,rw /

```
I have had to do this when problems happens on my root file system but needed something first before rebooting and completing an fsck.

If the remount works, you can then run this command before rebooting to force a fsck:
```
touch /forcefsck
```

Cheers!

---

### Post by SeijiSensei on 2011-06-15
> **ruffEdgz said:**
> I agree with SeijiSensei on this but if you need to get something before rebooting, you could try and remount your root (/) file system [read-write]

I've done this, too, but only in dire circumstances.  If you simply need to copy some files from the impaired file system, boot from the CD and use the "Live CD" or "Try Ubuntu" mode.  You'll be able to mount the damaged filesystem read-only and copy the items you need to a USB key.  Then you can reboot and fix the filesystem.

One thing I'd definitely avoid is writing to a damaged filesystem that is not mounted at boot.  You risk the chance of exacerbating the damage.

Oh, I also recommend getting a small home UPS.  [APC]("http://www.newegg.com/Product/Product.aspx?Item=N82E16842101311")s work well with Linux.  You can run the [apcupsd]("https://help.ubuntu.com/community/apcupsd") daemon to monitor the UPS and gracefully power the system down if an extended power failure is detected.  If you have a network, you can run [apcupsd]("https://help.ubuntu.com/community/apcupsd") on the other machines as clients.  They'll be informed about a power failure by the server and act accordingly.

---

### Post by 1serveyou on 2011-06-16
Last night I was able to run fsck on sda4 which my / is on, and this is what it returns:

[IMG]http://i.imgur.com/mHmsQ.jpg[/IMG]

I'm not sure how to fix this. Also since I'm using a software raid, is there anyway for me to pull the information off of it, so worst case scenario I can at least grab my data off that and format the main drive? 

Also I can't edit the fstab, so not sure how I would mount a drive to transfer the files over. I believe I had formatted it to be in ext4 format as well.

P.S. I remember earlier last week I was playing around with iptables and acl, could this be a reason why webmin can't connect to the server either?

---

### Post by SeijiSensei on 2011-06-16
You can try the alternate superblock approach, but you might be out of luck depending on the amount of damage to the file system.  Here's a [good how-to]("http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/") on the subject.

---

### Post by 1serveyou on 2011-06-16
> **SeijiSensei said:**
> You can try the alternate superblock approach, but you might be out of luck depending on the amount of damage to the file system.  Here's a [good how-to]("http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/") on the subject.

I'm thinking worse case scenario and when I get home that how to doesn't work, is there anyway to save that or get the information off of my raid since my raid(software raid) is on a different drive and partition? I don't mind restarting a new server, but rather not lose that data that is on those drives. Last time, I didn't raid those drives so I was able to connect them to an ubuntu desktop config and pull the data off of that.

Also thank you for the quick responses, it is greatly appreciated!

P.S. I'm thinking outloud here, but could I use a live cd and attach the raid to it, then get my files off that way?

---

### Post by SeijiSensei on 2011-06-16
> **1serveyou said:**
> P.S. I'm thinking outloud here, but could I use a live cd and attach the raid to it, then get my files off that way?

Yes.  You can mount the array from the terminal, then copy the files.  First, let's check the integrity of the filesystem on the array by running "sudo fsck /dev/md0".  Once it completes successfully, run 
```
sudo mkdir /mnt/raid
sudo mount /dev/md0 /mnt/raid
```

Now just copy from /mnt/raid to another device like a USB stick.

I'm assuming that you're using Linux software RAID to create the device.  If you're using a hardware RAID solution, then it will likely appear as some /dev/sdX device, probably /dev/sdb1.  If so, you'd use "/dev/sdb1" instead of "/dev/md0" above.

---

### Post by 1serveyou on 2011-06-16
Thank you for all your help, I must be missing something, as originally I had installed a couple versions of ubuntu server, and can't remember which superblock goes to which. I did those tests and and I kept on getting errors, except one time where it seemed it fixed something. I do have photos if you want to take a look at them. The strange thing is, that when I do -ls is shows everything in my directory, and when I remounted the raid, it shows all of the directory. I'm just not sure why I keep on getting errors. I think I'm going to start trying to copy over the 2tb of data before I crash the system... should be a fun time.

---

### Post by 1serveyou on 2011-06-16
I tried to mount the raid when a live cd, and it said it can't mount the special drive. Also it seems like now the raid doesn't have a super block on it, and when I tried to recover it, I have to keeep on hitting yes over 1k times, and eventually it just goes to a bunch of numbers black/grey all over the screen just moving around. I can mount it when I'm on the server, but since everything is read only I can't create a directory for my usb drive to attach it to. Any ideas?

Update: I tried it again, and sat through the numbers going all over the place, and it went through all of that. I was able to mount, but when I restart I still got the same can't mount / which I thought I had originally fixed and fixed the raid too.

---

### Post by 1serveyou on 2011-06-17
Last night I got to the point that I could edit the fstab, but then after more fiddling with it, I couldn't. The raid doesn't mount on boot, but I can mount it normally and see all the files, but I just can't transfer them to anywhere. When I load Ubuntu Desktop 10.4.2 lts and try out ubuntu, it won't attach the raid. This is so frustrating as I can see all the data, I just can't get it off the system. What would happen if took out the current boot drive and put in a new one? Would that mess up my current software raid?

---

### Post by SeijiSensei on 2011-06-17
> **1serveyou said:**
> The raid doesn't mount on boot, but I can mount it normally and see all the files, but I just can't transfer them to anywhere.

Perhaps the array cannot be assembled.  Is there a /dev/md0 device available?  If so, what does "mdadm --detail /dev/md0" report?  If there's no array started, try assembling it manually with "sudo mdadm --assemble /dev/md0" and see what results.

---

### Post by 1serveyou on 2011-06-17
> **SeijiSensei said:**
> Perhaps the array cannot be assembled.  Is there a /dev/md0 device available?  If so, what does "mdadm --detail /dev/md0" report?  If there's no array started, try assembling it manually with "sudo mdadm --assemble /dev/md0" and see what results.

Would the raid not being assembled cause the read only file system for the whole server? I can create folders on the raid, I just can't move them off the drive, as I can't create a folder to attach my external hard drive to. I'll try those commands when I get home from work. Again, I greatly appreciate your help and time on this, as I had just put a bunch of information I had on computers onto the server that I was going to backup before the power outage.

When I was able to get write access on the fstab, I deleted out that error/remount command, so I'm guessing I screwed myself on that.
[IMG]http://i.imgur.com/ZY4qr.jpg[/IMG]

Here are a couple other commands I tried and their output
[IMG]http://i.imgur.com/SKsqK.jpg[/IMG]
[IMG]http://i.imgur.com/7HGtF.jpg[/IMG]

Here is startup
[IMG]http://i.imgur.com/a7srm.jpg[/IMG]

---

### Post by SeijiSensei on 2011-06-17
Logs are your friend here.  What errors do you find in /var/log/syslog and /var/log/messages when you try to mount the array?

Why is the filesystem type for /dev/md0 listed as "auto" in /etc/fstab?  If you know what type of filesystem it is (ext3 or ext4 is my bet), state that in the /etc/fstab entry.  

Any reason you feel the need to use acl's everywhere?  I've never used them in my 15+ years of running Linux.

The screenshots show the array is assembled and passes the integrity test; it just can't be mounted for some reason.  My bet is the "auto" filesystem type, but that's just a hunch.

All those numbers that flashed on the screen during fsck indicates that there were a lot of errors on the filesystem being checked.  You might want to spend some time browsing lost+found after you get things going again.

---

### Post by 1serveyou on 2011-06-17
> **SeijiSensei said:**
> Logs are your friend here.  What errors do you find in /var/log/syslog and /var/log/messages when you try to mount the array?

Why is the filesystem type for /dev/md0 listed as "auto" in /etc/fstab?  If you know what type of filesystem it is (ext3 or ext4 is my bet), state that in the /etc/fstab entry.  

Any reason you feel the need to use acl's everywhere?  I've never used them in my 15+ years of running Linux.

The screenshots show the array is assembled and passes the integrity test; it just can't be mounted for some reason.  My bet is the "auto" filesystem type, but that's just a hunch.

All those numbers that flashed on the screen during fsck indicates that there were a lot of errors on the filesystem being checked.  You might want to spend some time browsing lost+found after you get things going again.

I'm not sure why I have the /dev/md0 as auto, when I know it should be ext4. The reason for the acl everywhere is just 2 weeks ago I tried using it, and admit-tingly went a little over bored due to not knowing enough. I was trying to make it so I could have different users login to a media server using samba.

I'll run a few tests when I get home in a couple hours and post my results.

---

### Post by 1serveyou on 2011-06-23
Sorry, finally had some more time to work on this, still with no luck. It's strange that I can view my home directory as root without remounting the / partition, but when the server is starting up it says it fails. Also I can still mount the raid and look at files, but when I use a live cd it says it doesn't exist.

Grub
[IMG]http://i.imgur.com/gCzDy.jpg[/IMG]

Startup
[IMG]http://i.imgur.com/MXcqz.jpg[/IMG]

Trying to mount MD0 with live CD
[IMG]http://i.imgur.com/xIYPg.jpg[/IMG]

Mdadm not using live cd
[IMG]http://i.imgur.com/Byhv0.jpg[/IMG]

Logs 1
[IMG]http://i.imgur.com/2xpx6.jpg[/IMG]

Logs 2
[IMG]http://i.imgur.com/p0UZP.jpg[/IMG]

Again I appreciate all of your help!

---

### Post by 1serveyou on 2011-06-23
I've gotten a bit farther, but for some reason when I try to mount the raid, it returns with 

```
sudo mount -t ext4 -o defauls /dev/md0 /WD
mount: special device /dev/md0 does not exist

``````
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/md0 /WD
mount: special device /dev/md0 does not exist

```I don't have anything in the fstab for the drive as I'm not sure how I should type it. Also could it be a rights issue?
 
This is my mdadm.conf


```
  GNU nano 2.2.2          File: /etc/mdadm/mdadm.conf                           

CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=752478c6:06a08d6a:7261255b:f2d644$

# This file was auto-generated on Fri, 24 Jun 2011 00:25:13 +0000
# by mkconf $Id$


```EDITED: Did some more testing

[CODE}
ubuntu@ubuntu:/$ sudo mount -a
mount: mount point UUID=752478c6:06a08d6a:7261255b:f2d64442 does not exist
ubuntu@ubuntu:/$ sudo mdadm --examine --scan
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=752478c6:06a08d6a:7261255b:f2d64442
[/CODE]

With this fstab, I did have it say ext4, but then it would say that line 5 was bad in fstab
[CODE]
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap defaults 0 0

/dev/md0 UUID=752478c6:06a08d6a:7261255b:f2d64442 /home/ubuntu/raid  defaults 0 2

[/CODE}

---

### Post by 1serveyou on 2011-06-24
I'm running out of ideas, I might try to have a friend of mine SSH into the livecd and see if he can fix it. Should their be any problems with doing this?

---

### Post by 1serveyou on 2011-06-26
Good news!! I had a folder named /Data that I had originally mounted the raid on...well remember how I said I could create files and folders on that drive? I ended up creating a folder called /Data/test and mounted my 2tb external hd which ubuntu allowed! I copied over a file to it, tried unmounting it(gave me an error saying it wasn't mounted), but I unplugged the external and put it on my mac, and it saw the few files I put on there. Quick question, it wouldn't let me delete it on the  mac, is that because the hd is formatte NTFS?
 
Cliffs:
Was able to get some information off!
Is it ok to mount a HD in the folder system that my raid is on?
Is NTFS the reason why apple wouldn't let me delete the file off the hd, but allowed me to view it?
Thank you again to everyone that helped in the beginning, it helped a lot.
 
P.S.
Through this process, I've learned a lot more on how ubuntu server works especially on some of the "basic" levels that you kind of pass over when you just reading how to's as it would be impossible for them to go over every little piece. I encourage everyone just starting out to really understand the basics before getting started in the adventures of Ubuntu server, it will save you headaches in the long run. Also... BACK UP your information, no matter how much it costs. If I had just spent a measely $100, I could have saved myself 20+ hours of testing on this, and not have been stressed about it. I will be purchasing an APC UPS with email notification once I do some research on them.

---

