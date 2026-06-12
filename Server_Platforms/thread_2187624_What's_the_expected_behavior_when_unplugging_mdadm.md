---
title: "What's the expected behavior when unplugging mdadm drives?"
date: 2013-11-13
forum: Server Platforms
---

### Post by Roasted on 2013-11-13
I have a test server I'm toying with for learning experiences. I use mdadm in my main server so I figure a safe playground makes the most sense for kicks and giggles with no consequence. Tonight I set up a mirror with two 160gb drives. While the system was running (but of course after the sync) I unplugged one of the drives. I plugged back in and nothing happened. I figured I'd need to remove and re-add to array, so I tried the re-add command, nothing, then tried  fail, remove, etc. Nothing worked. At one point I rebooted and I had both md126 with sdb1 and md127 with sdc1. LOL? No idea how this happened so I figured I'd ask. Any thoughts? Is unplugging a drive not a realistic worst case scenario test when zero data is under risk?

Right now I'm doing a low level format on the two drives and will try this again tomorrow to see if I can duplicate this.

---

### Post by SaturnusDJ on 2013-11-13
Did you try an unplug and write to array afterwards?
It indeed doesn't sound how you want the system to work, but mdadm is not on hardware level.

---

### Post by Roasted on 2013-11-15
So my above post was done pretty much when I was in a sleep coma. That said I've duplicated the same test on my test server. Basically with it running I pulled the power off of a drive, let it sit for 10 minutes (takes mdadm a few minutes to report the missing drive via cat /proc/mdstat it seems), and then tried to re-add sdb1 to the md0 array. Problem was, I couldn't. Like, no really. It gave me NO error whatsoever yet when I ran cat /proc/mdstat, all I saw was sdc1, not sdb1. 

I ended up rebooting my test server. Upon firing up it halted saying /media/storage was missing. Uh, not sure why, because the 2nd drive in the mirror was left untouched and was fstab'd to mount @ /media/storage. But whatever, ignored that error and moved on. Then when I logged back in, it said I had no devices in the array. Uh. LOL? I ran gdisk and created a new partition on each disk (fdisk -l was just showing sdb and sdc existing, but didn't indicate any partitions).

I guess the end goal here is to understand what mdadm is truly doing. So far, I have succeeded approximately 0 times in the experiment of unplugging a live running drive within the RAID array and then re-adding it back to the array. Each time when I try to re-add it, it doesn't fly. Doesn't matter if it's --fail and then --removed, then -add'd or just --re-add'd, etc. No idea. Like I said, just trying to understand this more, but so far the "test" of yanking power from a drive hasn't really been a fantastic one... Any additional thoughts?

---

### Post by SaturnusDJ on 2013-11-15
So now mdadm is reporting the drive as failed? That's good. You should be able to remove it like so:

```
mdadm /dev/md0 --remove detached
```

---

### Post by Roasted on 2013-11-15
> **SaturnusDJ said:**
> So now mdadm is reporting the drive as failed? That's good. You should be able to remove it like so:

```
mdadm /dev/md0 --remove detached
```

aka...

mdadm /dev/md0 --remove /dev/sdb1

Which successfully gets removed. Then I run...

mdadm /dev/md0 --add /dev/sdb1

It returns no error. No complaints. No nothing. But cat /proc/mdstat still reveals /dev/sdc1 in the array, but /dev/sdb1 no where to be found. I can run the --add command a thousand times, it simply doesn't respond to what I am telling it to do. From there, the RAID gets so wonky that I end up having to redo it, which begs the question of how "redundant" the setup is. That's why I began to question if unplugging a drive was a safe way to simulate a failure on a test box with absolutely zero data to spare, but the more I think about it, yes it absolutely is a good test, because who knows what the power supply may run into in terms of problems down the road. I should be able to pull a drive from the array, watch mdadm label it as failed, remove it from the array, then re-add it... but the re-adding part is not cooperating...

---

### Post by cjhabs on 2013-11-15
When I was playing around with this recently I did the following which worked for me:
sudo mdadm &#8211;manage /dev/md0 --fail /dev/sdb1 
sudo mdadm &#8211;manage /dev/md0 &#8211;remove /dev/sdb1
Add a drive back to the mirror &#8211; it needs to be partitioned and formatted first
sudo mdadm &#8211;manage /dev/md0 --add /dev/sdb1

---

### Post by Roasted on 2013-11-15
Er, you need to partition and format the drive before adding it to the array? But if it was partitioned and formatted prior, wouldn't it still retain that table structure? Also, in your testing when you outlined what worked for you, did you ever unplug a drive, or just simply pass the fail command to make it appear as if it failed?

I don't want to mess around with making the system think the drive failed. I want to yank the drive and simulate an actual failure. It's adding this "failed" drive back that I'm striking out at... That's why I'm doing this on a spare box with two 160 GB Seagates that I can afford to lose in the name of learning something new. :D

---

### Post by SaturnusDJ on 2013-11-15
--remove detached is a special command to remove a device that actually isn't attached anymore but somehow still a (failed) member

Try
```

partprobe

```
Or rescan the interface bus to where the data disk is connected.

---

