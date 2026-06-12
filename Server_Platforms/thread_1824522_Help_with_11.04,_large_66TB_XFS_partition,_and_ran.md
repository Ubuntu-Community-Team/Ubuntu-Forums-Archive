---
title: "Help with 11.04, large 66TB XFS partition, and random file loss!"
date: 2011-08-13
forum: Server Platforms
---

### Post by faroutliving on 2011-08-13
I'm helping to configure a server about 3000 miles away. The hardware is  basically 2 Xeons, 48GB of ram, and an Areca 1880 raid card running a  24 drive raid 6 array giving a total of 66TB of storage. It is going to  be used for video processing and related services. Initially I sent them  a USB thumb drive with a self installing version of 11.04 with SSH  access preconfigured so I can finish installation from here. Sending the  thumb drive was way cheaper than sending me :-)

The first hangup was ext4 can't be installed on a 66TB partition. So I  changed that to xfs. It seems to work well, except for one great bit  problem. The folks where this is setup seems to have a power problem. An  issue that needs to be addressed for sure, but the damage caused is  beyond what I would except. The first time this happened, I had just  finished installing and configuring virtualmin. The power loss caused  several virtualmin files to be lost (they appeared as 0 length) and a  few /etc files like shadow, groups, gshadow and even passwd. Fortunately  passwd and one of the others simple reverted to an older version.

Since I didn't know when the power went out (it wouldn't restart at the  time on its own) I just chalked up the loss as something that occurred  right after I had made the changes and the files must not have been  written out yet. I simply (?) rebuilt the lost /etc files, patched up  enough of virtualmin's files so I could get it to uninstall and  reinstall and went on.

However, Thursday night I added gitolite support, verified everything  was running well and called it a night. Friday morning about 9:30 the  server got rebooted (this time was human error) and still lost files!!! I  would have expected the cache to have been cleared by then, but worse  yet not all of these lost files had been edited by me at all since the  previous reboot so should not have been open/modified.

The restart log only showed this useless tidbit:

Aug 12 09:17:09 mdv kernel: [   11.693488] XFS mounting filesystem sda2
Aug 12 09:17:09 mdv kernel: [   12.068202] Starting XFS recovery on filesystem: sda2 (logdev: internal)
Aug 12 09:17:09 mdv kernel: [   16.700103] Ending XFS recovery on  filesystem: sda2 (logdev: internal)<30>udev[430]: starting version  167

I can't unmount this partition because it is the only partition, so I can't run the xfs recovery.

So my questions that you, the collective knowledge that is the great Ubuntu mindspace, might be able to help me with are:


1) How can I either repair, or at least pin point, what has been lost?

   (I have 3 - 3TB drives in a half complete JBOD that I can mount, so  maybe some way to install a rescue OS to one of those or? I would have  to stop the raid from booting and I'm pretty sure it would have  priority. All must be done from SSH of course.)


2) How do I prevent this from happening in the future? I understand  loosing a file being written, but this goes way beyond that! It seems we  have done everything I know of to improve handling of such an error,  but instead find it worse than my much abused home install where I  reset/reboot/crash all the time and I have no raid or fancy file system.

Thanks!

Deron

---

### Post by rubylaser on 2011-08-14
First, it sucks that you're going through this. Secondly, and XFS check on a filesystem this big is going to take a while.

Other than trying to get someone on that end to mount the Livecd for you and setup ssh, I can't see how you'll be able to repair this remotely without some help on the other end. Also, I know tons of people use XFS in production with large filesystems, but I've had numerous corruption issues with it in the past.  

Personally, I migrated our large data storage server (48TB) at work to Solaris 11 Express and had great luck with ZFS.

---

### Post by Havis on 2011-08-14
I would strongly recomend JFS filesystem, and don't even bother with XFS.
I had same problems with XFS 2-3years ago...  after reset some files had zero size etc etc...

BTW, check your install with debsums (debsums -c), to see if there are no other corrupted files

---

### Post by faroutliving on 2011-08-14
Thanks to both of you for your advice (and sympathy). I agree that moving from xfs is the prudent thing to do. However, I think I might go back to ext4. I'm in no mood right now for another "non-standard" file system. I can live with 4 partitions for now. If they ever get e2fsprogs to support >16tb partitions then I can always merging/resizing if need be. I'll do a little research on your proposed file systems/os, but to be honest I can find plenty of folks saying nice things about xfs. I just don't happen to be one right now ;-)

Ok, I checked and the boot USB happens to be still attached. I rebooted the system but it came back up off the RAID array so I can presume that the boot priority is set to the HDD first when available.

Other than waiting until Tuesday when someone will be available to rearrange the boot priority, any way to "restart" from the USB? Maybe even remove the boot flags or ?? from the Raid array? I can't just trash /boot since I don't want the system to hang on reboot. Then I really am stuck till Tuesday.

Any suggestions?

Thanks again,

Deron

---

### Post by arrrghhh on 2011-08-15
Well, the obvious suggestion would be a DRAC, iLO, etc... some sort of remote access controller that's separate of the OS.  

I assume if you're asking, this server doesn't have it, or its not configured... Not sure how else what you're trying to do would be achieved...

---

### Post by Havis on 2011-08-15
Btw, I googled a little bit and I found that you are not the only one with this problem:
[http://oss.sgi.com/archives/xfs/2011-06/msg00452.html](http://oss.sgi.com/archives/xfs/2011-06/msg00452.html)

---

### Post by dtfinch on 2011-08-15
XFS's delayed allocation causes a lot of this. Ext4 does it too. If a program writes to a file, but doesn't call sync() or fsync(), it'll keep the data in memory for a while before writing it to disk. I think the delay is 30 seconds for XFS and 2 minutes for ext4. It's a bad assumption for them to assume all apps will sync after important writes, since on previous filesystems that led to horrendous slowdowns, and ext3 didn't have the same risk of loss, but there's no arguing with them. And I don't know why they pick such long delays by default, except to expose apps that don't sync.

If you wrote to the files less than a minute before the power loss, I'd assume delayed allocation (and failure to sync after writing) was to blame. If it was longer, it's probably something else.

---

### Post by faroutliving on 2011-08-15
> **dtfinch said:**
> XFS's delayed allocation causes a lot of this. Ext4 does it too. If a program writes to a file, but doesn't call sync() or fsync(), it'll keep the data in memory for a while before writing it to disk. I think the delay is 30 seconds for XFS and 2 minutes for ext4. It's a bad assumption for them to assume all apps will sync after important writes, since on previous filesystems that led to horrendous slowdowns, and ext3 didn't have the same risk of loss, but there's no arguing with them. And I don't know why they pick such long delays by default, except to expose apps that don't sync.

If you wrote to the files less than a minute before the power loss, I'd assume delayed allocation (and failure to sync after writing) was to blame. If it was longer, it's probably something else.

I'm aware of those write back delays. However, I know for a fact a couple files had been changed more than 9 hours before the loss, and a few had not been edited since a safe restart.

Either way, it is unacceptable. I see someone was running a cron process ever second or so to flush the cache. That just seems crazy, and doesn't really fix the problem if the crash occurs within those few seconds. No one expects an actively open file to survive, but loosing (seemingly) random files is the last straw for me!

I wish I could boot from this USB and move on, but I can wait until tomorrow if I have to.

Thanks for the input.

Deron

---

### Post by dtfinch on 2011-08-15
Does the raid card have a battery? If not, and the card's own write cache is enabled, that could also lead to corruption in a power outage. Though it's a long shot because it's disabled by default if there's no battery detected.

---

### Post by rubylaser on 2011-08-15
> **dtfinch said:**
> Does the raid card have a battery? If not, and the card's own write cache is enabled, that could also lead to corruption in a power outage. Though it's a long shot because it's disabled by default if there's no battery detected.

Oh, yeah the 1880 comes with a minimum of 512MB onboard cache, or the high end version allows for up to 4GB of cache.  The battery does come separately, but I can't see (hopefully) someone buying a $600 - $1,200 (depending on model) RAID card, and not buying the BBU with it.

---

