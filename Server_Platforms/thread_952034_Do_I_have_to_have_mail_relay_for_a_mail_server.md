---
title: "Do I have to have mail relay for a mail server?"
date: 2008-10-18
forum: Server Platforms
---

### Post by scott_ttocs46 on 2008-10-18
Hi All,

As it is, I have shared hosting for several domain names. I want to move to an Ubuntu VPS service and manage my own stuff. My primary concern is setting up the mail server.

I have a general idea of how to setup the mail server. My question is: Do I have to have mail relay to send email? 

Some forums say that yes, it is necessary, otherwise your mail will be marked as SPAM. (I don't send any spam.)

Is there anyone who has expertise in this area? I do not want to spend more money than is necessary.

Scott

---

### Post by MJN on 2008-10-18
The ones likely to require a mail relay are those that match one or more of the following:
 
1. Using a dynamic IP address - Many RBLs exist to identify dynamic IPs as used by resedential dialup/broadband customers and hence a common source of spam
2. Using a static IP address but sat within a 'troublesome' netblock - The owner of the netblock may well be 'spammer-friendly' or not proactive with kicking spammers (his customers) of his network and hence some RBLs blacklist the entire netblock taking you with them, innocent or not
3. Not having control of the PTR records for their assigned IP address - An common anti-spam technique involves performing reverse lookups on the connecting IP address and, in some cases, performing a forward lookup on the resulting answer to look for a match. The lack of a reverse lookup and/or matching entries can result in the suspicion of being a spammer
 
If any of the above apply to you you may well need to consider relaying via a 3rd party.
 
Any help?
 
Mathew

---

### Post by rcrcomputing on 2008-10-19
If you have a dynamic ip address from your provider, the answer is yes. While much of you mail may be accepted. You'll have troubles with those that are not. 

With some providers, you have to send thru them regardless..

Is there a problem sending thru your isp's smarthost?  

My provider at home blocks outgoing on port 25, so I have postfix also answer on another port at work. Outgoing mail from home gets sent to work and goes out from there. Just giving you ideas..

---

