---
title: "Raid 5"
date: 2008-04-04
forum: Server Platforms
---

### Post by rgotten on 2008-04-04
I have built my server, it has a duo core on a nvidia 680isli motherboard with 2 gib of memory and 3 hard drive of 500 gb each, I am planning to do RAID 5. I am going to install Ubuntu server and then Kubuntu GUI (unlkess otherwise advise), How do i do the RAID 5 on Ubuntu server

---

### Post by rickyjones on 2008-04-04
> **rgotten said:**
> I have built my server, it has a duo core on a nvidia 680isli motherboard with 2 gib of memory and 3 hard drive of 500 gb each, I am planning to do RAID 5. I am going to install Ubuntu server and then Kubuntu GUI (unlkess otherwise advise), How do i do the RAID 5 on Ubuntu server

Well I see two possible options.

1) Hardware RAID. You'll need to purchase a supported RAID card and configure the array from within this card.
2) Software RAID. You'll use mdadm to create and monitor your array. A google search should help. I took the liberty and here are some links that I found:

[http://www.linuxquestions.org/questions/linux-software-2/raid5-using-mdadm-how-to-mount-devmd0-387769/](http://www.linuxquestions.org/questions/linux-software-2/raid5-using-mdadm-how-to-mount-devmd0-387769/)
[http://ubuntuforums.org/archive/index.php/t-517282.html](http://ubuntuforums.org/archive/index.php/t-517282.html)
[http://www.networknewz.com/networknewz-10-20030113mdadm-A-New-Tool-For-Linux-Software-RAID-Management.html](http://www.networknewz.com/networknewz-10-20030113mdadm-A-New-Tool-For-Linux-Software-RAID-Management.html)
[http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188)

I hope this helps!

Sincerely,
Richard

---

### Post by rgotten on 2008-04-04
This motherboard has the capabilities fo RAID 0 1 5, do i still need a RAID card..And if yes, which is better the software of the hardware (more secure)

---

### Post by rickyjones on 2008-04-04
> **rgotten said:**
> This motherboard has the capabilities fo RAID 0 1 5, do i still need a RAID card..And if yes, which is better the software of the hardware (more secure)

You'll want to see if your motherboard's onboard RAID is supported by Linux. Most of the time the onboard RAID depends on a software driver to function correctly, and unfortunately this usually means Windows is required.

Secure is not the correct term to use here in my opinion. RAID has nothing to do with security. 

Hardware RAID solutions are usually faster than a software solution because they have a dedicated processor for organizing your data. However if the hardware fails you must replace it with an identical card or else you may run into some severe problems.

Software RAID solutions are usually a little slower because they use the servers CPU to perform storage calculations. The nice thing, however, about software RAID is that you can usually survive a hardware failure (such as a failed hard disk controller) because all of the RAID information is stored in the software on your disks.

I hope this helps you out!

Sincerely,
Richard

---

### Post by rgotten on 2008-04-04
Well i talk to the manufactor of the motherboard, and they said that i can get raid 5 on the BIOS,(when i saw the instruction it only give you the option of stripped or mirror, i did not see RAID 5 (i believe that raid 0 is stripped and raid 1 is mirror) will this be ok, or  if i can do this will it be still safer to also get software RAid...

---

### Post by rickyjones on 2008-04-04
> **rgotten said:**
> Well i talk to the manufactor of the motherboard, and they said that i can get raid 5 on the BIOS,(when i saw the instruction it only give you the option of stripped or mirror, i did not see RAID 5 (i believe that raid 0 is stripped and raid 1 is mirror) will this be ok, or  if i can do this will it be still safer to also get software RAid...

You still need to ask the manufacturer if the onboard RAID is supported by the Linux kernel. I can't help you with that.

If it is supported then you could probably use the BIOS to configure your RAID.

Otherwise you can always default to using the mdadm software as outlined in the links that I posted above.

-Richard

---

### Post by rgotten on 2008-04-04
I do not believe they are supported by linux, but let me ask you, the motherboard is on the BIOS, will that have to do anything with OS?, they send me to this link on there website: [http://www.evga.com/support/knowledgebase/](http://www.evga.com/support/knowledgebase/) search for raid motherboard type is 680i sli. Thnaks for your help

---

### Post by rgotten on 2008-04-06
Finally i am ready to install ubuntu server edition and even though the motherboard is raid enable evidently is a fakeraid and will not work under ubuntu. After researching is my impression the the sofware raid will work well and even sometimes it is better than the hardware and less expensive. This is my question in the event i need to buld from a crash ( i will still make backups of the server), But in regards to the raid this are my questions:

Originally i was going to do a raid 5, but then reading all over the internet found that i should have to do boot in raid 1 and the rest for storage in raid 5, so if the boot section is damage i can still boot up. I have (3) 500 gb hd then:
a) how big should the boot partition be for the raid 1? 
b) Since i have the 3 hard drive, should i have the same boot partition areas on each of this 3 hd? and can this 3 partiton be on read 1 
c) can i have raid 1 in this 3 equal size partitions, and then do the rest of the partition for each one of the hd for the raid 5 so evrything is on equal sizes?

Remember i am completely new to Ubuntu server, and instructions will be well apreciated

---

### Post by rickyjones on 2008-04-07
> **rgotten said:**
> Finally i am ready to install ubuntu server edition and even though the motherboard is raid enable evidently is a fakeraid and will not work under ubuntu. After researching is my impression the the sofware raid will work well and even sometimes it is better than the hardware and less expensive. This is my question in the event i need to buld from a crash ( i will still make backups of the server), But in regards to the raid this are my questions:

Originally i was going to do a raid 5, but then reading all over the internet found that i should have to do boot in raid 1 and the rest for storage in raid 5, so if the boot section is damage i can still boot up. I have (3) 500 gb hd then:
a) how big should the boot partition be for the raid 1? 
b) Since i have the 3 hard drive, should i have the same boot partition areas on each of this 3 hd? and can this 3 partiton be on read 1 
c) can i have raid 1 in this 3 equal size partitions, and then do the rest of the partition for each one of the hd for the raid 5 so evrything is on equal sizes?

Remember i am completely new to Ubuntu server, and instructions will be well apreciated

From what I've read I don't believe you can boot from an mdadm RAID5 array, only from a RAID1 array. I do not know how to configure this, however. It might be much simpler to add an additional two hard drives, smaller drives, that can be used for the root system for booting and configure those as a RAID1 array.

The original links that I posted above will guide you in creating a RAID5 array. Please review them.

Sincerely,
Richard

---

### Post by ikonia on 2008-04-07
your /boot partition can't be on a raid5 or raid0 array.

It needs to be on a raw device or raid1 array.

Please please please, use software raid over the crappy attempts at hardware raid on your motherboard.

---

### Post by rgotten on 2008-04-07
I have two old har drive, one is 10 gy anb the other is 40gy, can i use this for raid 1, also i am trying to do raid 5 for storage since i heard that if one fails the other 2 will rebuld, is this true with software raid, or should i just return one of the 3 500 hard drive and do raid 1 with two 500 gib

---

### Post by rgotten on 2008-04-07
Can you please give me some direction on how to do this, I am completely new to ubuntu

Thanks

---

### Post by kevdog on 2008-04-07
Are you sure you can't boot to a RAID 5 card?  I have a 3-ware RAID5 card, and although I haven't yet configured it to run under a Linux environment, when I bought it one year ago, the main impetus was that it stated it was Linux supported.  

Raid5 on MOBO's is nothing more than a fancy software raid implementation, since its actually the processor that is doing the XOR implemenation, rather than a separate processor.  True Hardware RAID5 with a decent controller card (ie 3ware) is very fast.  The card is warrantied up to 3 years.  Ive had a number of hard drives crap out on me, and its been a life saver to have a RAID5 array.

---

### Post by ajeannotte on 2008-04-08
i believe he was saying that you cannot boot to a software RAID 5. if you use a hardware controller it just looks like 1 big drive to the OS.

---

### Post by ajeannotte on 2008-04-08
> **rgotten said:**
> I have two old har drive, one is 10 gy anb the other is 40gy, can i use this for raid 1, also i am trying to do raid 5 for storage since i heard that if one fails the other 2 will rebuld, is this true with software raid, or should i just return one of the 3 500 hard drive and do raid 1 with two 500 gib

To do RAID 1 the drives should be the same. 

To install Linux you don't NEED a RAID array, just 1 harddrive is fine. The way i see it, it's the data that's important and should be on the RAID 5, the operating system and programs can be replaced easy enough.

I am in a similar situation right now as well. I have just purchased 3 x 500GB SATA harddrives. My plan is to use a previous 250GB drive to install my operating system(s) on, but the data is the same for all OSs looking at the RAID 5.

I look forward to trying the advice from the first page of this post when I get home.

---

### Post by rickyjones on 2008-04-08
> **rgotten said:**
> Can you please give me some direction on how to do this, I am completely new to ubuntu

Thanks

I posted some links in one of my first posts that contained directions for configuring a RAID 5 array using mdadm in Linux.

-Richard

---

### Post by ajeannotte on 2008-04-08
> **rickyjones said:**
> I posted some links in one of my first posts that contained directions for configuring a RAID 5 array using mdadm in Linux.

-Richard


Wicked. I tried last night and got the RAID5 working using the second of the 4 links posted on the first page of this thread. 

Many thanks Richard.

---

### Post by rickyjones on 2008-04-09
> **ajeannotte said:**
> Wicked. I tried last night and got the RAID5 working using the second of the 4 links posted on the first page of this thread. 

Many thanks Richard.

You're very welcome!

Sincerely,
Richard

---

