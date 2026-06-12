---
title: "ping / monitor external hosts"
date: 2011-03-31
forum: Server Platforms
---

### Post by mortuk on 2011-03-31
We got a new net connection installed recently (a shared leased line) and at first it was great, but recently it seems the response time has taken a hit. Sometimes its ok and others its appalling.

Is there anyway for me to say continually ping google and get it all in a graph or something so that i can see when its suffering and by how much?

Cheers

---

### Post by BkkBonanza on 2011-03-31
A combination of a cronjob and a one-line command could do this easily. Interpreting and graphing the info after would be more challenging but there are packages around that can do it with a bit of learning, or maybe just dumping the info into a spreadsheet to massage would be enough.

You could add a line like this to a cronjob (type crontab -e and paste in),

```

* * * * * ping -nc 1 google.com |awk '/ttl/ {print strftime("%F-%T"),substr($7,6)}'>>~/ping.log

```

That gives you a check every minute with current date-time and rtt in two columns, appended into your ping.log. (rtt is round trip time in mS). If you don't want so much data change it to every 5 minutes by changing the first * to */5.

Whether a ping will give you reliable indication of connection speed is another question though.

---

### Post by mortuk on 2011-03-31
Thanks for the solution. I am a web dev so porting the raw data into a graph wont be an issue, however I was hoping for something a bit less time consuming and more out of the box

Its not really the connection speed thats the issue, we seem to get what we are expecting download / upload speed wise, its more the response time before any transfer of data even takes place.

Best example I can give is that when I open a tab, type in a URL, hit enter, the time it takes to resolve the address and initiate the data load seems to take the time. When I do this to an internal address (one of our locally hosted dev servers) its more or less instant, but to any external addresses it can sometimes take 5-10 seconds just to think about it.

---

### Post by Grenage on 2011-03-31
Have you ruled out a DNS problem?

---

### Post by BkkBonanza on 2011-03-31
You can generally tell DNS problems in Firefox by watching the status line at bottom. If it gets stuck on "looking up ..." rather than "connecting..." and "waiting", then the problem is likely DNS lookup.

You could try a manual DNS lookup for a site and typing in the IP directly. 
See if the site loads quickly. But be sure to choose a site that doesn't have a lot of other urls to resolve (eg. many linked photos from other IPs). This may help figure it out.

Also change your /etc/resolv.conf to have google DNS 8.8.8.8 and test with that. It is not too uncommon for ISP DNS servers to be awful, and sometimes bypassing them can make a big difference.

Of course, if this is intermittent then you need to test like this during a problem time.

BTW I only suggested the idea above because that's what you asked for, rather than being more clear about your actual problem is.

---

### Post by rubylaser on 2011-03-31
You could just use Smokeping. Easy to setup and works great.

[http://oss.oetiker.ch/smokeping/]("http://oss.oetiker.ch/smokeping/")

---

### Post by nobound on 2011-08-23
Thanks, I've been looking for something simple like this.
One small edit, I had to escape the % symbols in my crontab file to get this to work.

```
* * * * * ping -nc 1 google.com |awk '/ttl/ {print strftime("\%F-\%T"),substr($7,6)}'>>~/Desktop/pinglog.csv
```

---

### Post by eentonig on 2011-08-23
Proxy in between that 's checking the urls or content.

---

### Post by gcc on 2012-03-12
Just published a Java applet to help with this:

[https://github.com/aptivate/netgraph](https://github.com/aptivate/netgraph)

---

