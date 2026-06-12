---
title: "Total Noob Question Re: Flash Ubuntu"
date: 2015-07-17
forum: Ubuntu, Linux and OS Chat
---

### Post by cap2 on 2015-07-17
When I run Ubuntu from my flash drive on various computers, does my activity communicate with the computer's inherent hard drive?  My understanding is one can run Ubuntu flash without a hard drive.

Also, any direction towards resources where I might read up on any/everything IT would be appreciated of course :)

---

### Post by ashley-a on 2015-07-17
> **cap2 said:**
> When I run Ubuntu from my flash drive on various computers, does my activity communicate with the computer's inherent hard drive?  My understanding is one can run Ubuntu flash without a hard drive.

Also, any direction towards resources where I might read up on any/everything IT would be appreciated of course :)
Hello cap2!
Don't worry about noob questions or anything - we were all ubuntu noobs at one point or another!
In answer to your question about flash Ubuntu communicating with the computer's hard drive, it does...if you want it to.
On Ubuntu (and any other linux system) all drives (except the boot drive) are in the /mnt folder. The computer's hard drive will be automatically mounted in the /mnt folder, but it wont be interacted with unless you try and access it.

I hope this helps!

---

### Post by cap2 on 2015-07-17
Yes it does, actually... Thanks! &#55357;&#56835;

---

### Post by ashley-a on 2015-07-20
No problem :)

---

### Post by deadflowr on 2015-07-20
> **ashley-a said:**
> .
On Ubuntu (and any other linux system) all drives (except the boot drive) are in the /mnt folder. The computer's hard drive will be automatically mounted in the /mnt folder, but it wont be interacted with unless you try and access it.

The /mnt directory is, by default, an empty location, which a user can manually mount a drive's( really a partition) contents into for access.
(This is why we typically tell users with problems to mount a trouble system's partition there)

For a more accessible way to mount using the Ubuntu Files program (Ubuntu's file manager) if you look inside that program's left side pane you will see a section for devices.
The Devices section will list all connected external (this includes internal) storage devices.
External storage devices are any storage device that are not part of the current system, whether it is an internal hard drive's partition(s), a flash drive or a cd rom.
If you were to click on one of these listed devices, it would be automatically mounted to the /media directory.

But as far as the hard drive and a live session goes.
The live session, by default, only knows that the drive exists, and the basic layout of the drive(how the partitions are laid out, how big they are, and basic drive make and model info)
But until the partitions in the drive are mounted the live session will know nothing about the contents of those partitions.

---

### Post by ashley-a on 2015-07-20
> **deadflowr said:**
> The /mnt directory is, by default, an empty location, which a user can manually mount a drive's( really a partition) contents into for access.
(This is why we typically tell users with problems to mount a trouble system's partition there)

For a more accessible way to mount using the Ubuntu Files program (Ubuntu's file manager) if you look inside that program's left side pane you will see a section for devices.
The Devices section will list all connected external (this includes internal) storage devices.
External storage devices are any storage device that are not part of the current system, whether it is an internal hard drive's partition(s), a flash drive or a cd rom.
If you were to click on one of these listed devices, it would be automatically mounted to the /media directory.

But as far as the hard drive and a live session goes.
The live session, by default, only knows that the drive exists, and the basic layout of the drive(how the partitions are laid out, how big they are, and basic drive make and model info)
But until the partitions in the drive are mounted the live session will know nothing about the contents of those partitions.
That's what I meant...I was trying to make it sound simpler...(grumble Grumble) :p

---

