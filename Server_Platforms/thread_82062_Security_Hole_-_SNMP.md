---
title: "Security Hole - SNMP?"
date: 2005-10-25
forum: Server Platforms
---

### Post by Terrik on 2005-10-25
Hi all,

I have recently set up a server with Ubuntu 5.10. I am trying to secure my system, so I did a scan with Nessus and it comes up with one security hole notice. The details report this:

SNMP Agent responded as expected with community name: snmp
SNMP Agent responded as expected with community name: openview

I am pretty new to Linux so I don't know exactly how to close these. I tried doing some searches online and on these forums, and I have not come up with much in pertaining to this/these holes. Can anyone out there help me close them? Much appreciated.

---

### Post by sunset_studies on 2005-11-02
Are you intending to do any remote monitoring of this server via SNMP? (e.g. with [Cacti]("http://cacti.net/"))

... If you're not intending to remotely monitor the server, just :

apt-get remove snmpd

... if you do want to remotely monitor this particular server via SNMP, you should change some of the default values in /etc/snmp/snmpd.conf (the file tells you which ones).

'bye.

P.S. [http://en.wikipedia.org/wiki/Simple_network_management_protocol](http://en.wikipedia.org/wiki/Simple_network_management_protocol)

---

### Post by Terrik on 2005-11-02
Ok thank you.

I don't even want SNMP on my computer, but when I go to remove it in Synaptic, it wants to remove desktop-ubuntu also, which I kind of need. I'll see if I can mess around in the config file and close these things up, then.

---

