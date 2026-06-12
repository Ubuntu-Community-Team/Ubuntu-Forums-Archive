---
title: "Multiple Web Servers"
date: 2005-04-26
forum: Server Platforms
---

### Post by Myles3 on 2005-04-26
Hi I want to run two Web Servers one Linux Apache and the Other Windows IIS. They are both running currently on the same IP Address. What I want to do is have linux.domain.org point to the Linux Computer and windows.domain.org point to the Windows Computer. Can anyone help me out with this?

---

### Post by tonym on 2005-04-26
Please can you explain what you mean when you say they are running on the same IP address.  Are they separate machines behind a NAT firewall?

---

### Post by Myles3 on 2005-04-26
[QUOTE=tonym]Please can you explain what you mean when you say they are running on the same IP address.  Are they separate machines behind a NAT firewall?[/QUOTE]

There are both running the same external IP... but both computers have an indepentent network IP like 192.168.1.108

---

### Post by tonym on 2005-04-27
Sorry if I'm being a bit stupid here.  How are these machines connected to the Internet?  In what way are they set up to "run the same external IP"?

---

### Post by Myles3 on 2005-04-27
Okay This will explain it better:

[CENTER]Internet (domain.org)[/CENTER]
[CENTER]^[/CENTER] 
[CENTER]|[/CENTER]
[CENTER]Windows Web Server (192.168.1.101)    ----------   Ubuntu Web Server (192.168.1.170)[/CENTER]

I want both to be able to service the internet with HTTP, FTP, SSH, VNC, etc. So when I connect externaly in ssh I would go windows.domain.org or ubuntu.domain.org to connect to the respective computers.

The problem is that I only have one internet connectoin which means one external IP.

I havn't done anything with domains till now and I personally think if i edit the hosts file it will do the trick.

But then again how dose the rounter decide where to trafic the information. I am using a Liksys WRT54G (The one where you can install Linux) and was thinking I could find a distrbution for it which would assign the sub-domains.

P.S. Yes you can run an SSH Server on Microsoft Windows!

---

### Post by tonym on 2005-04-27
I think you have two options.

One is to get a second IP address and then use your router to forward the addresses to the two machines.  If your router runs Linux then this can be done using iptables and DNAT.

A variant on this with one address would be to use non-standard ports for one of the machines but this means the user would have to be aware of this and quote the port numbers.

If you don't have 2 addresses then I think it is harder.  You need software that can recognise which domain was used even though the IP address is the same.  I'm not even sure this is possible for some of the protocols you mention.

For ssh you could connect to the router and then ssh from there to the required machine using the local address.

For http you could run a proxy on the router - Apache or Squid.  These can detect which domain has been requested and then forward appropriately.  However this will only work for http,  not https.

I can't help on the other protocols I'm afraid.

---

### Post by Fab on 2005-04-27
[QUOTE=tonym]I think you have two options.

One is to get a second IP address and then use your router to forward the addresses to the two machines.  If your router runs Linux then this can be done using iptables and DNAT.

A variant on this with one address would be to use non-standard ports for one of the machines but this means the user would have to be aware of this and quote the port numbers.

If you don't have 2 addresses then I think it is harder.  You need software that can recognise which domain was used even though the IP address is the same.  I'm not even sure this is possible for some of the protocols you mention.

For ssh you could connect to the router and then ssh from there to the required machine using the local address.

For http you could run a proxy on the router - Apache or Squid.  These can detect which domain has been requested and then forward appropriately.  However this will only work for http,  not https.

I can't help on the other protocols I'm afraid.[/QUOTE]
 blargh, simple subdomain forwarding to local ips should fit

---

### Post by Myles3 on 2005-04-27
[QUOTE=Fab]blargh, simple subdomain forwarding to local ips should fit[/QUOTE]

This can be done in the */etc/hosts* file correct?

---

### Post by Fab on 2005-04-27
[QUOTE=Myles3]This can be done in the */etc/hosts* file correct?[/QUOTE]
 i don't know, i don't run webserver(s) on my own box.
i do however know, that it should be quite simple to do so
because, if cpanel can, it cant be too hard ;P

---

### Post by Myles3 on 2005-04-27
I hope this will help someone in the near future:

**On Linux**
You should edit the /etc/hosts file adding something like this:
127.0.0.1     ubuntu.domain.org ubuntu

**Windows**
Just go into you Control Plane -> System -> Network Identification -> Proporties -> More... Then just add you domain into Primary DNS suffic of this computer.

This all worked for me.

---

### Post by heimo on 2005-04-27
[QUOTE=Fab]i don't know, i don't run webserver(s) on my own box.
i do however know, that it should be quite simple to do so
because, if cpanel can, it cant be too hard ;P[/QUOTE]

Do you mean virtual hosting? I do run web servers and I can tell that name based virtual hosting is a whole different scenario. Yes, it's easy to setup different websites with different names to same ip. Thousands, if you like.

It's a different story to direct traffic through NAT (to reserved addresses), using one public IP. You need application layer logic, proxy, apache settings, what-ever.

tonyms answer is very professional. I'd only add couple possible ways to get around this. With HTTP, you could portforward from router to Apache and make it to "forward proxy" windows.example.org traffic transparently to IIS. This will of course cause additional traffic, but may be acceptable. This is probably the module I'm talking about:
[http://apache2docs.paradoxical.co.uk/mod/mod_proxy.html]("http://apache2docs.paradoxical.co.uk/mod/mod_proxy.html")

About SSH. If it's not a big issue, you could also portforward 22 to windows or linux machine and then just take another connection to the other machine, when neccessary. Or you can use non-standard ports (as tonym suggested). It depends on what you're going to do with this and what suits you best. tonym already gave the good solutions.

/etc/hosts file? No. cpanel? Not likely.

What would I do? Get rid of nat, get two static IPs. (Oh, actually I'd get rid of the Windows, but that's probably not an option in your case.) I hope you can solve it.

---

### Post by heimo on 2005-04-27
[QUOTE=Myles3]I hope this will help someone in the near future:

**On Linux**
You should edit the /etc/hosts file adding something like this:
127.0.0.1     ubuntu.domain.org ubuntu

**Windows**
Just go into you Control Plane -> System -> Network Identification -> Proporties -> More... Then just add you domain into Primary DNS suffic of this computer.

This all worked for me.[/QUOTE]

I'm amazed. Was this answer to something in the middle of the thread, or are you seriously suggesting this as a solution to the original problem?

EDIT: Never mind.

---

### Post by crmanski on 2005-04-27
I have been doing to transitioning away from IIS to an apache based installation.  I still have some ASP code that I need to run on IIS though.  To get around this I put the Apache server in the front to handle all of the web requests and the domains that I needed to run on the IIS box I proxied via apache's mod_proxy.

So it would look something like...
External IP (Apache)
if Apache domain then serve the pages
if not proxy to the IIS box.

For instance I have something like below on my apache...

<VirtualHost *:80>
ServerName szone.berlinwall.org
ServerAlias szone.berlinwall.org
	DocumentRoot /path/to/my/www
	ProxyRequests off
	ProxyPass /eduzone [http://internal.domain:82/eduzone/](http://internal.domain:82/eduzone/)
</VirtualHost>

In the above only the path /eduzone/ gets forwarded to the IIS box.
If I wanted to do it for the whole domain I would just change
	ProxyPass /eduzone [http://internal.domain:82/eduzone/](http://internal.domain:82/eduzone/)
to 
	ProxyPass / [http://internal.domain:82/eduzone/](http://internal.domain:82/eduzone/)

---

### Post by WiFi Net Guy on 2005-07-07
Sorry if I'm being a little dense. But here's what I'm trying to do and please let me know how to accomplish it. I'm a little lost in this thread:

I have two boxes: 1 Kubuntu box running Apache2 that has my company webpage. 

My second box is a Winbloze Server 2003 with Exchange

I only have one domain. How can I have http traffic go to the webpage while Exchange traffic goes to the Winbloze box?

Format, of course, is: [http://www.mydomain.net](http://www.mydomain.net) (for webpage traffic) and [http://www.mydomain.net/exchange](http://www.mydomain.net/exchange) (for, uh, Exchange traffic)

Thanks in advance...

---

### Post by LordHunter317 on 2005-07-07
You have two options:[list=1][*]Run one on a nonstandard port (i.e., not port 80).  Then you'd connect to [www.mydomain.net](www.mydomain.net) for regular stuff, and [www.mydomain.net:8080](www.mydomain.net:8080) for exchange[*]Use a proxy, like squid or mod_proxy for Apache 2 to forward traffic to /exchange to the Windows box.  This is more complicated, but probably what you'll have to do.[/list]I should also point out that allowing access to exchange over the internet without encryption is a ludcriously stupid idea.

---

### Post by Neg127 on 2005-07-07
[QUOTE=WiFi Net Guy]Sorry if I'm being a little dense. But here's what I'm trying to do and please let me know how to accomplish it. I'm a little lost in this thread:

I have two boxes: 1 Kubuntu box running Apache2 that has my company webpage.

My second box is a Winbloze Server 2003 with Exchange

I only have one domain. How can I have http traffic go to the webpage while Exchange traffic goes to the Winbloze box?

Format, of course, is: [http://www.mydomain.net](http://www.mydomain.net) (for webpage traffic) and [http://www.mydomain.net/exchange](http://www.mydomain.net/exchange) (for, uh, Exchange traffic)

Thanks in advance...[/QUOTE]
 There is all so the option of a linux based exchange replacement.  I'm not sure how well they work but I did a little research on them just the other night.  SuSe has an exchange replacement that is not free but it seems to be one of the most recommended ones that I have read about.

I have all so found a couple of open source alternatives.  There is one called exchange4linux or code named BILL Workgroup Server ([http://www.exchange4linux.org/billworkgroup/home)](http://www.exchange4linux.org/billworkgroup/home)).  There is all so openchange exchange replacement for linux ([http://www.openchange.org/)](http://www.openchange.org/)).  Those are probably the two best open source solutions I have found just yet.  Though I'm not 100% sure this is or would be an option for you, but it’s an idea for a solution.

Hope this will be of help to you or to some one else in the future.

Neg127

---

### Post by crmanski on 2005-07-08
If OWA is not required, I would use something like SquirrelMail [http://www.squirrelmail.org/](http://www.squirrelmail.org/) to access exhange instead. If you really need MS Outlook Web Acess then this page seems to describe the process in detail...
[http://www.sikurezza.org/ml/03_04/msg00041.html](http://www.sikurezza.org/ml/03_04/msg00041.html)

---

