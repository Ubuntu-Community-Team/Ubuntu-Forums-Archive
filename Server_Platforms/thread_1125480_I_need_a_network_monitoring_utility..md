---
title: "I need a network monitoring utility."
date: 2009-04-14
forum: Server Platforms
---

### Post by Underpants on 2009-04-14
This is posted in the Server forum instead of networking, because networking is full of people trying to get their wifi working and that's about it. Server people know server software :KS

I need to monitor traffic on an internet connection. For the sake of this thread, this is how things are set up. 

[internet] <-> [router] <-> [firewall] <-> [my cool Linux box] <-> [network switches] <-> [client computers]

From the Linux box I would like to be able to pinpoint something like a particular workstation sending tons of spam. So I’d like to be able to see that a particular workstation has traffic going out on port 25. Or I would like to be able to see a graph and find out where traffic spikes are coming from, or where they’re going. 

I am familiar with NTOP and IPTraf. Both of these utilities are very useful but I am wondering if there is anything I can use in addition to these to make this system a little more useful.

---

### Post by dguitar on 2009-04-14
[Nagios]("http://nagios.org/") with the right plugins can do everything you are looking for.

---

### Post by koenn on 2009-04-14
ntop sounds like the tool for what you're trying to do. 
For the specifiek spam issue, ethereal (wireshark) with a filter for port 25 wuld give you a good idea. 
and Nagios can monitor pretty much anything, given the right configuration

---

### Post by BDNiner on 2009-04-14
At a previous job we used PRTG - Paessler Router Traffic Grapher. It is a freeware windows application. I have been looking for some linux alternatives for a while.

---

### Post by wirelessmonkey on 2009-04-14
cacti [http://www.cacti.net]("http://www.cacti.net")

---

### Post by snakdoc on 2009-04-15
i like iptraf personally

---

### Post by koenn on 2009-04-15
> **BDNiner said:**
> At a previous job we used PRTG - Paessler Router Traffic Grapher. It is a freeware windows application. I have been looking for some linux alternatives for a while.

MRTG ?
[http://oss.oetiker.ch/mrtg/](http://oss.oetiker.ch/mrtg/)

---

### Post by koenn on 2009-04-15
I once made a list of 'network tools I ought to check out some time'. Never got much beyond listing them, but maybe you see something that's wort investigating further

[http://users.telenet.be/mydotcom/howto/linux/netmon.htm](http://users.telenet.be/mydotcom/howto/linux/netmon.htm)

---

### Post by Underpants on 2009-04-15
Programs like MRTG and Cacti do not have granular monitoring of a specific device. They let you see the total bandwidth of a specific router but I need to know more detail. 

MTRG and Cacti type programs say "You spent $1000 dollars this month" I need to know that I spent 100 on this, 250 on that, 75 on this other thing. 

IPtraf really is an awesome product, but it's a bit clunky to use if you need to filter things.

---

### Post by Underpants on 2009-04-15
> **koenn said:**
> I once made a list of 'network tools I ought to check out some time'. Never got much beyond listing them, but maybe you see something that's wort investigating further

[http://users.telenet.be/mydotcom/howto/linux/netmon.htm](http://users.telenet.be/mydotcom/howto/linux/netmon.htm)

Awesome! There's some cool stuff in there!

---

### Post by wirelessmonkey on 2009-04-15
> **Underpants said:**
> Programs like MRTG and Cacti do not have granular monitoring of a specific device. They let you see the total bandwidth of a specific router but I need to know more detail. 

MTRG and Cacti type programs say "You spent $1000 dollars this month" I need to know that I spent 100 on this, 250 on that, 75 on this other thing. 

IPtraf really is an awesome product, but it's a bit clunky to use if you need to filter things.

If you run snmp on your devices, you can get device specific, granular monitoring of services, network traffic, interfaces, mem usage, etc... cacti can be configured to poll as often as you'd like, for any snmp walkable returnable value.

---

### Post by Underpants on 2009-04-15
> **wirelessmonkey said:**
> If you run snmp on your devices, you can get device specific, granular monitoring of services, network traffic, interfaces, mem usage, etc... cacti can be configured to poll as often as you'd like, for any snmp walkable returnable value.

Hmm. I stand corrected. I will dig a little deeper into SNMP terminology and specifications. Thanks for the tip.

---

### Post by BDNiner on 2009-04-15
> **koenn said:**
> MRTG ?
[http://oss.oetiker.ch/mrtg/](http://oss.oetiker.ch/mrtg/)

Great, who knew that you just had to replace 1 letter!

---

