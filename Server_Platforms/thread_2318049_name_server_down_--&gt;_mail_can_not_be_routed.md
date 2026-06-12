---
title: "name server down --&gt; mail can not be routed ?"
date: 2016-03-22
forum: Server Platforms
---

### Post by marchello_lippi2 on 2016-03-22
Hi all, 

I got domain example.com 

with name server ns.isp.com 

;; AUTHORITY SECTION:
example.com.            900     IN      SOA     ns.isp.com. root.isp.com. 2016030702 10800 3600 604800 10800

and mx record 
0 vps.example.com 
20 vps2.OtherExample.com 

Also I set backup name server at isp's managament panel as ns1.cloudns.com 

Everything worked fine till today when ns.isp.com went down. I tried to perform 
$ host example.com 
from different vps servers and one of them had cached information, but other didn't and just answered 'domain not found'. 
Now ns.isp.com is up again after few hours
So I tried to send email to myself to [email]user@example.com[/email] from different external mailboxes and as I can see, some of them already know that I'm online again, but other still think that my domain doesn't exist: 

[COLOR=#000000][FONT=Verdana]4.1.2 <[/FONT][/COLOR]user@example.com[COLOR=#000000][FONT=Verdana]>: Recipient address rejected: Domain not found 

So what should I do to prevent this? As I can see, my ISP doesn't provide backup dns and my try to use free dns [/FONT][/COLOR]ns1.cloudns.com didn't help. 
The worst is that it seems I loosed emails and my backup mx record didn't help too.
Please advise. 
Thanks ahead.

---

### Post by Graham_Willis on 2016-03-31
Do I understand correctly that this ISP has only one nameserver? That would be a very weird setup. I believe that it is against RFCs and even if it isn't, it certainly doesn't provide for reliability, they should have at least two nameservers in different geographical locations. Also, I don't understand how (or why) make it possible to specify backup nameserver if this functionality doesn't work. But are there some reasons for which the concerned domain should be delegated to ns.isp.com? If there aren't, then I think the simplest solution would be to delegate domain to a provider who offer more nameservers (the more the better). And if that is not possible, then perhaps settting long TTLs may be an option, but it also put you at risk as if you make a mistake in DNS then this mistake will hold for a long time and if for some reasons it's necessary to change f.e. MX records quickly, then it also wouldn't be possible.

However updating zone with a pseudorecord and then incrementing the serial can help to ease the situation you described at hand.

---

### Post by darkod on 2016-04-01
What do you mean by mx record vps.example.com and vps2.otherexample.com? If you have only one mail server, the hostname (FQDN) is one and only. Besides, if you have one mail server it doesn't help making multiple mx records. You should use one mx record poiting to the server hostname.

Now, to protect yourself against DNS server going down, the recommendation is to have at least two. That is how your mail will keep working even with one mx record when dns1 goes down, because dns2 will serve the requests.

You probably didn't set up the secondary dns correctly, and that's why it didn't work.

For that you would need in general:
1. In your registrars control panel (where the domain is registered) configure two nameservers to use, one from your ISP and another for the secondary (it doesn't matter really where it is).
2. On this secondary dns server configure the zone for your domain, otherwise it won't work.

You can have the secondary dns configured as slave in which case it will get the zone info from your primary dns, and you always do modifications only on the primary dns. It depends whether the primary dns allws such configuration because you usually have to allow the fact that a secondary dns will connect to copy the zone.

Or you can have both dns servers as masters and unrelated to each other but in such case you manually have to make all modifications to both servers because they are never syncing their zones.

If you set it up like that then when dns1 fails the dns2 should keep working and serving the dns requests for your domain.

---

### Post by SeijiSensei on 2016-04-01
I'd change providers and get one that is competent enough to follow the RFCs.  Having one DNS server go down is acceptable, but having no solid secondary server is bad practice for an ISP.  I rent virtual servers at [Linode](http://www.linode.com) and have one in Newark, NJ, and another in Fremont, CA, to handle primary and secondary DNS.  Being both topologically and geographically separate makes them highly resilient to failure.

You can mitigate this problem to some degree with long time-to-live values.  If your DNS records change only rarely, use something like 864000 for a TTL which means that any cached records will not expire for ten days.  However this isn't an effective strategy when it comes to mail servers since most mailers will check DNS each time they send a message.  You might consider running a DNS server on the same machine that has your mail server if that is an option.

---

### Post by marchello_lippi2 on 2016-04-03
Ok, it was my bad that I did not set up secondary ISP's name server in management panel. Now it seems ok. 
Speaking of mx records, I do use few mail servers, so one is main and other is backup.
Thanks to all.

---

