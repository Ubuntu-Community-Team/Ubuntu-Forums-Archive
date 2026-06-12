---
title: "Utility for tracking cpu and bandwidth usage by process?"
date: 2008-11-14
forum: Server Platforms
---

### Post by touser on 2008-11-14
I'm sure there are a thousands apps that will track and graph cpu and bandwidth utilization by process--what I'm looking for are some recommendations of apps that can do this well and output data that can be easily read and manipulated for comparison and log it for later access.

Edit: I am NOT looking for just instantaneous bandwidth/cpu utilization.

---

### Post by hictio on 2008-11-14
This is subjective, I guess, but IMHO, the easiest and fastest way of getting this is (if you have an Apache or similar) using [MRTG](http://oss.oetiker.ch/mrtg/) and either scripts to gather the information from, say, the /proc filesystem, or setup snmpd on the box and use MIBs.

---

### Post by windependence on 2008-11-14
TOP from the command line for processes. MRTG is great for bandwidth. There are also many other command line utilities if you do a Google search.

-Tim

---

### Post by hictio on 2008-11-14
If you want to go with CLI tools, my favorites are:

- [iftop](http://ex-parrot.com/~pdw/iftop/)
Sort of like a 'top' for bandwidth use

- [htop](http://htop.sourceforge.net/)
A better 'top', more configurable.

You can install thosse using 'aptitude install'.

---

### Post by touser on 2008-11-14
I wasn't aware htop would log resource utilization on a per-process basis for later analysis. Obviously it provides "instantaneous" resource utilization but that's not really what I'm looking for, I need to aggregate resource utilization (bandwidth and cpu) for later analysis--again on a per-process basis.

I don't see this option in htop, can you help me?

---

### Post by hictio on 2008-11-14
> **touser said:**
> I wasn't aware htop would log resource utilization on a per-process basis for later analysis. Obviously it provides "instantaneous" resource utilization but that's not really what I'm looking for, I need to aggregate resource utilization (bandwidth and cpu) for later analysis--again on a per-process basis.

I don't see this option in htop, can you help me?

Ok, if that is the case, then MRTG will give you trending, and if you want to make a little more work, take a look at [Zabbix](http://www.zabbix.com/).
I have never installed on a Ubuntu box, but on CentOS, the program is simple amazing, but compared to MRTG it uses a lot of resources.

---

### Post by windependence on 2008-11-15
Zabbix is fantastic. If you want to go full blown, you could try Cacti, or Nagios. Full featured tools but setup is daunting.

-Tim

---

### Post by hictio on 2008-11-15
> **windependence said:**
> Zabbix is fantastic. If you want to go full blown, you could try Cacti, or Nagios. Full featured tools but setup is daunting.

-Tim

Actually... I think is the other way around... :D
If you **don't** want to go full blown, then choose Cacti or Nagios.
But, for trending, IMHO, it is better MRTG than Nagios, is a monitor, very, very useful to keep up with problems on your servers.

Zabbix sorts of stand in the middle, it can notify of problems, while at the same time has a an amazing capability to make and keep trend information, and the graphs are really astounding.

---

### Post by Ophidion on 2010-12-11
try nethogs, cheers!

---

### Post by sjhupp on 2010-12-12
Did the OP find one suitable?

I have a 10.04 server running, and looks like I'm uploading quite a lot of data (our plans count that as part of our monthly quota, so I need to understand exactly which process is doing it, how much and when.)
Havwe you found anything that can report on the last 24hrs (or whatever time frame) with which apps used upload and/or download bandwidth/data etc?
Be very interested to try it.
Thanks.

---

