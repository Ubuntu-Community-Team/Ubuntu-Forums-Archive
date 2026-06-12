---
title: "searching a Traffic Counter"
date: 2005-09-07
forum: Server Platforms
---

### Post by mael on 2005-09-07
hi there
I'm searching a traffic counter for my Ubuntu Hoary headless server/router
i already search using google, sourceforge, apt-cache etc but didn't find anything useful

the main interest is a summary, how many incoming and outgoing traffic flowed through one or more interfaces on a daily, weekly, monthly and yearly basis 

graphs (keyword RRD) of this would be nice but plain numbers are necessary

the output maybe a web site but simple text based output would be good enough, too

if the counting method uses iptables statements, it has to be easy to integrate them into my own iptables script (build by fwbuilder)
in this case the best way would be to insert the statements using the fwbuilder installation routine of the iptables script

i liked the net-traffic addon for ipcop ([http://firewalladdons.sourceforge.net/net-traffic.html](http://firewalladdons.sourceforge.net/net-traffic.html)) before i switched to ubuntu but i don't know perl and how to port it to ubuntu ;)

any help is appreciated
thanks

---

### Post by kivu on 2005-09-07
[QUOTE=mael]hi there
I'm searching a traffic counter for my Ubuntu Hoary headless server/router
i already search using google, sourceforge, apt-cache etc but didn't find anything useful

the main interest is a summary, how many incoming and outgoing traffic flowed through one or more interfaces on a daily, weekly, monthly and yearly basis 

graphs (keyword RRD) of this would be nice but plain numbers are necessary

the output maybe a web site but simple text based output would be good enough, too

if the counting method uses iptables statements, it has to be easy to integrate them into my own iptables script (build by fwbuilder)
in this case the best way would be to insert the statements using the fwbuilder installation routine of the iptables script

i liked the net-traffic addon for ipcop ([http://firewalladdons.sourceforge.net/net-traffic.html](http://firewalladdons.sourceforge.net/net-traffic.html)) before i switched to ubuntu but i don't know perl and how to port it to ubuntu ;)

any help is appreciated
thanks[/QUOTE]
 You mention the RRD keyword did you check out the RRD site [http://people.ee.ethz.ch/~oetiker/webtools/rrdtool/](http://people.ee.ethz.ch/~oetiker/webtools/rrdtool/) ? That should be the tool for you

---

### Post by TheDanMan on 2005-09-07
You may also look at webalizer.  I believe it is in the repositories.

---

### Post by mael on 2005-09-08
[QUOTE=kivu]You mention the RRD keyword did you check out the RRD site [http://people.ee.ethz.ch/~oetiker/webtools/rrdtool/](http://people.ee.ethz.ch/~oetiker/webtools/rrdtool/) ? That should be the tool for you[/QUOTE]
i know that tool already but i don't want to write the scripts myself, there got to be an out-of-the-box solution for this

[QUOTE=TheDanMan]You may also look at webalizer.  I believe it is in the repositories.[/QUOTE]
that's an analyzer for logfiles from webservers, but i need a tool for gathering statistics about network interfaces!

---

### Post by lao_V on 2005-09-08
Is this what you are looking for?

[MRTG]("http://people.ee.ethz.ch/%7Eoetiker/webtools/mrtg/")

---

### Post by mael on 2005-09-08
[QUOTE=][/QUOTE]
 afaik MRTG only creates graphs but doesn't say tell the amount of traffic

---

### Post by lao_V on 2005-09-08
[QUOTE=mael]afaik MRTG only creates graphs but doesn't say tell the amount of traffic[/QUOTE]

Surely it would have to create logs from which to create the graphs???!! I haven't looked into it in detail but have a look at the [manual.]("http://people.ee.ethz.ch/%7Eoetiker/webtools/mrtg/mrtg-reference.html")
The logs should be in /www/mrtg/logs by default??

---

### Post by mael on 2005-09-08
[QUOTE=mael]i know that tool already but i don't want to write the scripts myself, there got to be an out-of-the-box solution for this[/QUOTE]

...

---

### Post by LordHunter317 on 2005-09-08
Cacti will provide graphical viewing of your systems, and is far better than mrtg.

If you need more than that, ntop may be your only worthwhile recourse.

---

### Post by mael on 2005-09-08
i don't want to use SNMP and i didn't find a "nice" way to use cacti without SNMP to make statistics of local interfaces

i tried ntop and i would use it - if this server/router would be a 2 Ghz box with 1 GB of RAM :D
when i turned it on, the machine was almost unusable if i moved some files across the network ;)
it's a P3 800 Mhz/384 MB and it's currently using 30 MB swap space :\

---

### Post by mael on 2005-09-18
[QUOTE=][/QUOTE]
 i found what i was looking for: vnstat
that's _exactly_ what i needed

---

