---
title: "Clarifcation of naming convention for future Ubuntu"
date: 2015-08-04
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2015-08-04
[http://www.olli-ries.com/t-242d/](http://www.olli-ries.com/t-242d/)

Ubuntu Desktop Next? No. Snappy Ubuntu Desktop Next? No. Snappy Ubuntu Personal? No. Ubuntu Personal? Yes! The blog has a bit of a road map but based on my recent update of what was yesterday called Snappy Ubuntu Desktop Next I am not expecting too much to be achieved by 15.10 release date. At the moment it does not have an ISO image.

Regards.

---

### Post by ventrical on 2015-08-05
As I read it we will still have default unity7 for 16.04 and unity8+ mir as an alternate which I figured was the logical step. Since it's inception it has been very difficult to get a stable working unity8+mir desktop on a desktop PC , especially more middle of the road hardware.

---

### Post by grahammechanical on 2015-08-05
After making that post I listened to the Ubuntu On Air session that I had missed earlier in the day. Ollie Reis was there. From what he was saying and my understanding of it (So I could easily be wrong) I think that Canonical has scaled down its ambition a little bit regarding convergence.

Ollie Reis made it clear that every version of Ubuntu is built from the archives and they have deb packages and there is no plan to change that. We already know that 16.04 will be a "traditional" deb packaged version and it will be around for 5 years. But from what Ollie was saying I am getting the idea that Ubuntu personal will be a desktop version of Ubuntu that will be as "locked down" (to use a phrase) as the Ubuntu phone is. And it is Ubuntu personal that will be the converged code base installed on phones, tablets and desktops.

That will not be to everyone's liking (the locking down bit) but I think that it will be beneficial to those who want an OS and do not need to meddle with it. I can see OEMs liking a version of Ubuntu that cannot be broken by the purchaser. The meddlers will have to install 16.04 "traditional." I think we will not know for another year if there will be a development version of 16.10 "traditional" or just a development version 16.04.1 "traditional."

As you and I have found out the personal image has transactional updates. I do not think that Ubuntu personal will have version numbers. Just Over the Air updates.

Regards

---

### Post by ventrical on 2015-08-05
> **grahammechanical said:**
> After making that post I listened to the Ubuntu On Air session that I had missed earlier in the day. Ollie Reis was there. From what he was saying and my understanding of it (So I could easily be wrong) I think that Canonical has scaled down its ambition a little bit regarding convergence.

I think this is a wise path to take.  Why fiddle, tinker and hack something that is known to be rock solid. I mean .. to say..  that  if they book another traditional LTS version (as in 16.04) then it would be good for newer, current and  ubuntu converts to come. At this stage of the game the 'snappy' frame has a certain exclusivity that would bar a lot of noobs .. not deliberately .. but I would find it a hard sell for some of the converts I am working with. So you can see where my stress comes from. An O also work with noob elder converts  - some just starting to get a handle on trusty-unity7.

> 
Ollie Reis made it clear that every version of Ubuntu is built from the archives and they have deb packages and there is no plan to change that. We already know that 16.04 will be a "traditional" deb packaged version and it will be around for 5 years. But from what Ollie was saying I am getting the idea that Ubuntu personal will be a desktop version of Ubuntu that will be as "locked down" (to use a phrase) as the Ubuntu phone is. And it is Ubuntu personal that will be the converged code base installed on phones, tablets and desktops.

 I have 2 RCA 7 Voyager tablets that runs an ubuntu kernel and is almost impossible to install one of the ubuntu-touch images on. It is superlocked down. 

> 
That will not be to everyone's liking (the locking down bit) but I think that it will be beneficial to those who want an OS and do not need to meddle with it. I can see OEMs liking a version of Ubuntu that cannot be broken by the purchaser. The meddlers will have to install 16.04 "traditional." I think we will not know for another year if there will be a development version of 16.10 "traditional" or just a development version 16.04.1 "traditional."

As you and I have found out the personal image has transactional updates. I do not think that Ubuntu personal will have version numbers. Just Over the Air updates.

Regards

It will be interesting to see what happens in September. If we can't get a working gnome-terminal from the app store then as a distribution, unity8+mir will not be intriguing to hackers and testers at all. Of course a lot of testers don't like cooked and canned testing routines but I am always willing to  contribute what I can.

Thanks for the new news:)

Regards..

---

### Post by grahammechanical on 2015-08-05
There is one subject that I have my doubts about. Will Ubuntu Personal have an ISO image? I am beginning to think that personal_x86.img may remain the kind of image used by OEMs to flash devices. Perhaps laptops even.

I am trying to workout a way of installing personal_x86.img on to a hard disk partition. Discs>Image Restore has no option for partitions. Just complete disks. The dd command might do it but I need to study that command. Questions as yet unanswered by me.

1) Will Grub from another install detect the kernel in a restored personal_x86.img?
2) Can the target partition be expanded to increase the space available or are we stuck with the partition layout that comes with a restored personal_x86.img?
3) Can I find a way to activate a WiFi connection or get Personal to recognise ethernet connections? I can update by ethernet from tty1 but not by WiFi although the WiFi adapter is recognised and has a driver. Hence, I cannot install apps or access the Internet from Personal.
4) Can I find a way of adding users or changing the default password of Ubuntu?

They are just some of the questions I am asking myself at this moment.

Regards.

---

### Post by ventrical on 2015-08-05
I had to do it the sneaky way - [http://ubuntuforums.org/showthread.php?t=2286066&p=13318457#post13318457](http://ubuntuforums.org/showthread.php?t=2286066&p=13318457#post13318457)  ... so I guess I could call it 'snappy sneaky'. :)

 I know not everyone has a USB to SATA docking device but I was able to put the image on to the hdd and I can boot that hdd from most any tower I have on hand. There has to be another way to put it on hdd. I tried with mkusb and no work.

  You are asking a lot of good questions. I hope that you get some answers to.

Regards..

ahh ... umm once the img file is expanded in /Home perhaps it can be *moved* to a partition and detected by Grub? on the same hdd?

```


sudo update-grub


```

I used to do this with Windows floppy disks. MOVE images that is to make bootable disks. Something for me to try. maybe there might even be some breakage !!  :) oh joy! :)

---

### Post by QDR06VV9 on 2015-08-05
> **ventrical said:**
> I had to _do it the sneaky way - [http://ubuntuforums.org/showthread.php?t=2286066&p=13318457#post13318457](http://ubuntuforums.org/showthread.php?t=2286066&p=13318457#post13318457)  ..._ so I guess I could call it 'snappy sneaky'. :)

 I know not everyone has a USB to SATA docking device but I was able to put the image on to the hdd and I can boot that hdd from most any tower I have on hand. There has to be another way to 

ahh ... umm once the img file is expanded in /Home perhaps it can be *moved* to a partition and detected by Grub? on the same hdd?

```


sudo update-grub


```

I used to do this with Windows floppy disks. MOVE images that is to make bootable disks. Something for me to try. maybe there might even be some breakage !!  :) oh joy! :)

Thats a great Idea!
Now you got my curiosity up Got to play with it!
Thanks for the link also.
Regards

---

### Post by grahammechanical on 2015-08-05
The command update-grub when run from Ubuntu installed on a hard disk will detect the Linux kernel in Personal on the USB stick. So, I suppose it would be possible to dual boot a "traditional" Ubuntu and a Ubuntu Personal. 

I have not tested running update-grub from Personal to see if it can detect kernels on other partitions. I suspect that grub.cfg will get overwritten by a transactional update. 

Personal on a USB stick has five partitions. So, I suppose it is possible to use five partitions on a hard disk to re-create Personal. I think that the dd command will allow moving what is on one partition on one disk (USB) to a partition on another disk (hard disk). I guess that the five partitions being used for this will have to have the same names.

The USB has GUID partitions. I do not know if that complicates things for a drive with msdos partitioning. Partition 1 = BIOS boot. Partition 2 = EFI system Fat 32. Partition 3 = system-a Ext4. Partition 4 = system-b Ext4. Partition 4 = writable Ext4.

As far as I can make out the Linux kernel files are in writable cache/assets and not in system-a boot/grub/ or system-b boot/grub/ Personal is a very different country to traditional Ubuntu.

Regards.

---

### Post by ventrical on 2015-08-05
Ok.... I had 'restored' the snappy personal_x86.img to a 160GB maxtor hdd using the program 'disks' about 2 weeks ago and updated it once. I tried to use gparted to make a partiton out of the free space to see if I can restore another copy of personal_x86.img but I get a bug. 

So otherwise I have a 160hdd with the personal_x86.img on it that is bootable on most of the machines I have tired.

I have not tired using 'disks' to restore the image from a USB to bare hdd. Maybe this is the way it has to be done. 

*for me it is not a problem with hardware as I have much surplus drives*

I am also going to see if I can install ubuntu wily *alongside* the personal_x86.img. In fact .. I should try this first and see how compatible it is with grub update .. etc..

edit: Keep in mind that I used a USB to SATA docking device to restore personal_x86.img to 160GB hdd.

Regards..

---

### Post by ventrical on 2015-08-05
> **runrickus said:**
> Thats a great Idea!
Now you got my curiosity up Got to play with it!
Thanks for the link also.
Regards

I think maybe I should have curbed my enthusiasm because it was a complete fail with gparted and ubiquity installer. They are just not talking to each other. The snappy personal image is a whole other animal and completely out of the loop with most recent traditional methods of installing .. but that is why we are here.. to test all of this and find work-a-rounds. Having you on the case .. we know something good is going to happen :)

Regards..

---

### Post by ventrical on 2015-08-05
> **grahammechanical said:**
> After making that post I listened to the Ubuntu On Air session that I had missed earlier in the day. Ollie Reis was there. From what he was saying and my understanding of it (So I could easily be wrong) I think that Canonical has scaled down its ambition a little bit regarding convergence.

Ollie Reis made it clear that every version of Ubuntu is built from the archives and they have deb packages and there is no plan to change that. We already know that 16.04 will be a "traditional" deb packaged version and it will be around for 5 years. But from what Ollie was saying I am getting the idea that Ubuntu personal will be a desktop version of Ubuntu that will be as "locked down" (to use a phrase) as the Ubuntu phone is. And it is Ubuntu personal that will be the converged code base installed on phones, tablets and desktops.

That will not be to everyone's liking (the locking down bit) .....

Regards

 ..and now it starts... it  looks like for now all these transactions will have to happen over the network. It will not be a traditional ubiquity install that we have come to know and love.:) There is definitely a collision of philosophies here and it may even come to a point of being a complete train wreck!  Thats what happens when you have two trains on different tracks converging into one. It's going to be interesting to watch. I think there may even be a back track to the fast track.. I mean it's always worked in other scenarios and is the common sense thing to do. I am all for trying to make this work .. but it is not going to be easy by any stretch of the imagination.

Regards..

---

