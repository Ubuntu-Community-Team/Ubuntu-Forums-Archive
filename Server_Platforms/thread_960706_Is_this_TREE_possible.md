---
title: "Is this TREE possible?"
date: 2008-10-27
forum: Server Platforms
---

### Post by Kellemora on 2008-10-27
Hi Gang

[COLOR="Red"]**PLEASE JUMP TO POST #4, THANK YOU!**[/COLOR]

Trying to reduce my many words of my last post to a simple Picture which should save 1000 words.

Is this possible:  (you can ignore partitions 1 to 8 and jump to other drives below)

/dev/hda1: /boot
/dev/hda2: /    (root)
/dev/hda3:     Extended
/dev/hda4: /usr
/dev/hda5: /Swap
/dev/hda6: /srv
/dev/hda7: /var
/dev/hda8: /opt

/dev/hdb1: /home/users/ 
/dev/hdc1: /home/clients/
/dev/hdd1: /home/clients/images
/dev/hde1: /home/clients/inprogress
/dev/hdf1: /home/clients/finishedjobs

The above 5 hard drives will have 1 partition each, using the entire drive for file storage.

If NOT, how do you spread files across other hard drives?

TTUL
Gary

---

### Post by koenn on 2008-10-27
Hi there, 

yes, it's possible - if you can stick 6 hard disks in your computer.
The (partitions on) the 5 disks all mounted to subdirectories of the same parent directory is actually the most straightforward way of creating lots of storage across multiple disks. 

You might also want to look at LVM, which lets you span multiple disks or make partitions that cross the bounderies of the underlying disks.
Here's an intro: [http://users.telenet.be/mydotcom/howto/linux/disks2.htm](http://users.telenet.be/mydotcom/howto/linux/disks2.htm)
(maybe also [http://users.telenet.be/mydotcom/howto/linux/disks1.htm](http://users.telenet.be/mydotcom/howto/linux/disks1.htm) )


As for your 1st disk with the 8 partitions, 
Imo you don't need to partition that much. Seperate /var /opt and /usr partitions date back from the days that disks were small and it could actually happen that log files or misc data in /var filled up a disk entirely, causing a system crash if /var wasn't on a separate partition.

These days, it  actually only makes sense if you anticipate huge amounts of data in /var or /usr or /opt, or if you can predict disk I/O of your server so well that you can get a performance benefit from having seperate disks for directories that are expected to be accessed simultanously.

---

### Post by Kellemora on 2008-10-27
Thanks for taking a look here for me Koenn, I appreciate it.

I actually don't have my hda set up that way, although I do keep /usr on a separate partition for easier backup.  I do have a lot of proprietary stuff in that folder.  And /swap is not /swap, but just swap.  And their are UUID numbers in there as well.

I purposely left out /home on /dev/hda to see if someone would catch that it was not there.

I THINK it MUST be there, even if it's empty, just /home

And I don't think I can use /home/user in that way on /dev/hdb1
I have this feeling that I have to just use /user/joe without the home in front of it, and tie/link /home to /user/joe, on that drive.

Also, there are only 2 drives in each computer due to heat buildup.  So hdc and hdd would be another computer, hde and hdf would be another computer yet again.

I figure by playing around trying things, on computers not connected to my main system, I can't hurt anything and probably learn a lot.  BUT, finding things to try usually ends in, for example Home Not Found on boot-up even though it's clearly listed in fstab with the proper UUID number.

You gave me some more places to go and study, so I'll do that before asking any more dumb questions, hi hi..........

Thanks for all the help you have given to me today too!

TTUL
Gary

---

### Post by Kellemora on 2008-11-18
Hi Gang

Still searching for the proper way to do this!

Is this possible: (you can ignore partitions 1 to 5 and jump to other drives below)

/dev/hda1: /boot
/dev/hda2: / (root)
/dev/hda3: Extended
/dev/hda4: /usr
/dev/hda5: Swap

Option A: (does not seem to work right, more than one home)

/dev/hdb1: /home/users/
/dev/hdc1: /home/clients/
/dev/hdd1: /home/clients/images
/dev/hde1: /home/clients/inprogress
/dev/hdf1: /home/clients/finishedjobs

Option B:

/dev/hdb1: /home
/dev/hdb2: Extended
/dev/hdb3: /users/theboss
/dev/hdb4: /users/debi  or should it just say /debi?
/dev/hdb5: /users/carol or should it just say /carol?
/dev/hdc1: /clients
/dev/hdd1: /images
/dev/hde1: /inprogress
/dev/hdf1: /finishedjobs

If NOT, how do you spread files across other MANY hard drives?

TTUL
Gary

---

