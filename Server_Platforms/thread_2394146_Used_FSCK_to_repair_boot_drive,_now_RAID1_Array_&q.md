---
title: "Used FSCK to repair boot drive, now RAID1 Array &quot;Inactive&quot;"
date: 2018-06-09
forum: Server Platforms
---

### Post by fensty on 2018-06-09
Hello,

Long time reader, first time poster.  I'll do my best to post correctly, go easy on me if I fail, please?

_**TL;DR: **_ Resolved a booting-to-Busy Box (initramfs) issue with FSCK /dev/sda, but found my RAID1 array on /dev/md0 (2 drives) was INACTIVE.  Found an online help page that described how to verify things, stop the array, then restart and add in missing drives, then sit back and wait for it to rebuild, etc.  However when I did the MDADM /S /dev/md0 and then turned around to restart the array, it came back with only 1 of 2 drives (as expected) but on mounting that and looking, the array appeared as it did in Oct. 2016 - nothing I added since showed up.  I freaked, shut down array, shut down machine, unplugged drives then came here to seek help.


_**More detail:  **_

After fixing the 'boot drive only takes to (initiramfs) mini environment' issue on /dev/sda, I rebooted to find my RAID1 array missing.  The gnome "Disks" util in LXDesk shows the drives (/dev/sdb1 and /dev/sdc) and also the RAID array but not mountable.  A detailed scan shows this:

[COLOR=#333333][FONT=&quot]sudo mdadm --detail --scan -v /dev/md0 [/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]INACTIVE-ARRAY /dev/md0 num-devices=1 metadata=1.2 name=Carn-Dum:0 UUID= (the correct UUID for the array)[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]devices=/dev/sdb1[/FONT][/COLOR]

The help page I found for this is here:   [http://fibrevillage.com/storage/676-how-to-fix-linux-mdadm-inactive-array](http://fibrevillage.com/storage/676-how-to-fix-linux-mdadm-inactive-array)

Essentially it talked me through various forms of verifying what was there, then how to stop the array with MDADM /S /dev/md0, then how to restart which it did with the "1 of 2 drives" note.  

I then mounted /dev/md0 and FREAKED when I saw it as it appeared on Oct. 2016 which was shortly after I set it up.  Nothing added since then was present anywhere or seemed to show up anywhere in LXDesk or command prompt.

I shut off the array again, shut down the system, pulled the SATA cables off both drives "just in case" so I don't screw anything up, and came here to seek help.
 
I suspect I'm being overly timid and cautious, and if I'd just gone ahead and re-added the missing drive and started the rebuild process, it would have rebuilt with the 'correct' file table perfectly fine and without drama.  But as I'm still only halfway between 'noob' and 'knows just enough to get in trouble' I felt it was best to be careful and seek assistance.

So, here I am. Please tell me I should just re-add this missing drive and then re-create the array and it'll be fine.  But if that's not possible because that's not true, if anyone can tell me what to do to save the data that I'm sure is on there but can't access, I would be forever grateful...

Thanks in advance!
JD

---

### Post by fensty on 2018-06-12
It's probably 'verboten' to bump a post back to the top like this, I would have deleted it and re-posted it shorter and to the point better, but I can't see how to do that.

I'm really desperate here, my media server is offline due to this issue, I've done due diligence looking anywhere for this particular issue and found nothing.

Shortest way I can restate the problem:  After fixing a boot issue on /dev/sda, my 2-drive 5TB RAID1 on /dev/md0 was showing inactive.  I followed a detailed help file to stop the array and attempt to rebuild.  It was /dev/sdb and /dev/sdc1 and once I added /dev/sdb back in, I started it and as expected, had 1 of 2 drives in the array.  I mounted to take a look - and found the filesystem as it appeared back in October 2016 when I first built the array and copied the 3TB of files into it from the array it was replacing.  I panicked, shut it all down, unplugged both drives, came looking for help.

Did I just go off-script on the help file, and if I had just followed directions, added the 2nd drive and let it rebuild, would it have been fine?  Or is something worse happening?

I'm honestly terrified of doing anything that might cost me 5TB of near-impossible to replace files without some expert advice.

Pardon my 'bump' please, and if anyone can help, I'll do whatever penance is required....
JD

---

### Post by howefield on 2018-06-13
> **fensty said:**
> It's probably 'verboten'

Not at all, please feel free to bump your thread back to the top once or twice a day if no response, every 12 hours or so. Oftentimes it is all it takes to attract the right persons attention.

Also might be better to move to server platforms for a better subject fit, which I have done.

---

### Post by CharlesA on 2018-06-13
I've had an issue similar to that when I had a drive fail on me, but your issue sounds different. Maybe this will help? [https://anders.com/cms/411/Linux/Software.RAID/inactive/mdadm](https://anders.com/cms/411/Linux/Software.RAID/inactive/mdadm)

What you can do is only connect one drive and try to activate it and see what happens.

Do you have a backup of the data on this drive array?

---

### Post by darkod on 2018-06-13
Are the raid member /dev/sdb (which is a drive) and /dev/sdc1 (which is a partition) or you made a typo?

Anyway, if the OS boots now, I would start by checking the superblock info (the arrays doesn't need to be running for that). Not knowing your raid members, I have to assume, lets say it's sdb1 and sdc1:
```
sudo mdadm -E /dev/sd[bc]1
```

That command can pick up both but only under my assumption. You can run the command twice, once for each raid member, like:
```
sudo mdadm -E /dev/sdb
sudo mdadm -E /dev/sdc1
```

Post the output here in CODE tags to keep formatting, and we will know little more...

---

