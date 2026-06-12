---
title: "what is best network logger/monitor?"
date: 2015-06-10
forum: Server Platforms
---

### Post by Higgins909 on 2015-06-10
I'm looking for a free network logger.
I used to use webmin bandwidth monitor, but it would stop logging everyonce in a while and have to be reset.
Now I'm trying NTOP but not really liking it.

Things I need:
some sort of easy to get to UI with graphs
upload and download graphs hour day month year etc
never deletes any data

Would be nice if I would see who is taking up what bandwidth, when and where.

Thanks,
Higgins909

---

### Post by TheFu on 2015-06-11
For an entire network, you need to get data off the choke point, usually each router. That means using a MIB and NMS.  OpenNMS is the tool that comes to mind, but there are others.  Some routers will use remote syslog stuff too.

"best" is highly subjective - best for you isn't likely the best for me.

If you want to monitor bandwidth on each system, there are many. Monit, Munin, openNMS, Nagios, zabbix, Cacti, and probably 10 others. [https://www.debian-administration.org/article/597/Monitoring_with_Munin](https://www.debian-administration.org/article/597/Monitoring_with_Munin) is easy to setup - that could be "best.' It makes pretty graphs too - and not just about bandwidth.

Nagios is what most people seem to deploy. I haven't looked at it in about 5 yrs.  [http://blogs.gartner.com/jonah-kowall/2014/02/06/monitoring-software-sucks-so-i-use-nagios-whats-a-better-approach/](http://blogs.gartner.com/jonah-kowall/2014/02/06/monitoring-software-sucks-so-i-use-nagios-whats-a-better-approach/) has a few options.

---

### Post by LHammonds on 2015-06-11
I use Nagios to monitor various servers/switches/services on my network.  I don't monitor bandwidth but I could see how it could be done. If you can get your NIC stats from each system, you could set it up to collect that data at specific times and Nagios has a great reporting utility for services over time.  I use the reports mainly for availability and storage increases over time to help calculate how much storage we will need several years out.

LHammonds

---

### Post by SeijiSensei on 2015-06-11
If you use a Ubuntu box as the gateway router, as we do at one site, how about [ntop]("http://www.ntop.org/")?

---

### Post by LHammonds on 2015-06-11
> **SeijiSensei said:**
> If you use a Ubuntu box as the gateway router, as we do at one site, how about [ntop]("http://www.ntop.org/")?
You missed this in his 1st post:
> Now I'm trying NTOP but not really liking it.

---

### Post by Habitual on 2015-06-12
zabbix.

---

### Post by Shane_Carmichael on 2015-11-02
In my opinion, Zabbix and Nagios are the most capable and reliable open source platforms. Zabbix will offer more out of the box graphing optionality. Since you are looking to graph of multiple time horizons, this is a viable option. However, Nagios also has graphing capabilities and a larger network of integrations. If you are monitoring at scale, I would recommend using Nagios and plugging in either [New Relic]("http://newrelic.com/sp/brand/?utm_source=GOOG&utm_medium=paid_search&utm_content=New+Relic+Brand+Exact&utm_campaign=APM&utm_term=new%20relic&mpc=PS-GOOG-APM-EN-Signup-New+Relic+Brand+Exact-NORAM&_bt=46840043036&_bm=e") and/or [BigPanda]("https://bigpanda.io/integrations/nagios-the-alternative-to-a-flood-of-alerts"). Both will provide their own visual analytics on the health and performance of your monitoring environment, but BigPanda will also give you compression of your alerts, thus suppressing quite a bit of noise.

---

### Post by Elizine on 2015-11-03
Did you try MRTG? [COLOR=#303E48][FONT=Helvetica]MRTG is yet another open source monitoring tool that collects data at local and/or remote host by means of SNMP protocol. But MRTG is much more simple than Cacti, Nagios or Zabbix so it may be a good choice for small projects.[/FONT][/COLOR]

---

