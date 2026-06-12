---
title: "Please help me find a server monitoring agent"
date: 2009-12-11
forum: Server Platforms
---

### Post by ddixonr on 2009-12-11
Sorry about the non-ubuntu question. Anyone know of a server monitoring agent I can install to monitor our red hat server? I just need something simple that will *email me when network activity is crazy high, or when it loses connectivity. A plus would be disk usage alerts, but not required.

*very much required

---

### Post by bodhi.zazen on 2009-12-11
Have you looked at something like webmin ?

---

### Post by ddixonr on 2009-12-11
This seems pretty complicated for my simple task. I'm scared. :^) Just kidding, but it does seem rather complex to setup. What else ya got? Thanks for the ideas!

---

### Post by mbaas on 2009-12-11
Nagios perhaps?

---

### Post by xkaliburx on 2009-12-11
Nagios is excellent but a lot to setup, you can look at groundwork [http://www.groundworkopensource.com/network-management-software.html]("http://www.groundworkopensource.com/network-management-software.html") or something a bit easier, there is always big brother [http://www.bb4.org/download.html]("http://www.bb4.org/download.html")

The only thing is you did mention for it to email when it loses connectivity, which if it did couldn't email you which is why your monitor is usually not the same box as the one you want to monitor, but hey, the above are both recommended.

---

### Post by ddixonr on 2009-12-11
Great. I'll check these out. Thanks guys.

---

### Post by munky99999 on 2009-12-11
Cacti

Cacti is really easy to get going and collecting. Getting it to spit out the graphs and understanding them is much harder.

[https://help.ubuntu.com/community/Nagios2](https://help.ubuntu.com/community/Nagios2)

[https://help.ubuntu.com/community/Logwatch](https://help.ubuntu.com/community/Logwatch)

---

### Post by benjaminsuman on 2009-12-11
We use Zabbix for our server and network monitoring.  The documentation is pretty good and it's not too hard to set up.

[www.zabbix.com]("http://www.zabbix.com")

---

### Post by koenn on 2009-12-11
> **xkaliburx said:**
> Nagios is excellent but a lot to setup, 

it's not really that much to set up. If he just wants to monitor connectivity to 1 server, all he'd have to do is write 1 host definition (copy/paste from a default and change a fe lines), and put his email address in the contact info. 

For additional monitoring (eg disk free space), you'd have to define a service, again, copy, paste, edit. 

And I agree Nagios would be an excellent choise - this is eactly what is was made for

It's only when you have a large network or many separate services you want to monitor, that setting up Nagios takes some preparation in making templates and organizing your cfg files to keep things scalable.

---

### Post by craigp84 on 2009-12-11
Monit & Munin. Both trivial to setup and not overkill for a 1 server deployment.

---

### Post by tgalati4 on 2009-12-11
ruptime

---

### Post by ian dobson on 2009-12-12
Hi,

Have a look at munin. I'm using it to monitor my home/video server. Quite easy to setup and writing plugins is really easy, you can write a plugin in any language that outputs text to stdout (bash,perl,php,phython,C).

You can see examples here:- [http://mail.planet-ian.com/munin/](http://mail.planet-ian.com/munin/)

regards
Ian Dobson

---

### Post by blue_ on 2009-12-12
Have a look at SIM it monitors more less everything and is really easy to setup and modify if you have other services you wish to have it monitor. like do a tcpdump and if your network traffic is over a certain limit notify you. 

[http://www.rfxn.com/projects/system-integrity-monitor/](http://www.rfxn.com/projects/system-integrity-monitor/)

If thats not something your interested in here is a list of different options [http://www.topology.org/comms/netmon.html](http://www.topology.org/comms/netmon.html)

---

