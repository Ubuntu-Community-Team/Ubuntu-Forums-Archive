---
title: "Server Hosting Types and Ubuntu"
date: 2009-10-14
forum: Server Platforms
---

### Post by skunkbad on 2009-10-14
I've ran my own web server using Ubuntu Server Edition 8.04. The server was an old desktop computer, and I managed to run 5 websites on it for about a year.

My question relates to different types of hosting accounts that I see. I don't know what VPS is compared to dedicated. I also see the term cloud used, and I'm looking for a good article about hosting types, and then a recommendation for hosts that are on the West coast of USA. I am in Southern California.

---

### Post by BkkBonanza on 2009-10-14
A VPS is a virtual partition of a dedicated machine. It gives you almost all the same functionality of a dedicated machine but only a portion of the computing/disk resource. If you like the full control of administering a machine as you did with your own Ubuntu server before but don't want to spend the money for a full dedicated box, nor need the full speed, then this is a good option. However, finding a decent VPS provider can sometimes be hit and miss as many will overload their machines with too many partitions. I have used several now and been impressed and disgusted both. As often is the case I would recommend not going with the rock bottom price but with one that appears more solid and reputable. There are so many around now that browsing this forum will give you several good leads. I have found the hosts offering Virtuozzo to be more reliable and a bit more costly in general.

Unless you plan to walk into the offices of your hosting provider there is no need to get one in your local area. It will make no difference for a VPS or dedicated machine. It would be handy if you plan to co-locate, ie. put your own machine in someones data center. As far as cost goes co-location often costs more than dedicated unless you need a souped up computer. With co-location they often charge higher for the bandwidth because unlike other package accounts they expect you may actually use it.

Regarding "cloud computing" I would recommend reading the intro material on the Amazon Web Services (AWS) site. They are pretty much the biggest player in this area and their offerings are substantial. This typically is only suitable if your have a fairly sizable need and/or want to design for rapid escalation of services. It is pretty nice stuff but also much more complicated than just renting a VPS/dedicated machine. I looked at it and tested some things quite a bit and would use it if I were designing the next Smugmug or Youtube. For small sites not expecting huge traffic it isn't cost effective. Using Amazon S3 for backups works very well though and is cheap.

Anyway, hope this helps a bit.

---

### Post by skunkbad on 2009-10-14
Hey, great advice. Thanks for your time.

---

### Post by BkkBonanza on 2009-10-14
When I said "browsing this forum", I was having a senior moment. I meant browsing webhostingtalk.com. The Ubuntu forums are light regarding server info but that forum has heaps of info and is well worth getting aquainted with. They have a board for VPS in particular which can be very helpful in finding hosts and dealing with problems.

---

### Post by skunkbad on 2009-10-14
I will go there and check out what people are saying.

Recently my host was giving me a problem, saying that I am using too much CPU, and in there opinion it was from too much traffic. Yes it is a shared host, but I felt I should be at least able to handle a few hundred visitors a day. They think differently. My thinking is that if I had 200 visitors *an hour* it should be fine, but maybe I am expecting too much.

So, needless to say, I'm looking into options.

Thanks again.

---

### Post by bernied on 2009-10-14
Google 'Linode'

---

### Post by BkkBonanza on 2009-10-15
Yes, I think you're right - even 200 visitors/hour is light, as long as they're just typical page hits and not video/downloads etc. Some shared hosts base their business around the idea that they don't expect you to use anything. When you actually do they want you to upgrade to a "real" package.

For serving multiple client's sites a VPS is a better solution and with a decent host company you should be able to serve a lot more than a few hundred hits/hour. I used KnownHost.com for quite a while and they were very good - probably the best out of a half dozen I've used. They cost a bit more but I always had good speed and it didn't degrade over time as they add more customers; something common with several others I tried. The other thing with a VPS is that you have full root access so you can run background tasks, cronjobs and any special server programs you may want. A lot more control. Security is better since all your sites are completely insulated from any other users on the same physical machine.

---

