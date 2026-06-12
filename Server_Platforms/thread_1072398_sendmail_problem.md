---
title: "sendmail problem"
date: 2009-02-17
forum: Server Platforms
---

### Post by recklessray on 2009-02-17
hi there,

i'd be really grateful if anyone could shed some light on this problem...

i am a sys admin in a secondary school in bristol uk. we 'rent' a proxy / email / firewall / adsl gateway box that is inty.ourdomain.com on 10.0.1.9 / 16

I can look at config in inty via webmin and can see it uses sendmail for email. I can also telnet to port 25 from inside the network.

I, in my ever increasing quest to bring open source solutions to our cash strapped school (!), have set up an ubuntu 8.04 server to use as an internal web application server. I installed apache2 and php5 and got joomla , meeting room booking software and others working fine. 

Now i'm working on an implementaion of MANTIS, the bug tracking sware. It's working fine, except for the email. if i join mantis with an external email address eg [email]me@gmail.com[/email] then it fires an email off no problem. but any emails destined for [email]someone@ourdomain.com[/email] it gets stuck in the sendmail queue and returns a 'no route to host' error. ive duely edited the /etc/hosts file to include inty.ourdomain.com and this made no difference. 

im new to email config, and im probably doing something quite stupid, so be gentle with me! any comments, pointers, questions or solutions very welcome!

thanks.

ray

---

### Post by AndyMcCall on 2009-02-17
What is your acutal domain? Is it a real Internet domain with DNS and MX records?  I am guessing its not which is whats causing you problems.

I *think* that your Ubuntu box is doing lookups for your domain and as it doesn't exist (or if it does exist there are no MX records for it) so it can't find a host to send them to.

There are a few ways of fixing this.  You could install BIND and make it authoritive for your internal domain, then forward requests it can't answer to your existing DNS server and add your DNS records (A,MX and CNAME's etc) for your internal network here.

Or you could buy (or fix if it is a real domain) your external DNS records by adding an an MX record for your domain to it.

You could already have an internal DNS server and duplicated the domain naming space from your ISP on your internal DNS server, and not added your MX records, which would have the same symptoms.

Hope that helps.

---

### Post by recklessray on 2009-02-17
thaks andy,

like i said, im new to email admin, so ill just go and wiki some of the terms you stated!  i think its the later problem tho. the internal domain is called the same name as the website domain something.bristol.sch.uk so ill investigate this further and post any results in this thread.

thanks again o/

ray

---

### Post by recklessray on 2009-02-17
ive just done an mx record lookup for my school email address and it returns a server out there on the web, so our email gateway box must use that (i guess). how would i tell the internal ubuntu box about this?  by the way - the 'actual domain' is colstonsgirls.bristol.sch.uk

---

### Post by AndyMcCall on 2009-02-17
If your on a sch.uk domain then your local council's IT department probably run the DNS servers or will know exactly what your problem is and who you need to contact - if not they will probably be able to help.

If they have a service desk or helpdesk then log a call with them and they may be able to help you.

I help look after all the oldham.sch.uk domains and if you were one of our domains we might not be able to fix the Ubuntu box directly, but we would tell you exactly who you need to contact and who you should call.

You probably just need MX records entering on your DNS server.  If whoever runs the DNS server won't add them, ask for a copy of your Zone file and set up your own authoritive DNS server and duplicate everything in the Zone file adding your MX records as you go.  The only issue there is if they change or add records you need to know about it to add or change them in your DNS server.

Good luck!

---

### Post by recklessray on 2009-02-18
it was a DNS problem. Thanks for all the advice. 

/etc/resolve.conf had both our DCs listed as DNS. I deleted them and put the ISP's DNS IP addresses in there instead and entered the other servers IP addresses in /etc/hosts. There may be implications on using external DNS servers; I've checked the other systems and it all seems to be working ok.:popcorn:

Restarted sendmail and it worked like a charm :)

All the best,

Ray

---

### Post by AndyMcCall on 2009-02-18
The issues you will crop into are that you won't be able to resolve any of your internal servers by hostname :-/

You might be best trying to enter the MX record into your internal domain.  This will mean anything on your local school network that needs MX records will then work with no issues.

You just need to add these MX records to your internal Windows domain:

```
colstonsgirls.bristol.sch.uk. 3600 IN	MX	20 mx2.maildefender.net.
colstonsgirls.bristol.sch.uk. 3600 IN	MX	30 mx3.maildefender.net.
colstonsgirls.bristol.sch.uk. 3600 IN	MX	40 mx4.maildefender.net.
colstonsgirls.bristol.sch.uk. 3600 IN	MX	50 mx5.maildefender.net.
colstonsgirls.bristol.sch.uk. 3600 IN	MX	10 mx1.maildefender.net.
```

And point you server back to your internal DNS.

---

### Post by recklessray on 2009-02-20
yup, did that, reverted back to internal DNS IP address' in /etc/resolv.conf. still not resolving internal names for unknown reason, but mail is working a treat. thanks skipper!

ray

---

