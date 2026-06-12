---
title: "losing disks in a RAID level 5?"
date: 2007-03-16
forum: Server Platforms
---

### Post by gradedcheese on 2007-03-16
Not specific to Ubuntu, but I hope you guys don't mind: I need to ask about failing drives in a RAID-5 array.

I have a server (Dell PowerEdge 1500SC) with six 18GB disks arranged in a RAID-5 with an approximately 64GB logical disk.  This morning it started beeping so I hooked up a display and found that the RAID controller was reporting problems.  In the RAID BIOS, it shows disks 0 and 2 as failed.  I happen to have a similar spare server that hasn't been set up yet, so I grabbed two disks out of its array (they are the same type and size) and swapped them in place of 0 and 2.  I then tried the 'rebuild' tool in the BIOS but it always fails.

So, my question: am I totally screwed?  Is there anything I can do to recover the data, given four working disks?  I really have no idea how to troubleshoot this stuff and only a vague understanding of how it works :(

---

### Post by moopere on 2007-03-17
> **gradedcheese said:**
> Not specific to Ubuntu, but I hope you guys don't mind: I need to ask about failing drives in a RAID-5 array.

I have a server (Dell PowerEdge 1500SC) with six 18GB disks arranged in a RAID-5 with an approximately 64GB logical disk.  This morning it started beeping so I hooked up a display and found that the RAID controller was reporting problems.  In the RAID BIOS, it shows disks 0 and 2 as failed.  I happen to have a similar spare server that hasn't been set up yet, so I grabbed two disks out of its array (they are the same type and size) and swapped them in place of 0 and 2.  I then tried the 'rebuild' tool in the BIOS but it always fails.

So, my question: am I totally screwed?  Is there anything I can do to recover the data, given four working disks?  I really have no idea how to troubleshoot this stuff and only a vague understanding of how it works :(

I think you are in for a bad time.  Its my understanding that RAID5 can only recover from a single disk failure at a time.  

Having said that, how unlucky would you have to be to lose 2 disks at exactly the same time?  Smells fishy, noone got in there and pulled out the disks did they?  If you pull a disk its marked as failed by the array, if you then put in back in, and pull another one its then marked as failed and your array goes down.

Unless you have a nominated hot spare in your array normally the controller won't rebuild the array on an unknown disk, nor one thats been marked as failed.

Cheers,
Craig

---

### Post by gradedcheese on 2007-03-17
I have good news, though the story is weird: I poked around the options in the RAID BIOS and found that although disks 0 and 2 are marked 'failed', the BIOS tells me they have "0 errors".  I then found the "bring disk online" option (which warns me not to bring failed disks online) and figured I have little to lose.  I brought disks 0 and 2 online and rebooted.  The file systems got mounted just fine, Ubuntu booted, and I quickly plugged in a big USB hard disk and started copying everything like crazy.  

'not sure what to think: I agree that it's odd that two disks would actually fail before the controller stops the server to begin with.  Could it be a mistake by the controller?  The whole thing seems to be up and running just fine.

Any suggestions for what to do next?  Should I trust these drives (especially 0 and 2)?  I was thinking of upgrading Ubuntu on this server anyhow, so perhaps this would be a good time to rebuild the RAID and clean-install the OS.

---

