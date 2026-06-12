---
title: "If I have two lancards"
date: 2011-07-11
forum: Server Platforms
---

### Post by Rakeshvijayan on 2011-07-11
This is only my doubt in DNS .if I have two lancards on server and I did nat with eth0 ip is 192.168.1.20 and eth1 ip is 200.168.14.1 .and wish to install dns on the same server .eth0  is for internet and eht1 for my internal networks .which address will I take for DNS .

dont feel any thing about me .I have a little time on this world I need to study administration in linux

---

### Post by haqking on 2011-07-11
that dont make much sense.

eth0 is a private class c ip address so when you say it is for internet you mean it is NAT behind a router ?

and when you say you want your own DNS server, for what ? your own internal lan ?

---

### Post by Rakeshvijayan on 2011-07-12
yes I need a DNS server for my Internal network .I have only one server system .......

---

### Post by 1clue on 2011-07-12
Are you passing anything from outside into the firewall?  Meaning, can somebody from Starbuck's in Pittsburgh hit your server from outside, or is there a firewall keeping all outside queries from entering?

The most common setup would be that you have no more than one system visible from outside, if that.  That means your ISP has the DNS for the public address, and the DNS is for inside.

Not sure which DNS you are using, but generally they have provision in the configuration to bind multiple names to a single IP as well as binding multiple IPs to the same name in a round robin or similar.

Maybe you can outline what you have going on.  There are just too many wacky possibilities to guess more than I have.

---

### Post by Rakeshvijayan on 2011-07-12
dear frends I need to configure DNS on the same system which I did NAT .....

---

### Post by Rakeshvijayan on 2011-07-12
Please check the site [http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server ]("http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server")

This is what I need to know but doubt in configuration eth0 adapter if it is static can we do nat? and set up dns?

am not expert on here that why ....do my question clear

---

### Post by Rakeshvijayan on 2011-07-13
I leave this issue .I configured nat on 1 pc and going to set up dns and dhcp on another pc

---

