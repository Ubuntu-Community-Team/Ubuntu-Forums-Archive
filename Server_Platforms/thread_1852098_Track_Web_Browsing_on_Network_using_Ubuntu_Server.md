---
title: "Track Web Browsing on Network using Ubuntu Server"
date: 2011-09-29
forum: Server Platforms
---

### Post by abandonedthe_mulletator on 2011-09-29
Hi,

I have an Ubuntu server at my workplace which acts as a router/gateway for our network.  Is there a way I can track what websites are visited by client PCs?

Thanks

---

### Post by Dangertux on 2011-09-29
You can probably use dansguardian for this -- however in that application I believe you would have to purchase an adequate license.

---

### Post by collisionystm on 2011-09-29
You can use Squid Proxy to do this. Or even better, use Zentyal.

We had squid running on an old server and did the same thing you are trying to do. We had to set each browser to authenticate through the proxy and then had a script in our crontab that generated a log file each night.

> /usr/bin/perl -w /usr/local/bin/squint.pl /var/www/traffic < /usr/local/squid/var/logs/access.log

---

### Post by abandonedthe_mulletator on 2011-09-29
> **collisionystm said:**
> You can use Squid Proxy to do this. Or even better, use Zentyal.

We had squid running on an old server and did the same thing you are trying to do. We had to set each browser to authenticate through the proxy and then had a script in our crontab that generated a log file each night.

Cool.  Squid should work out.  I'll have to learn about how it logs visited websites.

Does Zentyal require clients to set a proxy in their browser?

---

### Post by spynappels on 2011-09-30
I'm not sure if Zentyal uses Squid to do this, but squid can be set up as a transparent proxy, which if it runs on your gateway box anyway, means you won't have to change any client side config. You can configure Squid to capture all traffic with a destination port of 80, so all web traffic is captured and processed (caching, filtering and logging).

---

### Post by Jonathan L on 2011-09-30
> **the_mulletator said:**
> Hi,

I have an Ubuntu server at my workplace which acts as a router/gateway for our network.  Is there a way I can track what websites are visited by client PCs?

Thanks

Hi 

Just a tip: when you do this, you might find out some very surprising things about individuals which you might have to keep private, such as medical conditions and financial information, as well as who's using facebook and adult websites.  You should consider reviewing your security policies about who can see the logs you generate, and for how long, and in what condition.  In one place I worked we kept the logs without the user names, so you would have to cross reference if you really needed to know who was looking at a paricular website rather than it being right there on the screen that Bert is browsing drug rehab support groups.

And of course you tell people that web browsing will be logged!  It's just good manners, and probably you'll have local legislation requiring it.  But it also has the effect of cutting out a lot of inappropriate web use before you even put the logs in.  If you don't have a written-up policy about these things, it's time to get one.  Most people in companies think the IT staff spy on them anyway, but it really helps if you have written up rules about what is considered private and what is not, and have management that stands by that.

Hope that's of use.

Kind regards,
Jonathan.

---

### Post by abandonedthe_mulletator on 2011-10-01
Thanks guys.  I set up squid as a transparent proxy and it is working as I hoped.  I just have to come up with a script to organize the log files.

We will definitely notify everyone that web traffic is being logged.

---

### Post by SeijiSensei on 2011-10-02
Take a look at [SARG](http://sarg.sourceforge.net/sarg.php) if you want a convenient method to summarize Squid's access log.

---

### Post by headvampyre@hotmail.co.uk on 2011-10-02
If you only want to monitor the traffic, does he really need a proxy?

Couldn't you just configure IPTables to log every packet sent on port 80,443 and 8080?

---

### Post by SeijiSensei on 2011-10-03
Wow, I'd hate to have to diagnose those logs.  

Squid's access logs have entries that look like this:

```
1290403600.659    378 10.10.10.10 TCP_MISS/200 1807 GET http://weather.partners.msn.com/data.aspx? - DIRECT/65.55.17.39 text/xml

```

It consists of a timestamp (with milliseconds), the duration of the request in milliseconds, the requesting IP address, the nature of the request (here it's getting an object that's not already cached, hence "MISS"), the size of the object in bytes, the request method (GET in this case), the target URL (with the query string truncated), the type of connection and the server's IP address, and the mimetype of the object.  (This the squid-2 format; I haven't got a proxy running squid-3 yet.)

That's a bit more informative than a packet dump, don't you think?

---

### Post by i.r.id10t on 2011-10-03
I think there is a way of using analog (analog.cx) on squid log files...

---

### Post by SeijiSensei on 2011-10-03
Analog is very customizable in terms of the log formats it will accept, and squid will write logs into custom formats including the "Common Log Format" that web servers like Apache use.

I've used analog for years to generate web traffic reports.  I think SARG is a better choice for summarizing squid logs, though, since it produces daily reports by default.  In a setting where you have hundreds of users behind the proxy, you need frequent reports to keep up with the traffic generated.

I've actually written a PHP application for a client that parses the squid access logs and places the results in a database for analysis via a web-based front end.  It's more flexible than SARG since the administrator can quickly identify all the sites visited by a single IP address across a longer period of time like a month or two, or list all the visitors to a specific domain or URL.

---

