---
title: "Network traffic total through interface?"
date: 2012-10-27
forum: Server Platforms
---

### Post by darkod on 2012-10-27
Hello all.
I need to do some usage statistics for which I need the total traffic passing through one of the server interfaces. The server acts as firewall/router, so it's important that forwarded traffic is also counted, not just the traffic destined for that machine.
I think ifconfig gives you the traffic destined for the machine, but the forwarded traffic is much more important to me. I need the full total.

What would be the easiest and simplest way to get this number? I don't need any detailed statistics, however it would be nice if I can filter by protocol (or port) if that's easy to do.

I googled and is ntop something that would be an easy solution?
[http://www.cyberciti.biz/faq/debian-ubuntu-install-ntop-network-traffic-monitoring-software/](http://www.cyberciti.biz/faq/debian-ubuntu-install-ntop-network-traffic-monitoring-software/)

I don't need the gui or anything fancy. In fact, just a number is enough and maybe I can get that right now without installing anything, just I'm not aware of it.

For example, the server has uptime of 175 days. If there is a way to see the total number of the traffic through eth1, I would be happy with that too.

Any suggestions? Thanks.

---

### Post by Habitual on 2012-10-27
snmp
[URL="http://www.nwsmith.net/HintsTips/net-snmp-tutorial.htm"]This is a tutorial with examples on how to use 'Net-snmp' 
on Linux to query network devices.[/URL]

may help. 
net-snmp should already be 'installed'.

---

### Post by Cheesemill on 2012-10-28
I use [vnstat]("apt://vnstat"), it keeps a database of network usage for each interface and will give you daily, weekly and monthly statistics.

---

### Post by darkod on 2012-10-28
> **Cheesemill said:**
> I use [vnstat]("apt://vnstat"), it keeps a database of network usage for each interface and will give you daily, weekly and monthly statistics.

Thanks. I'll try to give it a shot in the next few days. I read the link about snmp but honestly didn't see anything helpful for traffic counting, it might be just me. :)

---

### Post by Habitual on 2012-10-28
Darko:

If you can use vnstat, here's something I tossed together using it.

```

#!/bin/bash
echo "Tx (MiB) for this hour is" $(for i in `date +%H` ; do vnstat --dumpdb | \grep "h;$i" ; done | cut -c 17- | cut -d\; -f1)
echo "Rx (MiB) for this hour is" $(for i in `date +%H` ; do vnstat --dumpdb | \grep "h;$i" ; done | cut -c 17- | cut -d\; -f2)

```

seems "vnstat --dumpdb" has some flexible options. :)

HTH.

---

### Post by darkod on 2012-10-28
I googled vnstat after it was mentioned and it sounds good. There is only one thing I couldn't find, or probably I missed.

Can it also display the maximum Tx and Rx rates the interface reached?

I saw there is an option like vnstat -l which seems to display the max but you have to activate the process, look at it and stop it with Ctrl + C when you are done.

In all the other "reports" I didn't notice max values. It would be nice if I can get the max load the interface handles.

PS. For example, I saw it here, at the very end of the article.
[http://humdi.net/vnstat/](http://humdi.net/vnstat/)

---

### Post by The Cog on 2012-10-28
> **darkod said:**
> Can it also display the maximum Tx and Rx rates the interface reached?[http://humdi.net/vnstat/](http://humdi.net/vnstat/)
The max rate is always the interface speed, 10/100/1000Mbit/Sec.
This is because the interface only ever transmits at that speed, and continues transmitting at that speed until there are no more packets in the transmit queue. If you are looking for any other figure, then you need to specify the time interval over which you want to calculate the average, and I guess the answer is "No, it only keeps hourly,daily, weekly and monthly averages".

P.S.
I think the ifconfig stats report total bytes through the interface, regertless of whether this was local traffic or forwarded from another interface.

P.P.S.
Getting protocol breakdowns isn't that easy as far as I know. You could perhaps use iptables to permit TCP:22, TCP:80 etc, and use the iptables hit counters there to track how many bytes each line logged, but it's a bit of a pain.

---

### Post by darkod on 2012-10-28
> **The Cog said:**
> The max rate is always the interface speed, 10/100/1000Mbit/Sec.
This is because the interface only ever transmits at that speed, and continues transmitting at that speed until there are no more packets in the transmit queue. If you are looking for any other figure, then you need to specify the time interval over which you want to calculate the average, and I guess the answer is "No, it only keeps hourly,daily, weekly and monthly averages".

OK, makes sense. But in this case the machine is a firewall/router in front of a webserver. The incoming internet connection is 10Mb with a burst of up to 100Mb, so it shouldn't be able to fill the 1Gb ever.

Ideally, I would like to see if I can find out how much of this 10/100Mb are getting used, including in peak traffic, so I can reconsider the services.

Does that make any sense?

---

### Post by The Cog on 2012-10-28
OK, I understand it won't ever reach 1G. But really, interefaces are generally fixed hardware speed, and only work at that speed. You really can't have a peak speed. Because transmisson is either on or off, to get any value other than 0% or 100%, you **have** to be averaging over time. GUIs will often sample at 1S or 2S intervals, which gives the impression of continuous monitoring, but they are really 1S or 2S averages.

---

### Post by darkod on 2012-10-28
> **The Cog said:**
> 
P.S.
I think the ifconfig stats report total bytes through the interface, regertless of whether this was local traffic or forwarded from another interface.


You might be right. The first time I looked at the numbers they seemed small, but now thinking about it, it might be right.

The system uptime is 177d12h and the eth1 ifconfig stats are Rx=1.1GiB and Tx=1.55GiB.

That gives approx daily averages of Rx=6.35MiB and Tx=8.94MiB. That would mean the traffic is much below the connection speed, which would be great news.

---

