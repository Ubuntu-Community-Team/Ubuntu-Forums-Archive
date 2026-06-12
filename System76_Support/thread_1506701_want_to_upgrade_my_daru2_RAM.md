---
title: "want to upgrade my daru2 RAM"
date: 2010-06-10
forum: System76 Support
---

### Post by izquierdista on 2010-06-10
Hi Everyone I saw this old post on the system76 forum:
[http://ubuntuforums.org/showthread.php?t=1075517&highlight=daru2+RAM](http://ubuntuforums.org/showthread.php?t=1075517&highlight=daru2+RAM)

I currently have 2.5GB of RAM on my daru2 ultra and want to upgrade to 4GB, the person on the forum suggested that if they want to use more than 2GB they would have to use 64-bit ubuntu. 

oh yeah I forgot I would also like to know how I can add a nvidia video card and if I can do that as an enduser of a daru2 ultra


how do I do that? 

thanks for the help

---

### Post by jml on 2010-06-10
What I have read on line suggests that the maximum ram a 32 bit OS can "see" is 4 gig.  If you already have the ram purchased, you can simply install it, boot your system and see if the 4 gigs is recognised.  If yes, you are good to go, if not, then upgrade to 64 bit version of Ubuntu.  I run 64 bit on both of my Darters, (a first and third generation,) and it works very well.

Joe

---

### Post by thomasaaron on 2010-06-11
You cannot add an nVidia card to a DarU2.

---

### Post by jdb on 2010-06-12
> **jml said:**
> What I have read on line suggests that the maximum ram a 32 bit OS can "see" is 4 gig.  If you already have the ram purchased, you can simply install it, boot your system and see if the 4 gigs is recognised.  If yes, you are good to go, if not, then upgrade to 64 bit version of Ubuntu.  I run 64 bit on both of my Darters, (a first and third generation,) and it works very well.

Joe

There is around 800 MB, almost a gig, of memory space reserved for hardware addresses.
To use any ram in that area it has to be remapped above 4 gig which requires a 64 bit system.
Bottom line is that the most memory you can use in a 32 bit system is a little over 3 gig.

I've loaded 64 bit Lucid on my Daru2 and it seems to be OK but I haven't tried adding memory.

I'm still mostly using 32 bit Karmic on the Daru2 because I haven't gotten around to loading all my apps in the Lucid partition, so there could be bugs I haven't seen yet.

jdb

---

### Post by izquierdista on 2010-06-13
I went ahead and installed the RAM  which gives me a total of 4GB. when i rebooted the computer and went to the system administration-->system monitor-->system tab, it says I have 2.9GB why doesnt it show all 4GB?

---

### Post by izquierdista on 2010-06-13
I SOLVED IT :) by following the instructions in the link below:
[http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/](http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/)

I used option 2 and now when I run the command      free -m
using the terminal 
my memory shows the proper amount

thanks for the help everyone,

---

### Post by jdb on 2010-06-13
> **izquierdista said:**
> I SOLVED IT :) by following the instructions in the link below:
[http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/](http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/)

I used option 2 and now when I run the command      free -m
using the terminal 
my memory shows the proper amount

thanks for the help everyone,

Cool, I didn't know about PAE.

jdb

---

