---
title: "Bind9/IIS question"
date: 2006-12-21
forum: Server Platforms
---

### Post by LightShear on 2006-12-21
Hey all,

My situation is that I work for a company who hosts websites. We use zone edit to take care of the DNS stuff. The other day, some of zone edit's servers went down, thus we had a ton of problems. My boss wants a DNS server in-house now, and I'm trying to convince him to go with Ubuntu. My question is, since all these websites are on a windows machine, using IIS, how do I get Bind9 to look at that windows machine?

Thanks.

---

### Post by kidders on 2006-12-21
Hi there,

Your question is a little strange ... Bind's job is to turn hostnames into IPs and vice versa, based on the contents of its own config files. It doesn't need to be able to access (look at?) the addresses it knows about.

Basically, your IIS box shouldn't care how remote hosts figure out where it is ... so what kind of DNS service you're using is irrelevant. If you intend to make your in-house DNS service publicly accessible though, you *will* need to make sure it's fairly resistant to DoS attacks.

---

### Post by LightShear on 2006-12-21
DoS attacks are the least of my worry at the moment :)

Thanks for the reply... I know I have a strange way of describing my strange and sometimes unfounded questions. So basically I need the dns server (let's say 10.0.0.53) to associate mysite.com to the IIS box's internal IP (let's say 10.0.0.54) or the external IP(let's say 123.123.123.123)? 

Thanks for your help!

---

### Post by kidders on 2006-12-21
Hmmm... Most DNS servers only resolve hosts that live within their own address space. That is to say it would be weird for the same DNS service to resolve addresses in the 10.0.0.0/8 range, *and* public IPs as well. There would, for instance, be no way for the server to know whether to answer 123.123.123.123 or 10.0.0.54 to a request for [www.youriisbox.com](www.youriisbox.com).

Presumably, you already have a DNS service running on your network for internal purposes ... the new development is that your boss now wants to take control of DNS resolution for the whole world. To do this, you would need to run, say, two additional DNS servers, both of which are externally accessible, and have no knowledge of your private (10.0.0.0/8) address space. Then, you'd need to get in touch with the company you bought your .com from and have them amend your nameserver records to point to your new DNS servers. The changes would then take a few days to propagate throughout the global DNS system.

If you really are only running a single web server, it would be an awful lot of trouble to go to, which is why most people in your position prefer to opt for a third party DNS resolution service. The other advantage of course is that a third party DNS server will stay up, even when your own network goes down. (This is important.)

> DoS attacks are the least of my worry at the momentDNS servers are terribly prone to attack ... you really need to be _sure_ that yours are able to resist interference. As a "for instance", consider that someone bombards your DNS server with requests, making it unresponsive for a few seconds. In the meantime, an AOL subscriber tries to visit one of your websites, triggering a DNS lookup. Your nameserver fails to respond within a satisfactory timeframe, and AOL's network infrastructure thinks your hostname is bogus. Your entire web service could now be inaccessible by half the US for several hours, if not longer. (**Edit:** This is a bit over-simplified, but hopefully illustrates one type of problem.)

---

### Post by LightShear on 2006-12-21
Thanks for your advice, again. Now that I understand your side it does sound like a lot of trouble and we don't have that kind of equipment to prevent an outage. I just wanted an excuse to make a DNS server since I never have before; maybe I'll follow some howtos and experiment with my home server. Perhaps we just need an alternative to zone edit; know of any that are more reliable?

Thanks again for your help.

---

