---
title: "New Question for Dell Mini 9 with Ubuntu"
date: 2009-02-02
forum: The Cafe
---

### Post by billyjack on 2009-02-02
I am new to Ubuntu.. I purchased this mini 9 with Ubuntu and wondering why it shows I have 6.8 total gb and used 5.3gb available 1.5gb.. when I have nothing on this computer but Ubuntu.. nothing added.

Does Ubuntu take up that much?  Also is it necessary to defrag this computer and if so how? and also disk cleanup?

Thanks
George

---

### Post by OutOfReach on 2009-02-02
Ubuntu should take up about 4gb, but maybe with all the things Dell added it comes up as 5gb.

No you don't need to defrag Ubuntu, or any Linux distribution for that matter.

---

### Post by CrazyDesi on 2009-02-02
Nope it just takes up that much space.  One of the main reasons that I went for the Mini 12.

---

### Post by Sealbhach on 2009-02-02
What disk size did you order? Does it have a Disk Usage Analyser that shows you what's taking up space? 

The standard Ubuntu contains this and shows a nice clear picture of what's using up your space (see attached image).

---

### Post by billyjack on 2009-02-02
> **CrazyDesi said:**
> Nope it just takes up that much space.  One of the main reasons that I went for the Mini 12.


Thanks,

Well I bought an outside drive and will use that if I need to download anything.. but I surely thought I had enough memory and space to do what I need to do.  

910 Intel Atom Processor 6ghz 
1gb ddr2 533mhz 
4gb solid state drive

---

### Post by Bölvaður on 2009-02-02
I guess you could remove bunch of packages, but you may want to get more familiar with the system before doing any surgery

---

### Post by henryw@cablespeed.com on 2009-05-09
What has filled my 4GB of Memory? I've had my Dell 910 w/ the basic 4GB of memory since December. and I have been diligent in not adding anything to the memory - at least not intentionally. I have pulled off most of the unused applications provided. Nevertheless, my memory is now at 90+ %, the 910 is running very slow, and I am in a quandry. I have downloaded the Ubuntu updates, when notified to do so. Is it the updates that have added 1.5GB of data? If so, how can I deal with this? I was confident that if I was careful not to store anything additional on the 4GB internal emory, I would always be OK. Now I can't use the Mini! Any ideas?

---

### Post by mikewhatever on 2009-05-09
Memory usually means RAM, which isn't the same as disk space. It's doubtful a Dell mini would have 4 GB of RAM, so I suppose it's safe to assume you are talking about the disk space. What's the output of df -h?

To the OP: Why is this thread in the Comunity Cafe?

> **billyjack said:**
> Thanks,

Well I bought an outside drive and will use that if I need to download anything.. but I surely thought I had enough memory and space to do what I need to do.  

910 Intel Atom Processor 6ghz 
1gb ddr2 533mhz 
4gb solid state drive

From what I hear, Dell has more then just Ubuntu partition there. There should be at least a swap and a recovery partition, all taking up space. You can verify that by the **sudo fdisk -l** command.
And by the way, that CPU is outstanding.:lolflag:

---

### Post by jonian_g on 2009-05-09
Ubuntu fresh install takes 2-2.5 gigs. My Eeepc has a 4gigs ssd, I have 1.5 gigs free. So all that size is not taken by ubuntu.

If you have installed various applications and then removed them, you will not get all your disk space back because the installation files are kept in cache in case you want to use them again.

To clear the cache go to System>Settings>Synaptic Package Manager. Then go to Settings>Preferences and then the Files tab. Click Delete files from cache. Also you might choose the filed to be deleted after succesfull installation.

---

### Post by henryw@cablespeed.com on 2009-05-09
Thanks, all, for the help with my question. Of course, I meant the 4GB of "memory" (storage space) on the internal solid state drive. Anyway, I did delete the cache as instructed and that has helped.

---

### Post by mxboy15u on 2009-05-09
> **henryw@cablespeed.com said:**
> Thanks, all, for the help with my question. Of course, I meant the 4GB of "memory" (storage space) on the internal solid state drive. Anyway, I did delete the cache as instructed and that has helped.

Back when I had a EEE 2GB surf I would run out of drive space constantly. I added an 8GB SD card and that helped, but it still was too little space for me. I have been looking at SSD drives again and would not get under a 16GB now I think.

---

