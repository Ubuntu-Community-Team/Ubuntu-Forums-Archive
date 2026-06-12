---
title: "Confused about a clean install"
date: 2010-04-30
forum: System76 Support
---

### Post by Tom Atkins on 2010-04-30
I have a Ratel Value and a Starling Net Book. I am planning on doing a clean install of 10.04 on both machines.

My home directory is on a separate device (sda3). Is there a way to do the install without wiping out my home directory? 

The instructions sound like /home will be wiped along with / even though they are on separate devices.

I was planning on backing up /home, of course, just to be safe, but I do not understand why it has to be deleted to install the new system or am I misinterpreting the instructions.

Also, should I backup anything else?

Thanks for ny help

Tom Atkins

---

### Post by nitstorm on 2010-04-30
I don't think ur /home will be deleted unless you check the format option. But you might want to wait till the real pros give you the thumbs-up...

---

### Post by samalex on 2010-04-30
When installing you can manually setup the partitions so it formats  / (root) partition for the OS and leaves /home partition alone, but honestly I'd backup everything just to be safe.  It's one of those 'better safe than sorry' things :)

Sam

---

### Post by jml on 2010-04-30
You should be able to keep your home directory intact with a clean install.  That is in fact, one of the major advantages of keeping a separate home directory.

When you begin the install process and you are at the format stage.  Do not select format the entire disc.  Specifically select the drive or partition you want the install on and your home partition should remain intact.  Oh, and I fully agree with your plan to back up your home partition first.  Accidents do happen, even in Linux.  Good luck.

Joe

---

### Post by Tom Atkins on 2010-04-30
Thanks for the help. I thought that I would be safe but just wanted to check.

I will wait about a week until things calm down. This is a Linux only system so I should not have the GRUB problems I have seen on the Update forum.

Tom Atkins

---

