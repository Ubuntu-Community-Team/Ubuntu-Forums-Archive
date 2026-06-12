---
title: "Performance Issues?"
date: 2011-11-13
forum: Server Platforms
---

### Post by pjm2008 on 2011-11-13
Hey guys, I was wondering if anyone could answer some questions. I am new to Ubuntu and am running the server addition.

So, I've recently built it. 18TB in Raid 5. And I am copying things over from my Time Machine and am only getting 7MB/s, is that common?

---

### Post by rubylaser on 2011-11-13
Welcome to the Forums :) You're going to need to provide MUCH more info to get an answer.  Hardware specs, hardware / software RAID, network setup, machine you're transferring from.  Any benchmarks you've run, like iperf, hdparm, top, iostat, etc.

---

### Post by a2j on 2011-11-14
how recently? maybe its still syncing? but yeah, more details would be nice.

---

### Post by pjm2008 on 2011-11-14
Sorry for not being more descriptive. Anyways, we haven't done any benchmarks on it cause we just wanted the thing up and running and start to transfer over all of our movies and such. Anyways our build configuration is so: 
-RAM: 8GB DDR3 SDRAM 1333
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820220466](http://www.newegg.com/Product/Product.aspx?Item=N82E16820220466)
-CPU: Intel Core i3 Sandy Bridge 2.6GHz
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819115094](http://www.newegg.com/Product/Product.aspx?Item=N82E16819115094)
-MOBO: GIGABYTE GA-Z68A-D3H-B3 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128502](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128502)
-PSU: OCZ 500W
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817341016](http://www.newegg.com/Product/Product.aspx?Item=N82E16817341016)
-HDD: Western Digital My Book 3TB [x6]
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136749](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136749)
**Note: We have removed all hard drives out of the enclosures and attached via SATA.** 
-Root HDD: Western Digital My Book 500GB 
(Bought this long time ago and just removed it from another enclosure.) 

Everything has been setup in terms of RAID 5 (the 6 3TB) and everything went smoothly during the software setup of the RAID configuration and took 50hours to complete. Everything in the house is hardwire that we are transferring from (which all have 10/100/1000 ethernet). We are running Ubuntu Server 11.04 (the most current one) . Basically we are trying to setup this computer to be our Plex Box and Subversion w/ Trac on it for our programming projects. Last night speeds were around 7MB/s and this morning are now 1.5MB/s write speed from Time Capsule, Mac Mini (2011 i7 8GB RAM). 

Our setup in the house is such: 
-Every room has 2 ethernet ports
-38Mbps internet download speed (I usually get about 4-7MB/s)

Not sure what else to include, let me know if there is any additional info I can give. Sorry about being new to Ubuntu and want to learn this as it deals with my programming. Thanks for any suggestions / anything to help us facilitate to find out what's going on.

---

### Post by darkod on 2011-11-14
Stupid question but worth asking: Your switch is also Gb right? If you are using your ISP router for example, most probably it's only 100Mbps. 7-10MB/s is about what you would get.

Another thing is that WD uses Caviar Green for their My Book editions if I'm not wrong. That's a 5400rpm drive. But it should still do a lot faster than 7MB/s.

---

### Post by pjm2008 on 2011-11-14
Nope, everything is 10/100/1000 ethernet. So, I've ran some speed test for my internet connection as well cause I realized I was only downloading files internally (been trying to move 6TB of stuff to it) and my download speed high 18Mbps the first time, I was happy. All the other times 2Mbps or less. All other devices in the house get 20Mbps+ when I test them now. And it won't hit above that 2Mbps, it being the Ubuntu server. 

Also I've been installing jdownloader to see if I could try a file from my hosting account and it is taking forever in terms of doing the jdownloader, when my Mac and others update within minutes. Not sure what's going on. Hopefully that more information helps with any leads to check out would be appreciated. 

Thanks for the responses so far by the way.

UPDATE: So it looks like I jumped the gun. I have started a download from my site and I'm getting 4MB/s down to the server. And I'm starting to think it may be the slow read speed of my drives on the network. If anyone thinks it might be something different let me know cause we are getting 1MB/s from drives on the network and 4MB/s outside the network. Thanks!

---

### Post by cmileto on 2011-11-14
My experience is that the Caviar Green from their My Book stuff cannot even max out my usb speed (less than 2mb/sec for sure), much less anywhere close to even 10mb/s  and 100 or 1gb? never going to happen. Good luck

---

### Post by pjm2008 on 2011-11-14
> **cmileto said:**
> My experience is that the Caviar Green from their My Book stuff cannot even max out my usb speed (less than 2mb/sec for sure), much less anywhere close to even 10mb/s  and 100 or 1gb? never going to happen. Good luck

You know they aren't in the enclosures anymore and are connected via SATA to the motherboard? I removed them from the enclosures.

---

### Post by cmileto on 2011-11-15
Reading the feedback reviews on that newegg page does seem to point out the drive performance is very good, and the enclosure very bad. If they are out of that enclosure then I dont know, my apologies

---

### Post by darkod on 2011-11-15
> **cmileto said:**
> My experience is that the Caviar Green from their My Book stuff cannot even max out my usb speed (less than 2mb/sec for sure), much less anywhere close to even 10mb/s  and 100 or 1gb? never going to happen. Good luck

Make sure you use 'b' and 'B' wisely, it has a 8x difference. :)

I guess you meant it can't max 2MB/s, 2Mb/s is nothing.
And maxing 2MB/s should be no problem also.

As it happens, my network disk is WD My Book World Ed, the 1TB single disk version, and when I copy stuff to it from my PC it runs at 10MB/s which is about correct since my router is 100Mb/s and taking some network overhead in account. The disk is still in its original enclosure, simply connected to the router.

So the disks should be able to do at least 10MB/s, even more. Taking into account that the OP has them in RAID5, it should be even much much faster because it writes to more disks at the same time, but not the same data (it's not a mirror).
I haven't has a chance to try something like this, but with a 1Gb network and with raid5 array that writes to more disks at the same time, I think you should be coming close to maxing out the 1Gb.

---

### Post by a2j on 2011-11-15
could you post

*mdadm --detail /dev/md0* -> or what ever your raid5 device is

also, are there any dropped packets or errors in *ifconfig* ?

and hdparm of your raid device would be nice also

*hdparm -Tt /dev/md0*

---

