---
title: "SSD versus SATA RAID 1 (&amp; server logs)"
date: 2011-06-08
forum: Server Platforms
---

### Post by Dry Lips on 2011-06-08
I'm planning to make a server for a website with static HTML, 
and I need to figure out if I'll use a single SSD disk or whether 
I'll go for a raid1 array of traditional HDDs instead.
 

 The site is going to be rather small, but will a SSD disk of, say, 
16GB be enough for server logs? How much space does logs 
normally take on a server with medium traffic? And is it true 
that SSDs have worse performance on Ubuntu compared to 
Windows? Is it necessary to trim the SSD for better performance
 with Ubuntu 10.04.
 
 And what is most likely to fail, a SSD disk, or a RAID 1 array?

---

### Post by blind2314 on 2011-06-09
> **Dry Lips said:**
> I'm planning to make a server for a website with static HTML, 
and I need to figure out if I'll use a single SSD disk or whether 
I'll go for a raid1 array of traditional HDDs instead.
 
 
The site is going to be rather small, but will a SSD disk of, say, 
16GB be enough for server logs? How much space does logs 
normally take on a server with medium traffic? And is it true 
that SSDs have worse performance on Ubuntu compared to 
Windows? Is it necessary to trim the SSD for better performance
with Ubuntu 10.04.
 
And what is most likely to fail, a SSD disk, or a RAID 1 array?
 
You don't want to write logs to a SSD. SSD's lifespans are limited by their number of writes they can do, before they start failing. If you have hundreds or thousands of logs coming in, that will put a huge strain on the SSD, and most likely cause it to die or fail prematurely.
 
As far as how much space do you need, that's a question that can't really be answered until you get your site up and running and get some averages. Also, keep in mind that depending on how you have your logging setup, you'll run into situations where you get pounded with logs (i.e., someone is probing your site, DDoS, network issues, etc).

---

### Post by Dry Lips on 2011-06-09
Thanks for your reply!

So if you use a SSD in a server, you'll most likely have to have
a separate disk for logs anyway?

---

### Post by MSPdwalt on 2011-06-09
Have you thought about using Amazon Ec2? or maybe S3 depending on the function of your site? aws.amazon.com

---

### Post by Dry Lips on 2011-06-09
> **MSPdwalt said:**
> Have you thought about using Amazon Ec2? or maybe S3 depending on the function of your site? aws.amazon.com

Why rent expensive services when you can have a dedicated server for free?
My site probably won't be that big, at least not at first...

---

### Post by MSPdwalt on 2011-06-09
> **Dry Lips said:**
> Why rent expensive services when you can have a dedicated server for free?
My site probably won't be that big, at least not at first...

My server costs me $1 (USD) a month. I run a small ubuntu 10.04 Granted no one visits my site, but it's cheap, I don't have to buy or care about hardware. And it deploy's and tares down in seconds and it scales like no other. Not to mention that you don't have to worry about your internet going down.

[http://aws.amazon.com/ec2/#pricing](http://aws.amazon.com/ec2/#pricing)

---

### Post by Dry Lips on 2011-06-09
> **MSPdwalt said:**
> My server costs me $1 (USD) a month. I run a small ubuntu 10.04 Granted no one visits my site, but it's cheap, I don't have to buy or care about hardware.

Well, I don't expect to be an Internet superstar overnight, but on the other hand
I do hope to get some traffic after a while, so I think setting up my own box would
be a lot cheaper than signing up for a paid host. (Unless you sign up with someone
that oversell.)
Sure, there are downsides to having your own server, but I think of it
as a stepping stone. If my site becomes insanely popular I would probably
have to move on, but I think I'll be fine at first. But we digress... 

The question is whether or not if using a SSD in a server is off-limits.
It would make the box cooler and quieter, so the question is if the
strain of recording visitors would be too much for it.

---

### Post by Lars Noodén on 2011-06-09
SSD should be fine as far as wear goes nowadays.  

Also the system caches writes and only does them periodically to the disk.  It's not necessary to have a separate disk for logs, but it is a good idea to have a separate partition.  That way if it fills up, it does not block the use of /tmp and /var/tmp, which if blocked will crash your machine.

---

### Post by Dry Lips on 2011-06-09
> **Lars Noodén said:**
> SSD should be fine as far as wear goes nowadays.  

Also the system caches writes and only does them periodically to the disk.  It's not necessary to have a separate disk for logs, but it is a good idea to have a separate partition.  That way if it fills up, it does not block the use of /tmp and /var/tmp, which if blocked will crash your machine.

Thanks Lars!

Is there a mount point that I can use for this? Where do logs normally go?

---

### Post by MSPdwalt on 2011-06-09
> **Dry Lips said:**
> Well, I don't expect to be an Internet superstar overnight, but on the other hand
I do hope to get some traffic after a while, so I think setting up my own box would
be a lot cheaper than signing up for a paid host. (Unless you sign up with someone
that oversell.)

And that's where you miss my point entirely.  What's your budget for this project? $400? Probably more if you're considering SSD.  

There's about 730 hours in a month.  Look at those pennies that they charge for resources used and ask yourself how far your current budget will get you with that?.  Note that you don't pay for anything if your instance is powered off and you're committing to nothing.  Plan your server build, spin up an instance in Ec2 for a month.  Look at your bill, if it sucks blow it away.

Any vm in the amazon cloud will perform on par or better that the server you're about to build.  If you don't believe me try one for a day.  They'll round your cost up to a penny or 2.

---

### Post by Dry Lips on 2011-06-09
> **MSPdwalt said:**
> And that's where you miss my point entirely.  What's your budget for this project? $400? Probably more if you're considering SSD.  

There's about 730 hours in a month.  Look at those pennies that they charge for resources used and ask yourself how far your current budget will get you with that?.  Note that you don't pay for anything if your instance is powered off and you're committing to nothing.  Plan your server build, spin up an instance in Ec2 for a month.  Look at your bill, if it sucks blow it away.

Any vm in the amazon cloud will perform on par or better that the server you're about to build.  If you don't believe me try one for a day.  They'll round your cost up to a penny or 2.
** Amazon Cloud:**
*"Up to 10 TB / month $0.150 per GB"*
  Let's say the site uses becomes quite popular and uses 100 GB a month.  
  That'll be 180$ a year.  
 
 Now, I've already got a box. (AMD Athlon Dual Core, 2GB)
What I need is basically just a HDD. A 16GB SSD costs 54$. 

Let us say the server last for 3 years. That'll be a dedicated 
server for 18$ a year. In addition I won't have to pay a large
 bill if I get unexpectedly much traffic.

Thank you so much for the feedback, but I doubt I'll get
a cheaper solution than DIY hosting, even if there *are*
drawbacks to this.

---

### Post by Grenage on 2011-06-09
> **Dry Lips said:**
> ** Amazon Cloud:**
*"Up to 10 TB / month $0.150 per GB"*
  Let's say the site uses becomes quite popular and uses 100 GB a month.  
  That'll be 180$ a year.  
 
 Now, I've already got a box. (AMD Athlon Dual Core, 2GB)
What I need is basically just a HDD. A 16GB SSD costs 54$. 

Let us say the server last for 3 years. That'll be a dedicated 
server for 18$ a year. In addition I won't have to pay a large
 bill if I get unexpectedly much traffic.

Thank you so much for the feedback, but I doubt I'll get
a cheaper solution than DIY hosting, even if there *are*
drawbacks to this.

What's your power consumption and cost?

---

### Post by Lars Noodén on 2011-06-09
> **Dry Lips said:**
> Thanks Lars!

Is there a mount point that I can use for this? Where do logs normally go?

Yes.  Normally logs go in /var/log so when you are making your system, make /var/log into its own partition.  Play a little bit and then decide how large or small it must be.  Logs are text files and thus rather small.  The log rotater will also compress the old logs, and text compresses well so those files will be small.  

There are merits in hosting, but if your goal is to learn, then having the machine on hand has value, too, even if it is increasing your bill.  After some months when you find you're not changing things anymore, then it might be worth looking at hosting options again.

---

### Post by a2j on 2011-06-09
single ssd will have higher failure rate vs sata raid1.

I don't really think you need ssd on your server... yet.

---

### Post by Lars Noodén on 2011-06-09
> **a2j said:**
> single ssd will have higher failure rate vs sata raid1..

SSD RAID 1 will also be quite sound, though expensive.  I did some quick searching and find that the reliability complaints on SSDs come largely from some rumors published about three years ago.  The [SSD failure rate turned out to be unfounded](http://www.bit-tech.net/news/2008/03/20/1_in_3_ssd_failure_rate_unfounded/1).

---

### Post by Dry Lips on 2011-06-09
> **Grenage said:**
> What's your power consumption and cost?

Minimal; electricity is far cheaper here than in the UK! :)

---

### Post by blind2314 on 2011-06-09
> **Lars Noodén said:**
> SSD RAID 1 will also be quite sound, though expensive. I did some quick searching and find that the reliability complaints on SSDs come largely from some rumors published about three years ago. The [SSD failure rate turned out to be unfounded]("http://www.bit-tech.net/news/2008/03/20/1_in_3_ssd_failure_rate_unfounded/1").
 
 
I agree that is unfounded. However, I wasn't referring to that with my first post. There is still the wear component with SSDs in terms of their writes/life expectancy (This is assuming NAND based solid state drives, which are still the most common I believe. SSDs that are based on DRAM don't have write limitations, but, they aren't commonplace yet, and are far more expensive.); that's simply the nature of the hardware.
 
I'm not saying they will die in a week, or that you shouldn't purchase them; but, for writing and maintaining of logs that have the possibility to come in very frequently, I don't believe they are the optimal choice.

---

### Post by Lars Noodén on 2011-06-09
> **blind2314 said:**
> I agree that is unfounded. However, I wasn't referring to that with my first post. There is still the wear component with SSDs in terms of their writes/life expectancy (This is assuming NAND based solid state drives, which are still the most common I believe. SSDs that are based on DRAM don't have write limitations, but, they aren't commonplace yet, and are far more expensive.); that's simply the nature of the hardware.
 
I'm not saying they will die in a week, or that you shouldn't purchase them; but, for writing and maintaining of logs that have the possibility to come in very frequently, I don't believe they are the optimal choice.

The three systems I've had with SSD drives have all had long warranty periods.  This one has 3-year coverage.  So they are expected to last about as long as old fashion hard drives.

About the number of writes, the logs partition will only get written when the system buffer is cleared, which IIRC is about once every 5 seconds, unless the filesystem is mounted sync instead of the regular async.  So the number of writes is not quite in direct proportion to the activity on the log.

---

