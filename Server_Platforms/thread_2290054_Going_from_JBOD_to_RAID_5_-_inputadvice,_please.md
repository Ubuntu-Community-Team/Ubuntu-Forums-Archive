---
title: "Going from JBOD to RAID 5 - input/advice, please?"
date: 2015-08-08
forum: Server Platforms
---

### Post by Donny Bahama on 2015-08-08
My media server has been up and running for quite a while now. Current JBOD configuration is: 
2 x 3TB HDD
4 x 1TB HDD
1 x 1.5TB HDD
1 x 500GB HDD
1 x 320GB HDD (system drive)

I've recently purchased 2 new 3TB drives (I'll call them drives 3 and 4) and I was thinking I would create a (software) RAID 5 array with drives 3 and 4, move everything from drive 1 to the new array, then add drive 1 to the array. (Then repeat that with drive 2.) This 4 drive array would hold my video library, and initially, I think there would be enough free space to move over everything (my music library) from my 4 x 1TB drives so I could create a second RAID 5 array from the four 1TB drives (then move my music library back over to the second array).

My questions:
[LIST=1]
[*]Does this seem like a reasonably good plan, in general? Or am I making a big mistake?
[*]Can anyone point me to a nice, noob-friendly guide for setting up/working with software RAID 5 arrays?
[*]Is it OK to have more than one RAID array on a server?
[*]Will it require a lot of horsepower to manage two software arrays? I've intentionally gone low-power because the media server is on 24/7/365.
[*]The server currently has 2GB RAM. Will I need more if I'm going to have two software arrays?
[*]Would there be any advantage to replacing the system drive with an SSD? I have one available and the server is offline/disassembled at the moment...
[*]Are there cfg options for the software arrays for spinning down the disks when they're idle? If so, is this advisable? Seems like it might be good for my electric bill, and perhaps the longevity of the drives as well.
[/LIST]

---

### Post by cj13579 on 2015-08-09
Hey, I looked into to doing something similar a while back (though at the moment I still haven't set everything up and am still running JBOD). As part of my research for that I read an article when I was comparing the RAID options and it drove me away from RAID 5 ([link]("http://www.cyberciti.biz/tips/raid5-vs-raid-10-safety-performance.html")). 

Appreciate that this doesn't answer the specifics of what you have asked above but it may the questions become different once you have read the article :)

---

### Post by tgalati4 on 2015-08-09
Well, if you are interested in power-saving and spinning down disks, then RAID is not really an option.  RAID and "Green" drives are not a good combination.  If you want to save power, just keep JBOD.  If you need to group disks together for management purposes, then consider LVM, but RAID and spinning down is not compatible.

Now, you can configure RAID5 or really 6 or higher for the size pools you are considering and use Wake-on-LAN (WoL) to put your server to sleep and put WoL widgets on your phone and on your laptops to wake the server when you want to stream.  

RAID is not a backup strategy.  It can improve data availability, but it can also cause headaches when it fails and then fails to rebuild properly.  If you want to reduce bit-rot from media files then consider ZFS.

Why do you think RAID5 is appropriate for a home server?

---

