---
title: "A questions about the restore CD"
date: 2007-03-18
forum: System76 Support
---

### Post by klato on 2007-03-18
Hey guys,

I just got my Gazelle Performance and am loving it.  However, I ordered it with a 40gb hard drive with plans to remove it and put in my 120gb monster that I bought not too long ago.  I want all of the hardware to work as it does right now when I first booted the computer.

If I install Ubuntu from scratch on that disk, and then apply the system76 driver install, will this achieve the desired effect?  Or would it be better to use the restore dvd and then rearrange my partitions to how I had them before (/, /home, swap), and then copy over my /home stuff?

Also, the drive I want to put in is a Seagate Momentus 5400.2 120gb...I just checked out the hard drive, and it looks like it has a different connection in there.  Is this hard drive compatible with my gazelle?

Thanks! :)

update: after doing some research, it looks like i have an ata-6 version of the hard drive instead of serial ata...guess i'm screwed eh?

---

### Post by crichell on 2007-03-19
> If I install Ubuntu from scratch on that disk, and then apply the system76 driver install, will this achieve the desired effect?

You've got it - install Ubuntu via the standard disk.  Update your system.  Run the System76 driver and you're back to factory deafults.  If I'm understanding correctly I'd arrange my partitions during the Ubuntu installation process and then move over the home directory.

> update: after doing some research, it looks like i have an ata-6 version of the hard drive instead of serial ata...guess i'm screwed eh?

The Gazelle Performance?  That should be SATA not PATA.  Do you have a camera at the top of your LCD?

---

### Post by klato on 2007-03-19
Carl,

Thanks for the response.  What I meant to say was that the hard drive that I bought was actually PATA.  The one in my Gazelle Performance is indeed SATA.

BTW, my laptop has 1GB of RAM, and since I plan on having 3 partitions, is there a recommended swap size?

---

### Post by crichell on 2007-03-19
> is there a recommended swap size?

Swap sizing isn't an exact science - in fact we call it a SWAG (Scientific Wild *** Guess).  Generally you want at least your amount of memory - if you add another 1GB stick down the road you'll want at least 2 GB swap.  IBM has a good article on this.

[http://www-128.ibm.com/developerworks/aix/library/au-satswapspace.html](http://www-128.ibm.com/developerworks/aix/library/au-satswapspace.html)

It gets involved and most of it isn't really relevant but it may helo you decide how much space you want to allocate.

---

### Post by klato on 2007-03-20
Thanks Carl.

---

