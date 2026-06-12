---
title: "Raid on ubuntu server"
date: 2010-01-25
forum: Server Platforms
---

### Post by melocco on 2010-01-25
I am new to ubuntu and linux, but I am tiered of Windows..  I installed Ubuntu server on a system.  I am wanting to run raid 5 with 4 1.5 terabit drives. I did a low level format on each drive and set up raid 5. I am using a rosewell raid pci controler card. Ubuntu see's it, but when I try to do a partition it tells me that it's a error and in use. 
 
"one of more blocks are holding /dev/mapper/sli_bgabdhddejci"
 
I installed the gui and I am useing it to partition it.  All the drives are seen as a Raid Component, and the one large file is seen twice.  Any ideas about setting this up. I am hoping I can set it up as a file server and share files with my home theater and other computers...  That's my next question once I get the drives seen..  How do I share the drive on the network..  But that's for another day...  Thanks for any help...

---

### Post by Vegan on 2010-01-25
Not sure about your RAID problems, but you should boot to a single disk and then use the RAID for data.

To share with Windows clients, SAMBA is the popular choice.

---

### Post by melocco on 2010-01-25
I have the OS on a 250 gig wd hd. the data is going to go on the raid. That's the way I thought I would be safest. Then if the OS goes out, I can just reinstall the os and keep the raid. If a drive in the raid goes out, I can put a new drive in and rebuild it..

---

### Post by melocco on 2010-01-25
Samba..  What is that? where can I can it?

---

### Post by melocco on 2010-01-25
Also, I'm wanting to share with windows and apple..  The mac is hooked up to my TV and some of my other computers are running windows..  So it would need to beable to work on all three..

---

