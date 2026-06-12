---
title: "When do you know when load is too great?"
date: 2010-05-26
forum: Server Platforms
---

### Post by R.Bucky on 2010-05-26
How do you know when your server load is too much? 

My home server is currently configured for 21 domains, which receive around than 1500-2000 hits per day with approximately 160 processes. Well over half of the domains are simply redirects to domains that I have purchased over the last couple of years... Much of the load is for my internal projects hosting such as Piwik, Munin, Jinzora (streaming my music), Bind9, DHCP, VPN, bookmarks manager, and others. 
Page loads are not slow and all is happy. This is more of a pre-emptive strike! So, how to know when load average is nearing the tipping point?
SERVER SPECS
Ubuntu 8.04 ext3
Server load averages are typically 0.40 averaged over 5 minutes. RAM usage never exceeds 700MB/4000MB
Xeon 3200 series CPU
RAID1

---

### Post by iponeverything on 2010-05-26
Xeon 3200 series is quad core cpu. 

1.0 on a single core cpu represents 100% utilization. As long as this load is not sustained -- it is not a big deal. Note that loads can exceed 1.0 this just means that processes have to wait longer for cpu a slice. 

4.0 on quad core represents 100% utilization..
Anything under a 4.0 load average for a quad-core xeon is ok.

Ideally, I would say that a sustained load average of 3.0 or under on your machine would be very good as I have had quad cores servers running at over 3.0 every day during peak usage -- that had no perceptible slowdown. 

.4 is nothing for you.

---

### Post by R.Bucky on 2010-05-26
Excellent explanation. I published the explanation on my blog as well. I appreciate the response. [http://rbucky.com/blog/understanding-server-load-averages/]("http://rbucky.com/blog/understanding-server-load-averages/")

---

### Post by iponeverything on 2010-05-26
My explanation is somewhat simplistic, there are a number other factors involved that will affect how a given machine will behave at given load average - memory speed and specifics of cpu architecture etc. A new i7 with 4 Cores / 8 threads with its tighter core integration, would probably have the same feel at a load of 6 as the xeon would have at a load of 4.. I am always amazed at the speed of cpu evolution.

---

