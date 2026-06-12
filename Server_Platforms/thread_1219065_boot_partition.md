---
title: "/boot partition"
date: 2009-07-21
forum: Server Platforms
---

### Post by abraham.varricatt on 2009-07-21
I read in a server book that as the /boot section of a linux install is (normally) fixed and changes rarely, it would be benificial to keep it in a separate parition.

Something like 500MB ext2 for /boot. And preferably near the beginning of your hard-drive.

How valid is this argument? And for that matter, what do we get in return? Better stability or better performance ?

(Apart from the book, I wanted a 3rd opinion as well) The book in question is this one,
[http://www.amazon.co.uk/Beginning-Ubuntu-LTS-Server-Administration/dp/1430210826/ref=sr_1_2?ie=UTF8&s=books&qid=1248185651&sr=1-2](http://www.amazon.co.uk/Beginning-Ubuntu-LTS-Server-Administration/dp/1430210826/ref=sr_1_2?ie=UTF8&s=books&qid=1248185651&sr=1-2)

---

### Post by dragos2 on 2009-07-21
> **abraham.varricatt said:**
> I read in a server book that as the /boot section of a linux install is (normally) fixed and changes rarely, it would be benificial to keep it in a separate parition.

Something like 500MB ext2 for /boot. And preferably near the beginning of your hard-drive.

How valid is this argument? And for that matter, what do we get in return? Better stability or better performance ?

(Apart from the book, I wanted a 3rd opinion as well) The book in question is this one,
[http://www.amazon.co.uk/Beginning-Ubuntu-LTS-Server-Administration/dp/1430210826/ref=sr_1_2?ie=UTF8&s=books&qid=1248185651&sr=1-2](http://www.amazon.co.uk/Beginning-Ubuntu-LTS-Server-Administration/dp/1430210826/ref=sr_1_2?ie=UTF8&s=books&qid=1248185651&sr=1-2)

ext2 or ext3 is ok for boot. Some people argue that ext2 is faster as a boot, which is
indeed true but I will start a flame with this, just use ext3 at this time (only ext2 and ext3 can be used as boot partitions).

Make it lat least 2-3 GB because you may want to switch to previous kernels, also
depends on how long you want to keep the setup.

Yes, the beginning of the hard drive is recommended - if you want to squeeze the last
drop of boot speed.

---

### Post by az on 2009-07-21
In the Olde days, a computer's BIOS would not be able to access all of a larger hard drive.  In that case, it was always necessary to put the bootloader and the files needed for booting in the beginning of the drive.  Hence, the use of a /boot partition at the beginning of the drive.

If you can find a computer from the mid 90s, you may be able to reproduce this.  In fact, you may be able to install Ubuntu on a 40 gig hard drive and boot fine and dandy until you update your kernel.  The new kernel may be saved further up on the hard drive and not be accessible to the motherboard at boot time.

But nowadays, that's not necessary.

---

### Post by Cheesemill on 2009-07-21
> **dragos2 said:**
> ext2 or ext3 is ok for boot. Some people argue that ext2 is faster as a boot, which is
indeed true but I will start a flame with this, just use ext3 at this time (only ext2 and ext3 can be used as boot partitions).
 
Not true, I'm happily using ext4 on my boot partition with Jaunty.
 
> Make it lat least 2-3 GB because you may want to switch to previous kernels, also
depends on how long you want to keep the setup.
 
The linux kernel is currently about 16 MB, 2-3 GB is way overkill, you could get 120-180 kernels in that amount of space. All of my boot partitions are 128 MB, that's enough for 8 different kernels which is plenty IMHO.

---

### Post by dragos2 on 2009-07-21
> **Cheesemill said:**
> Not true, I'm happily using ext4 on my boot partition with Jaunty.
 

Glad to hear that. What kernel version allows this ?
 
> **Cheesemill said:**
> 
The linux kernel is currently about 16 MB, 2-3 GB is way overkill, you could get 120-180 kernels in that amount of space. All of my boot partitions are 128 MB, that's enough for 8 different kernels which is plenty IMHO.

I said that is depends on how long he plans to keep the setup.

---

### Post by cariboo on 2009-07-21
I'm not sure what the default Jaunty kernel is any more, but I'm running 2.6.28-13, it boot just fine from ext4.

Edit: I just checked my server, I haven't rebooted yet since the kernel update, it is using 2.6.28-11

---

### Post by abraham.varricatt on 2009-07-21
> **dragos2 said:**
> 
I said that is depends on how long he plans to keep the setup.

If you mean how long I plan to run the linux system without installing another OS over it, then I'm hoping to do it until 2013  ... that's when the Ubuntu8.04 LTS runs out, right?

Until now, I've never given the /boot section much thought. I usually stick with making an entire hard-disk for Ubuntu (home-desktop) and re-formatting it every 6 months. :)  But after reading about it, I got curious.

I amazed that people actually reserve an entire partition for the /boot section! Hmm... Considering that Cheesemill has got it running just fine on 128MB (and he considers it plentiful!), perhaps I'll copy that? From the way I see things, it should be fine for my setup.

Tell me Cheesemill, do you make regular back-ups of the /boot as well? To my understanding, if anything goes wrong, all one would need to make the system accessible is write the back-up copy to /boot.

---

