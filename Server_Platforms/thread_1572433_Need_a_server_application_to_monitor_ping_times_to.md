---
title: "Need a server application to monitor ping times to clients"
date: 2010-09-11
forum: Server Platforms
---

### Post by gronbaek on 2010-09-11
Hi guys

I have an embedded server running Ubuntu which is on a network with a lot of wireless AP's. The AP's doesn't support SNMP or anything else, so I monitor if they are up or down by simply pinging them continuously.

My question is if there is anything I could install on the server that could provide me with a webpage where I could see the ping time to the AP's? So it just shows a list of the IP's I have told it to ping, and what their latest response time is. This is what I basically need, but if it were more advanced than that, and could give warnings if ping time were to high etc. that would also be nice.

Regards

Bjørn

---

### Post by BkkBonanza on 2010-09-11
Why don't you just write a simple script to do it? There probably is some package that can do it but my guess is that it will be more work to setup and configure than to just do a script since the task is fairly simple.

eg. pingstats
```
#!/bin/bash

HTMLPATH="/var/www/site/stats.html"
NODES=( 192.168.2.1 192.168.2.2 192.168.2.3 )

while true; do

TIMES=()
for ip in ${NODES[@]}; do
  TIMES[${#TIMES[@]}]=$(ping -nc 1 ${ip}|grep "time="|awk -F= '{print $4}'|awk '{print $1}')
done

TS=`date`
cat >$HTMLPATH <<-EOF
<HTML><HEAD>...blah blah</HEAD>
<BODY>
This is my heading and stuff like that, whatever...
Up to the table rows 
${TS}
<TABLE>
EOF

for ((n=0; n < ${#NODES[@]}; n++)); do
  echo "<ROW><COL>${NODES[$n]}</COL><COL>${TIMES[$n]}</COL></ROW>" >> $HTMLPATH
done

cat >>$HTMLPATH <<-EOF
</ROW></TABLE>
Stuff after the table, whatever...
<HTML>
EOF

sleep 10
done

```

This simply loops every 10 seconds doing the pings and writing a new html file. You plug in your IPs. You can alter the html to suit, and change the ping interval.

Put it in your /etc/local.rc and it will start at boot.

Run it in the background like this,

pingstats &

Anyway, I just threw that together in a few minutes as an example.
This one works though - I just tested it.

---

### Post by hictio on 2010-09-11
Don't know how hard is for you if something goes wrong with the devices you are monitoring, but, I believe you should really take a look at [Nagios](http://www.nagios.org/) for the monitoring part of the deal; and you can use [MRTG](http://oss.oetiker.ch/mrtg/) to graphic the ping latency, if for instance, you want to keep trends.
Both of those are free, and they are on the repositories.
Another very good package for monitoring/ trending is [Zabbix](http://www.zabbix.com/), it is a bit more complex and has more dependencies than Nagios, but it looks impressive ;)

---

### Post by arrrghhh on 2010-09-11
Yea, there are a TON of network monitoring tools.  [Zenoss](http://www.zenoss.com) is one of my faves, very customizable... which a good company behind it, but the enterprise product is very $$$... Their core product is completely free.  It may be overkill for what you're needing tho.

---

### Post by thingy on 2010-09-11
Maybe you are after something like PingPlotter ([http://www.pingplotter.com/]("http://www.pingplotter.com/")).

In which case, try this [http://sourceforge.net/projects/m-ping/]("http://sourceforge.net/projects/m-ping/")

---

### Post by BobVila on 2010-09-14
> **arrrghhh said:**
> Yea, there are a TON of network monitoring tools.  [Zenoss](http://www.zenoss.com) is one of my faves, very customizable... which a good company behind it, but the enterprise product is very $$$... Their core product is completely free.  It may be overkill for what you're needing tho.

I like Zenoss as well (aside from Core being DEAD slow without a ton of tweaking); It seems like overkill for this application, though. 

A quick script is the most straightforward way to do this. If you'd like to incorporate more monitoring than just these APs, look at Nagios.

---

### Post by kustomjs on 2010-09-18
i have a simple script that does single ping PM me if you want it?

---

