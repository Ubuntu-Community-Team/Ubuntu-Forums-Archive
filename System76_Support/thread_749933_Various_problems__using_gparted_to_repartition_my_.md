---
title: "Various problems  using gparted to repartition my Serval Performance"
date: 2008-04-09
forum: System76 Support
---

### Post by gbinal on 2008-04-09
Hi folks.  

A new question.  I've looked around a good bit here, via google, and via the gparted forums, but I am hitting snags using gparted-live on a cd to repartition my new Serval Performance**.  

The laptop is a newly purchased (1-2 months ago) Serval, the hard disk is 120 GB 7200 RPM SATA (if I'm reading it right - Hitachi HTS72201).  

I also tried Knoppix, but hit roadblocks there as well (could not resize the two partitions other than my swap for some reason.  

I guess my end question for the good folks over at system76 is to ask how you recommend repartitioning successfully?  I've use gparted several times and felt comfortable, but gparted couldn't see any of my drives.  

The reason for all this is that even though there's a healthy amount of space on :/ I'd very much like to add a few more gigs as I've been running out of space on it.  Plus the main partition with 90+ gigs has more than enough for me to spare.  

With a fresh out of the box Serval Performance, how can I got about resize the partitions.  

Thank you as always for any help you can lend and for being here on the forums.  

**I am going to say this each time I post a question about my System76 laptop, but I am incredibly satisfied with the company and the product.  Good stuff.

---

### Post by thomasaaron on 2008-04-09
You cannot resize a mounted partition. You will have to do it from a live cd. Please follow the instructions in the first part of this tutorial to resize the partitions. (It is for installing windows, but the resizing process is the same.)

[http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine](http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine)

---

### Post by gbinal on 2008-04-09
Hi and thank you for the reply.  

I apologize, I should have said that I was using gparted-cd (I booted into the cd) not the gparted program when I'm logged onto my computer as normal.  

Just fyi, I ended up having luck using the knoppix cd, booting into it and using qtparted.  One nuance I'd missed was that there was a drop down menu in the top right of the program - I needed to choose \sda - that was not the default.  

Thank you again for the response.  Peace.

---

