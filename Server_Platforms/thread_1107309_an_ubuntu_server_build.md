---
title: "an ubuntu server build"
date: 2009-03-26
forum: Server Platforms
---

### Post by maclenin on 2009-03-26
Essentially, I am looking to build an ubuntu file/media/web server which will double as a basic desktop with vanilla gui (xfce)....

To achieve this, I am thinking the following hardware configuration will facilitate all of the above and more...

...motherboard: [**gigabyte**]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128357")
...cpu: [**intel e8400**]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819115037")
...ram: [**g-skill 4gb**]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820231122")
...hdds: [**western digital 2tb**]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136284")
...dvd: [**lg**]("http://www.newegg.com/Product/Product.aspx?Item=N82E16827136152")
...floppy: **(legacy)**
...power: [**corsair 550w**]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817139004")
...case: [URL="http://www.newegg.com/Product/Product.aspx?Item=N82E16811147033"]**rosewill**
[/URL]
...total: **$750**

Thanks for any thoughts!

---

### Post by albandy on 2009-03-26
were it's supposed this server will be exposed?
if you are thinking in a great number of users you configuration it's too poor, but if is for personal use it's enought.

---

### Post by maclenin on 2009-03-26
Thanks, **albandy**.

The server will be primarily for personal use and as a potential test environment for web sites (with very limited traffic)....

What more would it need to be effective as a "public" web server?

Thanks, again, for the comments!

---

### Post by albandy on 2009-03-26
> **maclenin said:**
> Thanks, **albandy**.

The server will be primarily for personal use and as a potential test environment for web sites (with very limited traffic)....

What more would it need to be effective as a "public" web server?

Thanks, again, for the comments!

2xIntel Xeon CPU (at least 2 cores per CPU) 
HW Raid Disk System SAS if possible
+8GB RAM

I recomend you to see some HP Proliant server specs to get an idea of how a server should be configured

---

### Post by maclenin on 2009-03-26
Yep - I took a look at the HP Proliant servers before I decided to build a system on my own....

Essentially, the traffic on my network will be personal/home office - with no "real" web traffic - no more than 10 people, perhaps (at the most) - simultaneously.... No "public numbers" of simultaneous web visitors....

I just want to be certain that it'll be able to handle basic music/video/file-sharing as well as "personal/home office" levels of use as a web server....

Thanks, **albandy**, for the follow-up!

---

### Post by albandy on 2009-03-27
Also I recommend you to make a raid-5 with 3 hard disk, it will increase the speed of data transmission and adds redundancy.

---

### Post by Spikerok on 2009-03-27
my pc spec are:
1gb ram
1tb
2.6ghz cpu 1core
but have ability of upgrade to 4gb, 4core cpu and some more harddrives

---

### Post by tubezninja on 2009-03-27
> **albandy said:**
> 2xIntel Xeon CPU (at least 2 cores per CPU) 
HW Raid Disk System SAS if possible
+8GB RAM


I've seen above-moderate-traffic web sites run quite well on **far** less RAM.  Under moderate use, I've seen a LAMP server configuration live comfortably using 384-500MB of RAM, using anything additional for caching and buffering.  However, that buffering is important if you have slow hard drives.  RAM is cheap, so if the OP can afford 8GB, then it's a good investment.  However unless he plans on running slashdot or an ubuntuforums clone, his 4GB configration should be more than adequate for now.

The bottleneck **will**  be the hard drive though.  2TB is big, but if you're doing something media-heavy **and** testing web sites under moderate load, that single hard drive will be your bottleneck.  Multiple processes doing I/O to a single hard drive will kill performance, no matter how many CPU cores you have. A RAID is useful, but if your budget is constrained or if you're not going that heavy-duty, keep the 2TB or a cheaper 1.5TB drive for media and large files only (perhaps as the /home partition), and use a separate smaller drive for the OS and web directories.

---

### Post by maclenin on 2009-03-27
Thanks much, all!

Just to clarify...

...**albandy**: you are suggesting raid-5 across 3 hard drives?

...**scaredpoet**:
...ram: my motherboard choice can support 4gb ram - MAX - would you suggest I spring for a mobo that can handle more ram?
...hdds: I will start with 2 x 1tb sata hard drives - with mobo space for a possible 3rd sata - would you suggest 3 x 1tb? Or are you suggesting, for example, 1 x 250gb for "/" and assign the other 2 x 1tb to /home? Not certain re: raid - perhaps I'd dedicate 50 gb to /  and 8gb to swap on the first of the 1tb drives and assign /home to the other 2 x 1tb drives?

...note: this server will be, primarily, a home file/media server - with very limited - mostly in-house - web use....

Thanks, again, for these great, on-target comments!

---

### Post by albandy on 2009-03-27
> **maclenin said:**
> Thanks much, all!

Just to clarify...

...**albandy**: you are suggesting raid-5 across 3 hard drives?

...**scaredpoet**:
...ram: my motherboard choice can support 4gb ram - MAX - would you suggest I spring for a mobo that can handle more ram?
...hdds: I will start with 2 x 1tb sata hard drives - with mobo space for a possible 3rd sata - would you suggest 3 x 1tb? Or are you suggesting, for example, 1 x 250bg for "/" and assign the other 2 x 1tb to /home? Not certain re: raid - perhaps I'd dedicate 50 gb to /  and 8gb to swap on the first of the 1tb drives and assign /home to the other 2 x 1tb drives?

...note: this server will be, primarily, a home file/media server - with very limited - mostly in-house - web use....

Thanks, again, for these great, on-target comments!

yes, raid-5: one of the drives it's an XOR (not really but its a simply way of explaining it) image of the other 2, so you can increase the speed and the capacity adding redundancy, of course more drives it's better, but you need at least 3 drives to make a raid-5. 
Also a raid-1 could be perfect with 2 drives but you will have only the capacity of 1 disk.

---

### Post by maclenin on 2009-03-27
Thanks, **albandy**!

So, in your mind, does the rest of the proposed configuration - given the way in which I'll be using the server - all seem fine? For you, it's about how to configure the hdds? I.e. to raid or not to raid, that is the remaining question? And, whether I should add another hdd to the mix?

I appreciate the lesson!

---

### Post by albandy on 2009-03-27
If I had to mount that server I'll build a RAID. Now you should think in a hardware RAID or a software RAID.

hw raid it's better but expensive (all it's done by harware and it's transparent for the o.s)
sw raid it's a good option if you've no money to spent in it, but it's more difficult to configure it.

---

### Post by maclenin on 2009-03-27
I'd consider investigating both hw and sw raid options - with a preference, at this stage, for the sw route (from a cost standpoint).... Can you suggest any solid resources / guides for configuring raid? I am willing to climb a steep learning curve....

Thanks, again, for the advice!

---

### Post by tubezninja on 2009-03-27
> **maclenin said:**
> Thanks much, all!

...**scaredpoet**:
...ram: my motherboard choice can support 4gb ram - MAX - would you suggest I spring for a mobo that can handle more ram?

Up to you.  If you can afford it, and plan on keeping this server for a significant period (>3 years) then yes.  


> ...hdds: I will start with 2 x 1tb sata hard drives - with mobo space for a possible 3rd sata - would you suggest 3 x 1tb? Or are you suggesting, for example, 1 x 250bg for "/" and assign the other 2 x 1tb to /home?

1 x 250 for / would be the way I'd go.

---

### Post by maclenin on 2009-03-27
**scaredpoet**:

So...

...you'd upgrade the motherboard to allow for 8mb+ ram?
...you'd also grab a 3rd 250gb drive to supplement the 2 x 1tbs....

How would the partitions look across these three drives?
What would be your back-up plan?
You are not convinced that RAID is, necessarily, the way to go?

Thanks for the help!

---

### Post by maclenin on 2009-04-03
...as for [_**partitions**_]("http://lissot.net/partition/partition-04.html"), I am thinking:

**250gb drive (1 of 3) - sda**
```

/ (50gb) - ext3 - primary - sda1
/home (196gb) - ext3 - primary - sda2
/swap (4gb) - swap - primary - sda3

```

**1tb drive (2 of 3) - sdb**
```

/archive1 (498gb) - ext3 - primary - sdb1
/archive2 (498gb) - ext3 - primary - sdb2
/swap (4gb) - swap - primary - sdb3 

```

**1tb drive (3 of 3) - sdc**
```

/archive3 (498gb) - ext3 - primary - sdc1
/backup (498gb) - ext3 - primary - sdc2
/swap (4gb) - swap - primary - sdc3

```
...my **swap** strategy comes via [_this post_]("http://www.ibm.com/developerworks/linux/library/l-swaptip2.html") and a wee bit of other reading on the matter....

...as for **backup**, I am thinking rsync to /backup with regular burns from /backup to external usb drives....

...as for **file-sharing**, the standards would come into play: nfs, samba, ftp... Perhaps I should create a windows/mac-readable fat partition - or just attach an extra usb drive to allow for backup/sharing for the rare windows/mac visit to the network....

...I am also thinking about resurrecting a recently "retired" windows 2000 environment via [_**virtualbox**_]("http://ubuntuforums.org/showthread.php?t=1114332")....

Thanks for any comments!

---

