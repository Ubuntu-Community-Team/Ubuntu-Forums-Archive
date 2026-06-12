---
title: "Host multiple domains with Virtualmin on Ubuntu VPS"
date: 2012-07-19
forum: Server Platforms
---

### Post by matimont on 2012-07-19
Hi,

I've got a VPS with Ubuntu 12.04 64 bits and installed WebMin & Virtualmin, that's the only thing I did on the server so far.

Now, I would like to host my domains in there (I have about 20) and wondering how. I created the virtual servers but... here's my problem. My VPS provider doesn't give me DNS to use, so in short words, I can't point my domains to a ns1.something.com and ns2.something.com....

What you suggest here? Do I get a new domain name with namecheap for example and set that as DNS pointing to my VPS so that I can later use it as ns1 and ns2 for my other domains I want to host? (Please let me know if my understaning of DNS is correct)..

I've read I could also set up my VPS to act as DNS server, but I don't want to get into that, it sounds like too much work...

Thank you for your suggestions!

Matias.

---

### Post by BkkBonanza on 2012-07-19
It sounds like your DNS understanding isn't quite right. When you register a domain name it will by default have a DNS server for you (most registrars provide this). Those would be your ns1 and ns2 domain servers. You don't need to alter that at all in order to serve your site on a VPS. 

What you need to do is update the DNS records on the current DNS server to have an "A record" that points to the IP of your web server. You may also want CNAME records that act as aliases for some subdomains that should point to the same as your A record. eg. mydomain.com could have an A record and [www.mydomain.com](www.mydomain.com) could have a CNAME that points to mydomain.com

Once you have those records entered in the DNS server (wherever it is, whether on your own server or at any third party) then your virtual server configs should work. 

You would only change the ns1 and ns2 IP values if you want to move your DNS server from the default your registrar provides. eg. to run your own DNS server or to have your DNS provided by zoneedit.com, for example.

---

### Post by matimont on 2012-07-19
Thank you, now the domains I have are all ".com.ar" and my registar doesn't provide DNS for these, that is, they just give me the domain name (eg: www.something.com.ar" and I need to delegate that domain to a ns1 and ns2 in order to have them working somewhere. In the current shared hosting I have, it's easy, because I just delegate my domains to ns1.mysharedhostingservernameserver.com and ns2 as well.

My new VPS doesn't have ns1 and ns2 I could use, so I'm trying to figure out the way to use a ns1 and ns2 to point my domains to..

What should I do in that case?

Thanks you!

---

### Post by BkkBonanza on 2012-07-19
In this case you need a DNS server. It doesn't have to be on your VPS but you need one somewhere. There are a few free DNS providers out there. I've used zoneedit.com in the past (long time ago, and I think they're no longer free). I've also used sitelutions.com (pretty good, fast, free but a bit cumbersome). There are also non-free ones.

Whichever one you use you would sign-up/register with them, add the DNS records for your domain. And then update your registrar to have their ns1 and ns2 IP values. 

If you do choose to run a DNS server on your VPS I would seriously look at tinydns. It's a package on Ubuntu and is much lighter resource wise than Bind. But to do it properly yourself you really should have two independent servers (and IPs) for redundancy. That's why I'd recommend just using some free DNS provider over the hassle of setting up your own.

Also sometimes VPS providers will host a DNS server for it's users but they don't always publicise it much. It may be worth asking.

---

### Post by sandyd on 2012-07-19
> **BkkBonanza said:**
> In this case you need a DNS server. It doesn't have to be on your VPS but you need one somewhere. There are a few free DNS providers out there. I've used zoneedit.com in the past (long time ago, and I think they're no longer free). I've also used sitelutions.com (pretty good, fast, free but a bit cumbersome). There are also non-free ones.

Whichever one you use you would sign-up/register with them, add the DNS records for your domain. And then update your registrar to have their ns1 and ns2 IP values. 

If you do choose to run a DNS server on your VPS I would seriously look at tinydns. It's a package on Ubuntu and is much lighter resource wise than Bind. But to do it properly yourself you really should have two independent servers (and IPs) for redundancy. That's why I'd recommend just using some free DNS provider over the hassle of setting up your own.

Also sometimes VPS providers will host a DNS server for it's users but they don't always publicise it much. It may be worth asking.

A few DNS Services to look for

[Amazon AWS Route 53]("http://aws.amazon.com/route53/pricing/") - 50c/domain, 50c/million queries (this is actually hard to pass, it almost never goes over a million queries for me). Its never been offline, and has been extremely stable for me.
[Freedns.afraid.org]("http://freedns.afraid.org") - sometimes gets hit by DDOS attacks, .etc .etc, some downtime
[Namecheap DNS]("http://www.namecheap.com/products/freedns.aspx") - Free, quite popular, very little downtime
[Hurricane Electric DNS]("http://dns.he.net") - Hurricane Electric occasionally gets hit with DDOS attacks at its fremont locations, due to the fact that they provide cheap bandwidth, and their hardware(brocade) is incapable of handling DDOS attacks. Sometimes has congested pipes as well, which may affect the reachability of the DNS servers.

---

### Post by matimont on 2012-07-20
> **sandyd said:**
> A few DNS Services to look for

[Amazon AWS Route 53]("http://aws.amazon.com/route53/pricing/") - 50c/domain, 50c/million queries (this is actually hard to pass, it almost never goes over a million queries for me). Its never been offline, and has been extremely stable for me.
[Freedns.afraid.org]("http://freedns.afraid.org") - sometimes gets hit by DDOS attacks, .etc .etc, some downtime
[Namecheap DNS]("http://www.namecheap.com/products/freedns.aspx") - Free, quite popular, very little downtime
[Hurricane Electric DNS]("http://dns.he.net") - Hurricane Electric occasionally gets hit with DDOS attacks at its fremont locations, due to the fact that they provide cheap bandwidth, and their hardware(brocade) is incapable of handling DDOS attacks. Sometimes has congested pipes as well, which may affect the reachability of the DNS servers.

Thanks, I opened an account with namecheap and added one of my domains there to test.

Now, I've got Virtualmin Installed, do I just create the virtual server for the domain I will test? that's it?

thank you!

---

### Post by BkkBonanza on 2012-07-20
Do a DNS query on the your domain using eg. nslookup or dig, or online service. If it resolves to your IP then you're ready to create a virtual server and go.

---

### Post by matimont on 2012-07-20
Works! thanks, that sitelutions service is fast!

Ok, now here's my next challenge, I can't send mails outside my VPS server, I inistalled roundcube and I can send mails within the same domain, for example: [EMAIL="domain@domain.com"]domain@domain.com[/EMAIL] but when I attempt to send an email outside it returns this:

 host mx2.hotmail.com[65.55.37.120] said: 550 DY-001     (COL0-MC4-F20) Unfortunately, messages from (myVPSIP) weren't sent.     Please contact your Internet service provider. You can tell them that     Hotmail does not relay dynamically-assigned IP ranges. You can also refer     your provider to [http://mail.live.com/mail/troubleshooting.aspx#errors](http://mail.live.com/mail/troubleshooting.aspx#errors). (in     reply to MAIL FROM command)

I tested and got this:
    Attempting to retrieve DNS MX records for domain (mydomain.com.ar)
     ExRCA wasn't able to retrieve MX records from DNS.

Is it that I need to configure MX records as well in sitelutions?

---

### Post by sandyd on 2012-07-20
> **matimont said:**
> Works! thanks, that sitelutions service is fast!

Ok, now here's my next challenge, I can't send mails outside my VPS server, I inistalled roundcube and I can send mails within the same domain, for example: [EMAIL="domain@domain.com"]domain@domain.com[/EMAIL] but when I attempt to send an email outside it returns this:

 host mx2.hotmail.com[65.55.37.120] said: 550 DY-001     (COL0-MC4-F20) Unfortunately, messages from (myVPSIP) weren't sent.     Please contact your Internet service provider. You can tell them that     Hotmail does not relay dynamically-assigned IP ranges. You can also refer     your provider to [http://mail.live.com/mail/troubleshooting.aspx#errors](http://mail.live.com/mail/troubleshooting.aspx#errors). (in     reply to MAIL FROM command)

I tested and got this:
    Attempting to retrieve DNS MX records for domain (mydomain.com.ar)
     ExRCA wasn't able to retrieve MX records from DNS.

Is it that I need to configure MX records as well in sitelutions?
what you using for mail?
windows live domains?

---

### Post by matimont on 2012-07-20
I figured how to do it, now I'm getting something strange...


Whenever I want to send an email to hotmail I get this (xx.xx.xx.xx is my ip address)
  host mx2.hotmail.com[65.54.188.110] said: 550 DY-001     (BAY0-MC3-F6)  Unfortunately, messages from xx.xx.xx.xx weren't sent.     Please  contact your Internet service provider. You can tell them that      Hotmail does not relay dynamically-assigned IP ranges. You can also  refer     your provider to [http://mail.live.com/mail/troubleshooting.aspx#errors](http://mail.live.com/mail/troubleshooting.aspx#errors). (in     reply to MAIL FROM command)
  

What may be the reason? I can receive mails ok and send to gmail for example with no issues...


When I went to mxtoolbox, I checked with the backlist and all are ok..
  Now, I ran a SMTP check and got this: "Reverse DNS FAILED! This is a problem"
  I think there's some setting I need to configure in Webmin or Virtualmin?

---

### Post by BkkBonanza on 2012-07-20
"Reverse DNS" is a record that allows someone to look up your IP and get back your domain name. ie. reverse of normal DNS. Usually you have to configure it with whoever allocates your IP. Some hosting/VPS providers offer to do this for you (as they should) and some have a control panel where you can do it yourself. If they don't have either then you won't be able to set up that record. Contact your VPS provider. Also, if you have a shared (or dynamic) IP it usually can't be done.

Another thing you should look at for mail setup is adding an spf record to your DNS. Some mail relays will want to check that but I don't know about hotmail specifically. See [wiki]("http://en.wikipedia.org/wiki/Sender_Policy_Framework") but also there are a few sites that can create the record to paste into your DNS. Google: "spf dns record" (it's very easy to do).

Judging by the hotmail message they seem to think your assigned IP is in a dynamic block, ie. belongs to a ISP that usually provides home connections. They block that as typically email from home IPs is more likely spam. I don't know who your hosting provider is but if hotmail doesn't like your IP for this reason you may end up having to move, depending on how important sending mail to hotmail is.

Another possible solution would be using an email proxy or forwarder but I'm not sure about how that would work out. Check the sitelutions info as they may offer some email forwarding option that would allow your email to appear to come from a good IP range.

---

### Post by matimont on 2012-07-21
Thank you,

I did paste a spf record to my domain and still failing, so I'm now sure it's the reverse DNS... I won't be able to send to hotmail until my provider decides to move forward with reverse DNS...

My provider is HP Cloud, they're in Beta status right now, so I hope someday they will allow me to sue reverse DNS on my public IP..

Meanwhile I'll stay with my previous hosting provider for email and use my Cloud system for hosting the domain.. If I don't change the MX records will I still be able to receive mails on my previous provider?

thanks,

Matias.

---

### Post by BkkBonanza on 2012-07-21
There's should be no problem with DNS records that point to different providers. As long as your MX records correctly point to a working server then I'd expect it will be fine.

---

