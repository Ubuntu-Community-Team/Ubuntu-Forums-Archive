---
title: "how to add to an existing partition."
date: 2008-03-17
forum: Server Platforms
---

### Post by twistedtwig on 2008-03-17
Hi all,

I have an old compaq server and had 3 36l.4GB scsi drives in which I just extended to 5.  This is the first time I am have really dealt with raid drives and did not understand how it all works.

As you can see from the screen dump attached I had 101.75GB of disk which was getting full.  I added the extra drives in and gained 67.83GB.  I read a little about GParted and it has explained to me what has happened but I do not really know how to resolve it.

my problem is the drive is mounted to /mnt/media but I can not view it.  I get the message, "The folder contents could not be displayed.  Sorry, couldn't display all the contents of "media"".

There is nothing displayed at all for that folder and its sub folders.

Before I installed GParted I presumed it was all lost and I would have to start again.  But looking at the picture it would seem it is still there but not able to show it. 

My question is:

1) is it possible to get the /mnt/media folder to show its contents again without formatting it and loosing the data?

2)  Can I add the 67.83GB drives into the 101.75GB drives to form one larger drive, (and hopefully still have the info, if it has to be lost it can be replaced, I think!).


Thanks for any and all advice.

As I say this is a competlely new area for me so I am a bit confused and nervous when its a lot of data involved.

Cheers

---

### Post by twistedtwig on 2008-03-18
I have been reading around it this morning but have not found an answer (at least one that I understand yet, my knowledge is growing slowly on this but is very low atm).

any and all advice would be great.  Thx

---

### Post by crouton on 2008-03-21
It looks like you're using a Compaq SmartArray of some type; did you add the drives into the RAID set?  This usually involves hitting F8 when the server is displaying the SmartArray information (on booting up), and adding the drives into the existing logical drive.  From the drive size, you have the drives set up in RAID0.  This is going to cause you a lot of pain, as one drive failure will make all of your data unrecoverable.  If you're OK with that, it should be pretty easy to expand the RAID0 to use the additional drives.

---

