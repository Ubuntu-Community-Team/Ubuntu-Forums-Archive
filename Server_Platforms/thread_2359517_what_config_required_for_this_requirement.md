---
title: "what config required for this requirement ?"
date: 2017-04-25
forum: Server Platforms
---

### Post by soamz on 2017-04-25
We are a ISP network with concurrent 3000+ customers, and average speed of a customer is 50Mbps and 100Mbps internet plans. 
Its obvious that customers can never use such high speeds, except doing speedtest at ookla server. 

So, I have a Intel Xeon E31220v3 with 8GB RAM server as my ookla server. 
But I see that, when even 1 customer is doing a speedtest of 100Mbps, no other in the network can do the speedtest as the server usage is full. 

The server has gigabit card, then why a simple 100Mbps transfer is choking the server resources ?

Its running ubuntu server edition 16.xx


So i need to build a new server with 10G card, but not sure, what config I should make if I need to handle concurrent speedtests too of 100Mbps customers.

---

### Post by TheFu on 2017-04-25
I suspect there are other issues.

Are you using quality NICs and quality switches and routers? Pushing 11MB/s (100Mbps) shouldn't stress that box.  Do you have bonded GigE networks?  I doubt you need a new server for a simple bandwidth tool like that.

For system sizing, shouldn't you ask ookla? [https://support.ookla.com/hc/en-us/articles/234577468-NetGauge-Server-Client-Requirements](https://support.ookla.com/hc/en-us/articles/234577468-NetGauge-Server-Client-Requirements) 
How many concurrent tests do you need to support? 
What is the memory requirements for each concurrent user?  
How much CPU does each concurrent test require?

Add all those things up ... see if your current system meets or exceeds it.  I'd be surprised if the current machine couldn't support 9 concurrent tests at 100Mbps - probably 18 with 2 quality GigE NICs that are using off-loaded transfers to limit the CPU requirements.

Does your existing network support 10G connections?

Not enough data to say much more.

---

### Post by soamz on 2017-04-25
Its a dell R220 server with Intel card, I guess. 
So, should not be an issue for the card.

---

