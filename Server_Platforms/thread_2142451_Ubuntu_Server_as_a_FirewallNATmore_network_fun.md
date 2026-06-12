---
title: "Ubuntu Server as a Firewall/NAT/more network fun"
date: 2013-05-05
forum: Server Platforms
---

### Post by JaredKat on 2013-05-05
Hello there!

Okay, so, I am wondering how I could use a Ubuntu Server installation on an old HP ProLiant server as a firewall, NAT/Router, DNS server, and other network goodies. 

My basic needs is that I would like this server to be able to do NAT for a network within a main network, and also do DHCP for that part of the network. I need to be able to easily port forward so the other servers behind this device can serve out to the rest of the network and to the internet, and also, I would like to do internal DNS for each of the servers behind this firewall, such as node1.local.domain.net and such. I intend for the entire network behind the firewall to be running ubuntu server, and one client running ubuntu desktop for management. 

The HP server that I want to install this on does have two onboard NIC's, and I can install more if necessary. 

Oh, and if I could also throw an intrusion detection system into the mix on this machine, that would be cool.

---

### Post by darkod on 2013-05-05
If it's a LAN within a LAN, how important is it to have a firewall active?

The NAT/routing is easy. First open /etc/sysctl.conf and look for the ipv4 forwarding option called something like net.ipv4.ip_forward=1. Enable that line (remove the # symbol at front). Save and close the file. Restart networking or the whole server.
After that you only need a MASQUERADE rule in iptables. Lets assume eth0 will be the connection to the main network, eth1 to the smaller network within. Try:
```
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

At this moment the machine on behind eth1 should have internet/access to the main network using this server as gateway (its IP on eth1).

You will put that iptables rule into a file later, and make it execute on boot.

So, that should do the routing/NAT part.

For the DNS, it depends if you want full DNS control or simply forwarding requests to public servers. For forwarding, it would be easier to use dnsmasq. For full dns service, it's probably better to use bind9.

For dhcp use what ever you feel comfortable with. Don't forget to configure it to send dhcp leases only on eth1, that is probably what you want. You don't want this server sending leases to the main eth0 network.

---

### Post by Cheesemill on 2013-05-06
Although it's possible to set up such a system using Ubuntu, I prefer using one of the speciality firewall distributions instead.

Installation and configuration will take you hours instead of days, and they all come with a web front end to make configuration easier. Personally I use SmoothWall but there are plenty of other options available.

[http://www.smoothwall.org/](http://www.smoothwall.org/)
[http://www.pfsense.org/](http://www.pfsense.org/)
[http://www.zentyal.org/](http://www.zentyal.org/)
[http://www.vyatta.org/](http://www.vyatta.org/)
[http://www.untangle.com/](http://www.untangle.com/)
[http://www.ipcop.org/](http://www.ipcop.org/)
[URL="http://m0n0.ch/wall/"]http://m0n0.ch/wall/
[/URL][http://www.clearfoundation.com/Software/overview.html]("http://http://www.clearfoundation.com/Software/overview.html")

---

### Post by corsairetc on 2013-05-07
Try to use this.
[http://www.fwbuilder.org/](http://www.fwbuilder.org/)

---

### Post by Grenage on 2013-05-07
Massive PFsense fan here (we have tonnes of them), so a +1 on that score.

---

### Post by darkod on 2013-05-07
While I have nothing against the speciality firewall distributions, I would like to remind the OP of this:
1. If the goal is to learn more about ubuntu this way, using one of the special distributions will have nothing to do with ubuntu.
2. If you think you might need additional services on that server, it depends what type of services because most firewall distributions are not designed to support many other services.

For example, VPN you might get away with, but don't expect them to run apache websites. :) Even though there should be apache for the GUI. :)

The bad side of having a full ubuntu server is that you have to learn about it and administer it. The good side is that you can do almost anything with it.
A firewall dusbution might be fast to set up (or not, depending on you), but will be quite limited for other types of services.

So, measure ten times, cut once. :)

---

### Post by Grenage on 2013-05-07
You are of course quite correct; it's really a case of horses for courses.  We have servers for certain roles; we the cut-down nature of most dedicated systems to be more reliable, and a lot quicker to replace in the event of a failure.

You'll certainly learn more by tailoring a desktop/basic OS, although I'm not sure I'd go that route in a professional environment

---

### Post by atm123 on 2013-05-07
you could try using vuurmuur- might have become old but your work with iptables becomes simpler.

---

