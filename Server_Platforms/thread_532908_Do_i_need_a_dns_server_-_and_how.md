---
title: "Do i need a dns server - and how?"
date: 2007-08-23
forum: Server Platforms
---

### Post by switch2linux on 2007-08-23
:confused:
Hello helpers!

Ok this is the problem - DNS - always a thorn in my side!

This is my setup - home server running 7.04 server, runnin mysql,apache2,axigen mail server. 
All functions are working perfectly on the internet but DNS is not good according to dnsstuff.com - regarding stealth and missing things etc - fail and more fail.

I have a domain name switch2linux.co.uk that at present is with 123-reg.co.uk - I have told my control panel there to point the www to my external ip address of my mail server which is static through BT. 
so [www.switch2linux.co.uk](www.switch2linux.co.uk) points to 81.138.92.145 
I have set my server up as server1
I have told my MX on the control panel at 123-reg to MX 10 server1.switch2linux.co.uk
I am using 123-reg to be my name servers: ns.123-reg.co.uk and ns2.123-reg.co.uk - but not sure if i need to change that.

I would like to know the process that needs being done to fix my dns problems..... from server - throught to the 123-reg control panel and dns settings.

Mail works perfectly, so does the www, but i still get bad results on dnsstuff.com - have a look and see.....
please help.

thanks

---

### Post by rickyjones on 2007-08-23
No, you don't need to run a DNS server.

As long as mail and web traffic comes and goes just fine then you should be OK.

Most of the problems I see from DNSREPORT.COM have to due with the company that his running DNS for you. They need to get their act together it looks like.

It should work fine, just not as *perfect* as it could. I see three options:

1) Do nothing - it should continue working as it is right now.
2) Host your own DNS - this is usually a lot of work and will probably put you in a worse place than doing nothing.
3) Switch to a new registrar and see if they are better at DNS hosting than your current host.

Hope this clears it up for you!

-Richard

---

### Post by koenn on 2007-08-23
I can resolve your www and server1 address, and get an MX record for your mail domain, so I'd say it's working : if I wanted to browse your website or send mail @switch2linux.co.uk, I'd be able to - DNS-wise. 


```

;; ANSWER SECTION:
www.switch2linux.co.uk. 86400   IN      A       81.138.92.145

;; ANSWER SECTION:
switch2linux.co.uk.     86400   IN      MX      10 server1.switch2linux.co.uk.

;; ANSWER SECTION:
server1.switch2linux.co.uk. 86400 IN    A       81.138.92.145


```

As rickyjones says, the "problems"  you get from DNSREPORT.COM  should be dealt with by your DNS provider. 
They only tyhing it'l look into are the reverse lookup entries - if the control panel lets you set PTR (pointer, reverse lookup) entries, you could add one for 81.138.92.145 --> server1.switch2linux.co.uk

You could try and find an other DNS hoster - no need to register your domain name again - just find a provider to host the DNS records for you on their servers. Probably your ISP can do this (for free or peanuts)

---

### Post by Mr. C. on 2007-08-24
Let me elaborate on what's already been stated.  Many mail servers will reject your email if your forward and reverse DNS records do not match.

Generally it is not your registrar/DNS provider who has control over your PTR records.  It is typically your ISP, or their carrier.  You will have to contact your ISP to see if they will create a PTR record for your MX.

MrC

---

