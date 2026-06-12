---
title: "Stuck at Ubuntu Server Installation - Help!"
date: 2015-11-20
forum: Server Platforms
---

### Post by soamz on 2015-11-20
Just got a refurbished Dell 2950 server from a vendor to make an in house web server. 
Inserted 2 new hard drives and then did the RAID configuration of the hard drives. 

Then downloaded Ubuntu server 14.03 and made 2 bootable media, one USB and CD. 
Then booted it from USB and when it asked to detect CD-ROM simply clicked continue and it went ahead with the installation.
It asked for the static IP and I entered the details, and set it to eth0 as thats where the CAT6 cable is connected. 

Next I saw this screen and Im stuck, what to enter now. 

[ATTACH=CONFIG]265685[/ATTACH]

---

### Post by Lars Noodén on 2015-11-20
It looks like it is asking for the rest of the networking information.  Specifically it needs two or three IP addresses for DNS lookups.  What are the addresses of your three best DNS servers?

---

### Post by soamz on 2015-11-20
> **Lars Noodén said:**
> It looks like it is asking for the rest of the networking information.  Specifically it needs two or three IP addresses for DNS lookups.  What are the addresses of your three best DNS servers?

I dont have any DNS server right now. 
I have bought 2 extra servers to setup as DNS server, buts its not done yet. 

So, I can simply type google DNS for those 2 entries ?

---

### Post by Lars Noodén on 2015-11-20
Your ISP has some closer to you.  Those would be preferable, I think.  Though you could also use Google's DNS and OpenDNS, if you are ok with the disadvantages.

---

### Post by soamz on 2015-11-20
> **Lars Noodén said:**
> Your ISP has some closer to you.  Those would be preferable, I think.  Though you could also use Google's DNS and OpenDNS, if you are ok with the disadvantages.

yes, my ISP has given me 2 of their DNS servers too. 
So, shall I enter them ?

And later, can I change those 2 entries to my own DNS IP, once my DNS servers are set ?

---

### Post by Lars Noodén on 2015-11-20
Yes, enter them first in the list for now.  You can change them later when you have your own set up.  But in general you want the closest and fastest ones first, otherwise you will unnecessarily slow down almost all of your network activities.

---

### Post by soamz on 2015-11-20
> **Lars Noodén said:**
> Yes, enter them first in the list for now.  You can change them later when you have your own set up.  But in general you want the closest and fastest ones first, otherwise you will unnecessarily slow down almost all of your network activities.

Okay sure!
Then google DNS shows the nearest figures than my ISP's DNS names. 
I think better off to use google DNS then .

---

### Post by Lars Noodén on 2015-11-20
You can compare them with traceroute and ping to see whether Google's or your ISP's are more responsive.

---

### Post by soamz on 2015-11-21
While doing this, my current went out and I just started the server again and went to boot and went ahead. 

Then I did not see this step at all, dont know why. 
May be ubuntu server installation remembers things or already writes to disk ?

But now when I started it, it said no network cards found, which is weird.

And now Im stuck here. 

Whatever I click, it returns back to the same page. 

[ATTACH=CONFIG]265698[/ATTACH][ATTACH=CONFIG]265699[/ATTACH]

---

### Post by darkod on 2015-11-21
You need to create your partitions on the sda disk. You are trying to continue without any partitioning layout and without specifying the root partition. Hence the message on the second screen.

When on the first screen, highlight the sda disk and hit Enter. That will ask you if you want to create partition table. Once you do that, you need to create the partitions you want. Usually the minimum is root and swap partitions. But on a server you can have other separate partitions for different mount points, as per your liking.

Imagine this screen as asking you where you want to install. You are not selecting anything so it can't go forward.

---

### Post by soamz on 2015-11-21
> **darkod said:**
> You need to create your partitions on the sda disk. You are trying to continue without any partitioning layout and without specifying the root partition. Hence the message on the second screen.

When on the first screen, highlight the sda disk and hit Enter. That will ask you if you want to create partition table. Once you do that, you need to create the partitions you want. Usually the minimum is root and swap partitions. But on a server you can have other separate partitions for different mount points, as per your liking.

Imagine this screen as asking you where you want to install. You are not selecting anything so it can't go forward.

Is there a way I can wipe out everything and let it install again ?

I think, it has happened due to the power cut thing.

---

### Post by Lars Noodén on 2015-11-21
Yes, if you create a new partition table, all the existing partitions will be wiped out.

---

