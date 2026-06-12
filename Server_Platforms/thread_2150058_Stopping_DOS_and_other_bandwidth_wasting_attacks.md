---
title: "Stopping DOS and other bandwidth wasting attacks?"
date: 2013-05-30
forum: Server Platforms
---

### Post by Rossithecat on 2013-05-30
Hi everyone.

I am probably going to install and run Ubuntu 12 LTS so these questions are pointed towards it.

I am new to Ubuntu server and I am trying to find out if there is a way to prevent excess bandwidth usage from unwanted visitors so I am not billed for using more bandwidth than I planned.


Is there anyway that I could prevent outsiders using my bandwidth and costing me money?


For example I thought I could shut down everything that is 'public' accessible services like Apache, etc.

Would this prevent using bandwidth from DOS attacks, etc.?

How could an outsider attack use up my bandwidth if I have everything turned off?

I would rather temporarily shut everything down than have to pay additional bandwidth fees.

How should I shut everything down?

sudo kill processes?


Thank you.

---

### Post by sandyd on 2013-05-30
> **Rossithecat said:**
> Hi everyone.

I am probably going to install and run Ubuntu 12 LTS so these questions are pointed towards it.

I am new to Ubuntu server and I am trying to find out if there is a way to prevent excess bandwidth usage from unwanted visitors so I am not billed for using more bandwidth than I planned.


Is there anyway that I could prevent outsiders using my bandwidth and costing me money?


For example I thought I could shut down everything that is 'public' accessible services like Apache, etc.

Would this prevent using bandwidth from DOS attacks, etc.?

How could an outsider attack use up my bandwidth if I have everything turned off?

I would rather temporarily shut everything down than have to pay additional bandwidth fees.

How should I shut everything down?

sudo kill processes?


Thank you.

Where are you running from?
If you are running from home, the server is not accessible until you port-forward ports in your router.

Also, even if you shutdown everything, DOS attacks will still use bandwidth. Use something like cloudflare/staminus/etc if you are expecting DDOS attacks.

If you dont want people accessing your server publicly,  take a look at the default linux firewall called IPTables

---

### Post by Rossithecat on 2013-05-30
> **sandyd said:**
> Where are you running from?
If you are running from home, the server is not accessible until you port-forward ports in your router.

Also, even if you shutdown everything, DOS attacks will still use bandwidth. Use something like cloudflare/staminus/etc if you are expecting DDOS attacks.

If you dont want people accessing your server publicly,  take a look at the default linux firewall called IPTables

Hi thanks for the reply.

No I won't be hosting from home.

This is for a paid hosting plan and they charge a lot for going over the bandwidth amount provided.

The plan is yes the server will normally be accessed publicly but in the event of a hack attack / DOS attack I need to know how to cut the server off from the public to not exceed my bandwidth amount.

Does it sound like IPTables will do this? 

I will have to read up on that!

Thanks.

---

### Post by sandyd on 2013-05-30
IPTables will not stop a DDOS attack.
The only things that will are (general list)
a) DDOS protection (offered at some dedicated server providers such as Staminus, Black Lotus/etc). Includes GRE/Reverse proxy solutions such as JavaPipe and Black Lotus. Also includes CloudFlare. The last two (GRE/Reverse Proxy/Cloudflare) assume that you havent already made your IP Address public knowledge, because they are filtering the data, and then passing it on to your public ip or BGP session.
b) Disconnecting the server
c) Nullrouting the ip
d) Upstream filtering (if its a few ips that are attacking)

---

### Post by HermanAB on 2013-05-31
It is true that you cannot stop a Distributed DOS on the targeted machine, but it is not something that you should worry about much.  An ordinary DOS or brute force password guessing attack is more common and those you can control with iptables rate limiting rules and that should keep your server within the bandwidth budget.

For example:
[http://www.aeronetworks.ca/2013/05/ssh-brute-force-attacks.html](http://www.aeronetworks.ca/2013/05/ssh-brute-force-attacks.html)

---

### Post by SeijiSensei on 2013-06-01
I've run Linux servers on the Internet for over fifteen years and have never been the target of a DOS attack. Why do you think you will be so targeted?  I find the level of paranoia about these things unwarranted in real-life settings. 

If, for some strange reason, you do find yourself under attack, the first thing to do is to speak with your ISP and see if you can work out some type of upstream filtering.

---

