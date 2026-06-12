---
title: "[SOLVED] Server monitoring software"
date: 2007-08-08
forum: Server Platforms
---

### Post by cancaseiro on 2007-08-08
Hi!

Can someone please recommend good server monitoring software?

---

### Post by mzar on 2007-08-08
Zabbiq or Nagios Web.

---

### Post by cancaseiro on 2007-08-08
> **mzar said:**
> Zabbiq or Nagios Web.

Thanks but I didn't find anything about Zabbiq from Google.

---

### Post by cancaseiro on 2007-08-08
Has anyone used [iLO]("http://h18004.www1.hp.com/products/servers/management/ilo/")?

Pros, cons?

---

### Post by MJN on 2007-08-08
> **cancaseiro said:**
> Thanks but I didn't find anything about Zabbiq from Google.
 
Try Zabbix - did Google not suggest it? (it's usually quite good in that regard)
 
(Incidentally I have no experience of Zabbix, just Google! ;))
 
Mathew

---

### Post by rickyjones on 2007-08-08
> **cancaseiro said:**
> Has anyone used [iLO]("http://h18004.www1.hp.com/products/servers/management/ilo/")?

Pros, cons?

iLO isn't exactly for monitoring servers in my experience (that, and it's only available on servers that have the hardware installed). Personally I use Nagios on my home and client networks. My employer uses Orion and HP Insight Manager to monitor and page though.

-Richard

---

### Post by cancaseiro on 2007-08-09
> **rickyjones said:**
> iLO isn't exactly for monitoring servers in my experience (that, and it's only available on servers that have the hardware installed). Personally I use Nagios on my home and client networks. My employer uses Orion and HP Insight Manager to monitor and page though.

-Richard

Ok, I am searching on anyways. I want to find definitly the best one and will not rush with deciding what to use.

---

### Post by nocturn on 2007-08-09
Nagios is very, very good.  Heard many good things about the new ZenOSS core.  

Tried Zabbix, not so great IMO

---

### Post by wirelessmonkey on 2007-08-10
Groundworkopensource ([www.groundworkopensource.com](www.groundworkopensource.com)) is wonderful, easy to install/configure, and just plain nifty.  However, I use openNMS for network monitoring and to get server status, i.e. uptime, throughput, traffic, disk status, logged in users, memory usage, cpu stats.    I also use Cacti to monitor uptime and graph network utilization, users, cpu/memory stats.  openNMS provides tons of hard data, and I love the easy to use graphing capability of Cacti.

---

### Post by orotrev on 2007-08-10
I have found Zabbix to do the job well. I currently have it monitoring 4 systems. I though it was relatively easy to setup and configure. iLO, in my experience on HP server, stands for integrated lights out. It is a way to access a system even though it is down. With iLO you can power a system up or down, as if you were right in front of it and using the integrated VNC client see the post of the system. I believe, as is the case with HP iLO it can be integrated into their Insight Manager. But give Zabbix a shot.

---

### Post by quietas on 2007-08-10
Hehe, I'd definately add a second for Nagios. I've got it on my network here at work monitoring 6 locations throughout the state, 14 servers, 12 routers, 22 switches, 15 print servers, and more.

It's able to monitor specific IP's or a range of IP's, and on those it can watch for specific servers such as HTTP or FTP. Between emails and text messages I know within a minute normally of a server or router going out, I have print servers set at 5 minutes, and there is plenty of more options available.

---

### Post by rbprogrammer on 2007-08-10
i personally use [webmin]("http://www.webmin.com/"), and the old fashioned ssh..

did you try webmin yet?

---

### Post by cancaseiro on 2007-09-06
> **rbprogrammer said:**
> i personally use [webmin]("http://www.webmin.com/"), and the old fashioned ssh..

did you try webmin yet?

I just installed Webmin and Cacti and will test them.

---

### Post by GigaVolt on 2007-09-06
Hi,

View this solution: [http://mon.itor.us/](http://mon.itor.us/) \\:D/

---

### Post by shizzy-t on 2007-09-06
I have to say I really like Open NMS [http://www.opennms.org/index.php/Main_Page](http://www.opennms.org/index.php/Main_Page)

It does network auto discovery and has tons of features.

---

### Post by cancaseiro on 2007-09-06
I have problem with cacti. Actually with SNMP: Cascti says: SNMP error. How can I overcome that?

---

### Post by Brazen on 2007-09-06
Nagios is by far the most popular open source monitoring software (probably one of the most popular even compared to proprietary software).  The only question is which management front-end to use.  Personally, I'm interested in Oreon (now called Centreon, or something like that) though I have not tried it out yet.

---

### Post by wirelessmonkey on 2007-09-07
cancaseiro,

You need to install the snmp server on your machine.

---

### Post by cancaseiro on 2007-09-07
> **wirelessmonkey said:**
> cancaseiro,

You need to install the snmp server on your machine.

I have installed it with apt-get install snmpd.

---

### Post by HermanAB on 2007-09-07
Zabbix is the easiest to install and scales to hundreds of nodes.
OpenNMS is the most difficult to instal, but it scales very well to tens of thousands of nodes.
Nagios is in between.

---

### Post by ftk on 2007-09-27
Take a look at JFFNMS [http://www.jffnms.org/](http://www.jffnms.org/)

I use it at work monitoring 500+ machines with alerts, etc...Plus you can give management a nice dashboard view of what's going on if needed.

---

