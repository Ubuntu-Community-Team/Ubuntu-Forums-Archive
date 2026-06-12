---
title: "Questions about fail2ban"
date: 2019-09-25
forum: Security
---

### Post by rogerk03 on 2019-09-25
Hi All,

First time post, I'm not a security expert, but have used Linux for several years, please be patient.  I've setup a new VPS running Ubuntu 18.10, and setup fail2ban (v0.10.2).  The system works well, lots of IPs being banned, almost every minute or so.

I have a few questions about fail2ban and wondering if any one may know the answer:

1. Why do people set the ban time to <24 hours?  I've set mine at -1, which the docs indicates is forever.  My server hosts an application for only a small set of IPs (not a public website for example) so I dont see a reason to ever let hackers try again.  Is this the right approach?

2. Over time a lot of IPs are being banned, which is good, the system works, however over time the number of firewall rules are increasing, many hundreds now, thousands per month.  I read somewhere this will eventually slow down the firewall and cause all requests to be very slow.  Is this true?  If so, is there a way to prevent it?

3. Because my server only hosts applications for a small number of known clients, I'm thinking I may be better off simply white listing those IPs at the firewall, and banning everyone else.  Would this approach have any side effects I'm not factoring in?

Thanks for reading.

---

### Post by uRock on 2019-09-25
Hello and welcome!

Be aware that 18.10 is EOL The only non-LTS currently supported is 19.04.

1. They are usually set to 24 hours just in case it was an accidental failed login. Sometimes legitimate users make mistakes and 24 hours gives them time to figure out what they're doing wrong.

2. Not sure about this as I have no public facing servers to get enough entries to matter.

3. If you know all of the IPs that are going to connect and they aren't being leased and subject to change, then adding ACL or firewall rules to allow those IPs and deny all others could be easier to maintain. I'd keep fail2ban in place just in case one of those allowed devices becomes infected and tries to connect or is spoofed.

I have not maintained any servers commercially, so I am sure someone else will come along with more in depth explanations.

---

### Post by TheFu on 2019-10-01
> **rogerk03 said:**
> Hi All,

First time post, I'm not a security expert, but have used Linux for several years, please be patient.  I've setup a new VPS running Ubuntu 18.10, and setup fail2ban (v0.10.2).  The system works well, lots of IPs being banned, almost every minute or so.

I have a few questions about fail2ban and wondering if any one may know the answer:

Servers should always run LTS releases. The current LTS is 18.04.  It is fine to run non-LTS releases for testing, perhaps a week at a time, just to be clear about the lacking support and not-so-great server stability.  Non-LTS releases are where Canonical tries out new things. The last 8 yrs or so, some of those trials have crashed and burned, IMHO.  

18.10 lost support in June, I think.  Your system is at risk from at least 1 remote attack that has been fixed since then.  Don't run non-supported releases on any network.  If you like, you can run them off-line.

> **rogerk03 said:**
> 
1. Why do people set the ban time to <24 hours?  I've set mine at -1, which the docs indicates is forever.  My server hosts an application for only a small set of IPs (not a public website for example) so I dont see a reason to ever let hackers try again.  Is this the right approach?
If you keep them forever, you'll have thousands of firewall rules left over for systems that will never be used again to launch any attacks. It will easily grow to hundreds of thousands.  The vast majority of attacks I see on my servers come from 3 countries that we will never have business contracts with, so why allow any access? Block those countries as best we can, using huge subnet rules.  Thousands of rules take up RAM and processing.

> **rogerk03 said:**
> 
2. Over time a lot of IPs are being banned, which is good, the system works, however over time the number of firewall rules are increasing, many hundreds now, thousands per month.  I read somewhere this will eventually slow down the firewall and cause all requests to be very slow.  Is this true?  If so, is there a way to prevent it?

Block using large subnets and using ipset.  A single ipset rule can block millions of subnets efficiently.

> **rogerk03 said:**
> 
3. Because my server only hosts applications for a small number of known clients, I'm thinking I may be better off simply white listing those IPs at the firewall, and banning everyone else.  Would this approach have any side effects I'm not factoring in?
Thanks for reading.

Definitely white list, but you'll need to discuss this with the clients or have a redirection to a page which explains what you are doing.  Clients often will travel and want to make orders 1-2 days before returning home from foreign locations.  If you are clear why you want to limit them to their work subnet only and they have VPN access to their office, it shouldn't be bad.  I do that for some services.  Everywhere is blocked except about 5 client subnets.

There is no 100% perfect answer, just the answer we can implement based on our current skills and time available.

BTW, you didn't mention what service is being attacked. There are different solutions based on the service.  For example, ssh doesn't need to be on 22/tcp for the WAN.  Just by moving that to some high port, you'll see the attacks drop to near zero.
If you are using plain FTP, stop it.
If you are using HTTPS, there are reverse proxies which can block harmful attempts while allowing full access to needed clients.
If you are allowing direct DBMS access - STOP IT!

---

