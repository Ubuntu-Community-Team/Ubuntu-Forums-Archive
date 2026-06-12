---
title: "Ubuntu Hardy  not the greatest experince"
date: 2008-04-25
forum: Testimonials &amp; Experiences
---

### Post by revelationman on 2008-04-25
After I installed Hardy I started to experince freezing this cause me to do on average 4 hard reboots a day. If you want to your hard drive to last this is something you should not do. 

I have looked everywhere for a solution tried everything many feel it is the broadcom driver. 

The postiive experince was faster boot times which was great gusty was terrible for booting.

Sadly I cannot hard boot all the time and there is really no solutions that can be found here .

I really love this system love the software that comes with it so it was regret that I need to go back to XP till this issue is sorted. 

Another thing was that Firefox Beta 5 is not compatible with online banking. 

So is this a negative experince I guess you can say that do I blame Ubuntu I am not sure. I do feel there is certain things that need to be address for them to be a serious threat to Microsoft. I do feel they can be that is how strong I do feel about Ubuntu but there is much work to do. 

I do hope there is some suggestions on what to do I really do not like Windows to be honest. But you have to go what works and I am sure all you can appreciate that.

:(

---

### Post by ukripper on 2008-04-25
> **revelationman said:**
> After I installed Hardy I started to experince freezing this cause me to do on average 4 hard reboots a day. If you want to your hard drive to last this is something you should not do. 

I have looked everywhere for a solution tried everything many feel it is the broadcom driver. 

The postiive experince was faster boot times which was great gusty was terrible for booting.

Sadly I cannot hard boot all the time and there is really no solutions that can be found here .

I really love this system love the software that comes with it so it was regret that I need to go back to XP till this issue is sorted. 

Another thing was that Firefox Beta 5 is not compatible with online banking. 

So is this a negative experince I guess you can say that do I blame Ubuntu I am not sure. I do feel there is certain things that need to be address for them to be a serious threat to Microsoft. I do feel they can be that is how strong I do feel about Ubuntu but there is much work to do. 

I do hope there is some suggestions on what to do I really do not like Windows to be honest. But you have to go what works and I am sure all you can appreciate that.

:(

Boot into live cd and check your file system first using following command in terminal, below will check for errors and attempt to fix them. 

```
sudo fsck /dev/sda*
``` replace "sda*" with your ubuntu partition e.g /dev/sda1 or dev/sda7 .

To check wot partition your ubuntu is mounted on do following :

```
sudo fdisk -l
``` "-l" is 'ell' not one

---

