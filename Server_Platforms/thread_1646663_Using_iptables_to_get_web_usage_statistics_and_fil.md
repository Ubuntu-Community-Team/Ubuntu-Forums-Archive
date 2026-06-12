---
title: "Using iptables to get web usage statistics and filter urls"
date: 2010-12-16
forum: Server Platforms
---

### Post by mee.six on 2010-12-16
Hello everyone,

I'm deploying new ubuntu server which should act as a router. I've already set up the NAT for local network, and also did some shaping for different groups of users, but now I'm facing new problem.
I need to make a scheduled URL filter. I know it's not a problem with cron and simple script, but maybe there is existing way to do that? 
And also, I need to make statistics on web-traffic. I need to have list of URLs visited by users (source ip, destination url). Is it possible with iptables? or with any other software but without using proxy servers.

thanks in advance,
Michael

---

### Post by SeijiSensei on 2010-12-16
> **mee.six said:**
> And also, I need to make statistics on web-traffic. I need to have list of URLs visited by users (source ip, destination url). Is it possible with iptables? or with any other software but without using proxy servers.

Not unless you're willing to write iptables rules for every pair of local addresses and website addresses you want to monitor.  For instance,

```
iptables -A INPUT -p tcp -s 10.1.1.1 -d www.google.com --dport 80
```

Honestly, it's just a lot easier to do this with Squid in transparent mode.  You'll get a log of every object accessed via the web.  What's more you can use "access control lists" to block sites and objects you want to keep out of your network.  You can get simple statistics using [SARG]("http://sarg.sourceforge.net/").

---

### Post by mee.six on 2010-12-17
Oh... I didn't know about SQUID in transparent mode. thanks a lot for that :)

---

### Post by mee.six on 2010-12-17
and is there a way to add filters that are changed by schedule. Disable social networks during work hours, enable in the evening and so on?

---

### Post by SeijiSensei on 2010-12-17
[http://www.deckle.co.za/squid-users-guide/Access_Control_and_Access_Control_Operators#Current_day.2Ftime](http://www.deckle.co.za/squid-users-guide/Access_Control_and_Access_Control_Operators#Current_day.2Ftime)

---

### Post by mee.six on 2010-12-17
> **SeijiSensei said:**
> [http://www.deckle.co.za/squid-users-guide/Access_Control_and_Access_Control_Operators#Current_day.2Ftime](http://www.deckle.co.za/squid-users-guide/Access_Control_and_Access_Control_Operators#Current_day.2Ftime)

Great, thanks a lot :)

---

### Post by iponeverything on 2010-12-17
I have perl/php scrips in past to load the logs into mysql database and fairly simple php script to mine the database to display the browsing history for any given ip address among other things -- it was not to hard.

ntop also does some amazing things in real time user traffic and protocol analysis.

---

### Post by mee.six on 2010-12-17
> **iponeverything said:**
> I have perl/php scrips in past to load the logs into mysql database and fairly simple php script to mine the database to display the browsing history for any given ip address among other things -- it was not to hard.

ntop also does some amazing things in real time user traffic and protocol analysis.

thanks for ntop hint. 

Btw, is there a way to block torrents?

---

### Post by iponeverything on 2010-12-17
> **mee.six said:**
> thanks for ntop hint. 

Btw, is there a way to block torrents?

Torrent'ers are easily id'ed by the excessive number tcp sockets that they have open. The easiest way to break torrents is to limit the number of open tcp sockets that any given ip can have. If you limit an ip's open tcp sockets to about 30 or so you will quite effectively break torrents (they will be lucky to exceed 30k/sec)

There is very good linux-based product out there called netequalizer does a lot of this stuff. It gives very fine control over traffic -- combine it with a transparent squid proxy with squid-guard and you can have good control. Add a captive portal to your network's border and you can add a splash page or force authentication..

---

### Post by SeijiSensei on 2010-12-17
> **mee.six said:**
> thanks for ntop hint. 

Btw, is there a way to block torrents?

One solution is to block all outbound traffic using high ports and connecting to high ports.  Something like this;

```
iptables -A INPUT -p tcp -s 192.168.1.0/24 --sport 1024:65535 --dport 1024:65535 -j REJECT
```

Most ordinary users don't need to communicate to remote high ports.  They're typically using services that make requests to ports below 1024 like HTTP, SMTP, etc.  If you have users that need to connect to specific custom services on high ports, you'll need to include specific exemptions for those IPs/services.

---

