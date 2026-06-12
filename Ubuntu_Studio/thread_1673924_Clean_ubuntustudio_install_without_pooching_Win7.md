---
title: "Clean ubuntustudio install without pooching Win7?"
date: 2011-01-23
forum: Ubuntu Studio
---

### Post by tedthetrumpet on 2011-01-23
I&#8217;ve managed to bring the ubuntustudio install on my msi wind clone up to 10.10 by a &#8216;sequential install&#8217; (is that what you call it?) from a copy of the latest .iso burned to dvd. However, I&#8217;m not happy, I feel I&#8217;ve got lots of half-digested, uneeded, possibly incompatible things left over from the last system. I&#8217;d kind of really like to delete everything I had before and do a completely fresh install.

I have no data in linux I need to keep. On the other hand, I really, really want to keep an existing Windows 7 system which I dual-boot.

What&#8217;s a good, simple, foolproof, mostly graphical way of doing this, without any terminal hackery? I was thinking that maybe I could boot from a cd and use GParted to turn everything which is not ubuntustudio into unallocated space (or an empty partition?), and then run the installer again?

Here&#8217;s what the hard drive looks like in GParted:

/dev/sda1/ ntfs System Reserved 100 MiB boot
/dev/sda2 ntfs ntfs 59.99 GiB
unallocated 3.29 MiB
/dev/sda3/
-   /dev/sda5/ ext4 / 49.54 GiB
-   /dev/sda6/ linux-swap 2.16 GiB
unallocated 2.49 MiB

I assume that the top two lines are the windows stuff, and that I could just get rid of everything else and start again? Or is there an easier approach?

---

### Post by dawiba on 2011-01-23
You can do a clean Ubuntu 10.10 reinstall graphically [using the method on this page]("http://sites.google.com/site/easylinuxtipsproject/partitioning").

---

### Post by Sylos on 2011-01-23
Personally I would agree with your idea. Use a partition utility to turn everything but the 2 windows partitions into unallocated space and then create more partitions for Ubuntu studio. If it was me I would probabbly create another primary partition to hold the Ubuntu studio install and then a logical partition for the /home directory.

A word of warning though - NO partitioning is foolproof or without risk - Back up your windows and info and have some rescue disks at hand!

---

### Post by tedthetrumpet on 2011-01-23
Thanks for both hints so far. One of the things that holds me back a bit is that ubuntustudio (as opposed to ubuntu) seems to not have that pretty e-z to use graphical installer, the partitioning bit of the install always scares me, never know what is going to get wiped.

If I made unallocated space, should I then make that into one partition for my new install? What about a 'swap' partition, do I need to make that, or will the installer cope with that for me?

---

### Post by Sylos on 2011-01-23
As I said above, I would go for two partitions - one to hold the system (the OS itself) and a separate one for your /home folder. The benefit with this is that if you want to upgrade or your OS throws a major paddy and spits the dummy you can reinstall without loosing all your personal files. I have this type of set up for my Ubuntu studio as it means that I can keep all my sound files on the /home partition and mess with the OS to my hearts content. If I break it then I just reinstall and all my recorded files are still as I left them ready for use. I actually also have the same /home partition available for use by a KXStudio install I have (a nice idea but I didnt like KX and rarely use it - but the theory is sound).

As for Swap - this is a matter of choice. Really it depends on what you do with your computer and how much RAM you have. If you do a lot of RAM intensive tasks then its worth having Swap so the system can keep up. A good indication can be to open the system monitor and watch how your current RAM use and Swap use look when you perform your usual tasks. If you are using up all your RAM using the Swap a lot then definitely create a swap partition. I always have one when I install but it is often unused - I feel I can spare the 1 or 2g space I use for Swap on my HDD and comes in handy if I am pushing things a bit more. The choice is yours really.

Hope that helps.

---

### Post by tedthetrumpet on 2011-01-23
That's really helpful, thanks. This time I think I'm going to try installing vanilla ubuntu first and then upgrading/crossgrading to ubuntustudio along these lines

[https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu](https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu)

This is not really a production machine yet, just gradually working towards a place where I might be able to do at least some of my live stuff on the netbook: Pd, SuperCollider maybe SooperLooper.

---

