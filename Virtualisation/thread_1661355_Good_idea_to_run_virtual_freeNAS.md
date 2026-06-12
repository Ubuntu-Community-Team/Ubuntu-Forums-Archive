---
title: "Good idea to run virtual freeNAS?"
date: 2011-01-06
forum: Virtualisation
---

### Post by piergen on 2011-01-06
For a couple of years I have run xubuntu. Recently I got a NAS and have had nothing but problems. Finally got things working and for about 1-1.2 TB of data transfer via netgear GB switch I can look at 40+ hours of transfer time. After 5 hours of transferring I see 11% is completed.......did someone say time consuming ?

I have had vmware and a few virtual machines running in the past and that have been smooth.
So now I am thinking rather then spending time fiddeling with resolving bad network speed or transfer time I might as well just run a guest OS like freeNAS inside the xubuntu box.

I have allready a raid running inside xubuntu cause I work alot with large video files and hi-res photos etc. I recently discovered that alltough I get extra speed from this raid 0 setup I also pay a primium when it comes to risk as I can not have any disks fail or even hardware failure might cause me to loose data.

I do have a dedicated 4 port RAID  controller card which I have not yet installed.
Would it be smart to use 4 x nTB drives mounted into the xubuntu box and connect them to the raid card? Then I can run raid 0+1 that will give me speed but also fail tolerance of -1 disk. 

Because the virtual nas will be inside the box rather then on the network I will gain maximum speed for file transfer? Then I can run some sort of script to make the virtual nas syncronise to the slow nas I allrady have. That way the cheap nas can run 24/7 with less powerconsumption and I can access all files from laptop, mediaplayer and what not and always have syncronized data.

So what do you think people, am I way off here or will this give me fast backup to virtual nas without the need to optimize cabling, switches and network traffic? Or does this not make any sense at all? Maybe I am overthinking the matter cause I am frustrated with network speed and a stardom NAS that is slow.

---

