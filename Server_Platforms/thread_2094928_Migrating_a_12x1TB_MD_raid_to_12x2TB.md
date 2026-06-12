---
title: "Migrating a 12x1TB MD raid to 12x2TB"
date: 2012-12-15
forum: Server Platforms
---

### Post by Xianath on 2012-12-15
I have a 12x1TB RAID6 md array. The disks are four years old already and I want to swap them for 2TB ones before disaster strikes. The obvious approach would be to replace them one by one, rebuilding the array each time, and finally expanding it. This, however, constitutes 13 full rebuilds. Isn't this risky given the disks' age? They are not RAID certified, just regular desktop HDDs (Samsung SpinPoint F1, to be precise.)

I was thinking about an alternative approach but I'm not sure how well it will work. Basically, build an entirely new system out of the 2TB disks, create partitions (4KB aligned and everything) of the same size as those on the 1TB disks, then hook the 1TB disks one by one to an eSATA or USB3 box and dd the entire partition, magic block and everything, onto the corresponding disk in the new system, then assemble an array from those partitions, and finally expand it. Would this work given the different drive geometry?

It's been quite a while since I last did this, so any tips will be much appreciated.

---

### Post by grunge09 on 2012-12-15
Its better to build the new pc with the 2tb drives, with the full size of the drives in the array, then copy the data over (12TB will take days to copy) but its the safe bet.  

You can get a rj-45 crossover cable to copy your data, or a cheap 30 dollar gigabit router.  

1 recently DD'ed a 1tb drive to a 2tb drive.  Took 11 hours after DD was started and the drives were in the same system.  Granted my 1tb was 7200rpm and the 2tb was 5900 rpm.  But still I am just sayin.

---

### Post by Xianath on 2012-12-15
Yes, that would be the perfect solution, but I see now that I didn't explain my plan well enough. I don't want to build a whole new PC (at least for now.) Rather, I'll take the drives out of this one and replace them with bigger ones. I'll be retiring the 1TB drives and there's no point in building a whole new system just for migrating data over. Hopefully this puts my dilemma in perspective.

Time is not much of an issue, but the data on that array is. If I manage to migrate one disk a day without a significant risk to data, I'll be perfectly fine.

---

### Post by darkod on 2012-12-15
I think making small partitions just so you can use them with dd is unnecessary risk. You will still have to expand each partition later, otherwise mdadm will not be able to use the full 2TB disk.

I'm not sure what would be the best way in this situation. You can also do this:
Instead of buying 12x2TB disks now, why don't you wait and swap only failed disks (if and when it happens). If you don't need the extra storage, replacing disks in such a big array just to swap them with new ones seems excessive. It might get you into more trouble than doing you good.
RAID6 gives you two disk redundancy. Just run it until a disk fails and replace it with a new one when it does.

---

### Post by Xianath on 2012-12-15
I kinda need the space now, I'm afraid... Also, these drives are all from the same batch (minus one that failed and was replaced) so they are much more likely to start failing within a relatively short time frame. Last time I had a drive failure was right around a big holiday break and I had to wait for ten days for a replacement. Not a good place to be, to be honest.

My biggest concern really is if I can just dd a partition from a 1TB drive to a 2TB drive and still retain all the md and dm metadata so I can reconstruct the array and logical volumes. Maybe I'll just give it a go and if that doesn't work, I'll take an alternative route, but if anyone has a definitive answer to this question, I'll appreciate it.

---

### Post by darkod on 2012-12-15
No, I don't have an answer about the dd option, except that that command is little bit "weird". I remember dd-ing a 4GB CF card onto 8GB CF card and after that the useful space was only 4GB, not 8GB.
The idea is that if it creates 1TB partitions on your 2TB disks, it doesn't help much since you would need to do partition expanding and that is a risk for the data always.

See if google turns up something about imaging/copying a disk member of mdadm.

---

