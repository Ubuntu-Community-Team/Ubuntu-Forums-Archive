---
title: "Recommended Webserver Requirements"
date: 2010-03-18
forum: Server Platforms
---

### Post by lateralus-paradox on 2010-03-18
Hi. I was wondering if there are any minimum requirements that a computer should have before turning it into a ubuntu server 9.10 based webserver. 
 
Minimum ram, cpu, internet connection, video, and other things needed for webserver hosting. A basic/general estimate is fine.
 
Thanks much.

---

### Post by jrssystemsnet on 2010-03-18
Entirely depends on how much traffic you expect the box to get, and how "heavy" the web applications you expect to be running.

A simple Apache box serving a few relatively static sites to a few people per day might get by with the oldest junk CPU you could scrape up off of eBay and 256MB; on the other hand a Mediawiki serving a few thousand people per day would require QUITE a lot more.

For reference, I'm running a Mediawiki site that gets about 10,000 unique visitors per month on an AMD Phenom triple-core box with 2GB of RAM and a single relatively modern SATA hard drive, and last year I was running the same site on an old Pentium 4 2.8 box with 1GB and a PATA hard drive.  It's significantly faster on the newer hardware, but it ran pretty reasonably on the older hardware.

If you're looking at SERIOUS traffic - ie, thousands of uniques per hour, not per week or per month, and on a heavily dynamic site - then the requirements will start getting a lot (a **LOT**) steeper.

---

### Post by dudumomo on 2010-03-18
Yes indeed, it depends on your needs.
What your server will be for ?

---

### Post by lateralus-paradox on 2010-03-18
My friend's dad just started up a restraunt and we said that we could host a website for the bowling ally portion of it. Probably won't expect more than about 50-100 per day for the first few months. Over time as the business grows probably could expect to see as much as 500 per day.
 
It'll only be running one static IP, for the bowling ally/restraunt site, and set up like a standard browsing web page.
 
Thanks again.

---

### Post by Kiwi76 on 2010-03-19
Pretty much anything that will run Ubuntu would run that, but it's best to expect for more. How much is the budget set for for a server (or do you ask with a certain possible existing PC in mind)?

---

### Post by dudumomo on 2010-03-19
If it is just for a simple website, 500/day shoudn't stress that much computer.
Depending on your budget, you can choose different components.
But I will say, 1gb RAM is far enough (But this doesn't cost that much), an ATOM CPU will do just fine, an integrated video card will be enough (As you don't really need one) but I will say, you may need 2 hard drives for safety reasons (In RAID1) and may be do sometimes a complete backup on external hard drive (Some people do that)

But for your connection, I guess you want to be self-hosted ? So you will be limited by the upload.
(The download is usually not a problem)

But a spare PC might also do the trick. ;)

---

