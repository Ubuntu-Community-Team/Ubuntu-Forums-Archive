---
title: "Can i use my Core 2 Duo / 4GB / 160GB / X3100 GPU Laptop as Web Server?"
date: 2009-12-02
forum: Server Platforms
---

### Post by screwmycomputer on 2009-12-02
Hi!
 
I was unable to sell my laptop which i bought for $1000 last year, but now I am thinking om making it to work as a webserver which can handle average amount of users 2000+ / day. Can I use my laptop as a Webserver using Ubuntu? it is an Dell Inspiron 1525.
Specifications:
Intel Core 2 Duo 2.0GHz T7250
4GB RAM 667Mhz
160GB Harddisk
Intel Graphic Media Accelerator X3100
 
Thank you

---

### Post by pi4r0n on 2009-12-02
Laptop spec looks OK and I think it can handle it. With regards to users access(performance) you will have to do some actual tests on this.

Note: Personal I think its achievable task ;).

---

### Post by bsharp on 2009-12-02
Your laptop would be able to handle 2000+ users a day (which is honestly not that much of a load). That works out to about 84 an hour.

The real question is when do you expect those 2000+ users? If it all happens at 12:00PM, you are going to have a problem. If not, you should be fine.

---

### Post by screwmycomputer on 2009-12-02
I dont know, but I am making a Social Networking site which you will later notice when it become a little bit famous (TrueLifeWeb.com) but I expect it will be more and more every day so if there is another specs you want to recommend me?

---

### Post by BkkBonanza on 2009-12-02
Try it and see. No one can really tell you how well it will work because when running a web server there are just so many factors that determine  loading. 

On a side note - if I were making a social site that I thought was going to get big some day I'd build it so it could be transferred to something like Amazon EC2. Good design and it could scale up to huge capacity with no hardware and server hassles.

---

### Post by screwmycomputer on 2009-12-02
But I will use this laptop solution for a short period and when I get more visitors I will upgrade to a quad core if needed?

---

### Post by dnvikram on 2009-12-02
> **screwmycomputer said:**
> Hi!
 
I was unable to sell my laptop which i bought for $1000 last year, but now I am thinking om making it to work as a webserver which can handle average amount of users 2000+ / day. Can I use my laptop as a Webserver using Ubuntu? it is an Dell Inspiron 1525.
Specifications:
Intel Core 2 Duo 2.0GHz T7250
4GB RAM 667Mhz
160GB Harddisk
Intel Graphic Media Accelerator X3100
 
Thank you

It may look good on the paper.But,in reality the scene maybe completely otherwise.My best guess is there maybe real latency due to IO limitations considering that it has a single sata drive assuming its a 5400 rpm and which may translate into spikes in cpu usage.Most of the performance problems are a result of IO and CPU.Consider running the same webserver on a basic workstation with multiple disks in raid and with the same cpu specs,it would be much better.This is just my opinion.

---

### Post by Sporkman on 2009-12-02
> **screwmycomputer said:**
> Hi!
 
I was unable to sell my laptop which i bought for $1000 last year, but now I am thinking om making it to work as a webserver which can handle average amount of users 2000+ / day. Can I use my laptop as a Webserver using Ubuntu? it is an Dell Inspiron 1525.
Specifications:
Intel Core 2 Duo 2.0GHz T7250
4GB RAM 667Mhz
160GB Harddisk
Intel Graphic Media Accelerator X3100
 

When my website was hopping with a flood of traffic from StumbleUpon, it was handling over 10k+ visitors/day, doing processor-intensive image processing. The site was served by a dedicated (single core) Athlon 2K with 256 megs RAM - the machine hardly broke a sweat.

Your core 2 duo with 4 GB RAM can easily handle 100 times your expected usage. :) It'll likely be bandwidth that will be the limiting factor, or perhaps disk drive delays.

---

### Post by Sporkman on 2009-12-02
...as far as disk drive delays, with all that ram you might consider placing your website directory tree on a ramdisk.

---

### Post by BkkBonanza on 2009-12-02
The Linux kernel will cache drive access in RAM by default so I expect little to be gained by a ram disk.

However, if you want a light duty server to handle more trafffic then design your web application with efficiency in mind from the start and really look into running NGinx as your web server instead of Apache. In particular, if you are using AJAX type code where you can expect a higher volume of small server requests, high concurrency, then NGinx is well suited. According to online stats it's now running more than 4% of web sites worldwide, making it third place after Apache and IIS.

Various schemes that utilize caching to convert dynamic content into static will also improve how much you can server from even the least capable boxes. ie. be smarter with less.

---

### Post by holastickboy on 2009-12-02
I am running a website at the moment that gets a few hundred people per day and it does it without a hiccup.  It's running Lampp, e107 as a CMS.  It's running a Celeron 2ghz, 768mb ram, and a 250gb IDE hard drive.  Your Core 2 Duo absolutely leaves my machine in the dust!!!  I agree with those who say that your limiting factor will be bandwidth, but again that depends on how many users you will at the same time.  Luckily for me, the most I have ever had on my site at one time was 10, and it handled it no problems.

---

### Post by munky99999 on 2009-12-02
The only factor I could see it being a problem. Laptop overheating. Get a nice cooling little thing for it. Then you'll be fine.

---

### Post by laceration on 2009-12-02
If I was you I wouldn't be worrying about the specs so much, I'd be worrying about a laptop being on 24/7.  Everything is jammed together in a small space, which makes them run hot and wear out.  Why do people hibernate them, while no one does that w/ desktops?
The issue was discussed here:
[http://ubuntuforums.org/showthread.php?t=658765](http://ubuntuforums.org/showthread.php?t=658765)

---

### Post by Sporkman on 2009-12-02
As far as bandwidth - if you're long on cpu power but short on bandwidth (as you appear to be), you can look into using apache's mod_deflate module, which compresses the outgoing web pages.

---

### Post by holastickboy on 2009-12-02
that's a good point in terms of the whole heat issue.  I must admit all of my laptops get nice and hot when processing things, let alone processing things 24/7.  I have a laptop that is serving media files to my house, but I actually removed the screen, and the top of the case so that the mobo is exposed and air gets through.  Not particularly safe, but keeps it cool until dust plays with it in the future.

---

### Post by BkkBonanza on 2009-12-02
A laptop is not ideally suited to this but what you have is what you have... right?
I assume if you wanted to buy a new server to dedicate to the site then you wouldn't be thinking about using the laptop. It will work for the time being. Neither a laptop nor a non-data-center located net connection are ideal. You could sell the laptop and fund a dedicated server in a data center for around $50-60 /mo. (or a VPS for $10/mo) that would be way ahead in performance and reliability. Or you could use it for now and do the same at some point when the laptop is obviously not adequate. Just keep data backups so if it craps out you can quickly move to a better solution.

I've run a server from home and from a data center. Having one at home is fun at first but anything serious on the net should be done from a data center IMHO.

---

### Post by holastickboy on 2009-12-03
Let us know how you go and what decision you make mate!

---

### Post by M!K3_$ on 2009-12-03
short answer is, yes. But BkkBonaza has a great point. Start off with your laptop, but if you are successful then you can always migrate to something more flexible.

> **BkkBonaza said:**
> On a side note - if I were making a social site that I thought was going to get big some day I'd build it so it could be transferred to something like Amazon EC2. Good design and it could scale up to huge capacity with no hardware and server hassles.

---

