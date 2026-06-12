---
title: "What DNS server can handle this?"
date: 2008-11-20
forum: Server Platforms
---

### Post by ssavoy on 2008-11-20
Our high school will be deploying hundreds of laptops to the student body soon, however we need to control internet access while the students are at home as well. We will be setting up a public DNS Server at school with forwarders to OpenDNS.

Our server will be running Ubuntu Server 8.04 LTS on an HP rack server that's about 4 years old. It has 1GB of RAM, so what will be the best DNS server to use assuming the possibility of close to near 1,000 simultaneous connections (if everyone uses their laptop at the same time...probably won't happen).

Is dnsmasq and bind9 different, or is bind9 always required regardless? 

We have a 30mbps connection to the net so we can afford the bandwidth for a public DNS.

---

### Post by bab1 on 2008-11-21
Why do you need DNS for the students?  Maybe they only need to have a public DNS server that is referred to them when the get an IP address via DHCP.  

If you do have a need for internal (private) mapping of IP to hostname you probably should look into BIND9.  DNSmasq might be a little lightweight for your needs.  DNSmasq does not to MX and other DNS type records.  It only maps hostnames to IP.  And if you you need  dynamic DNS, I'm not sure DNSmasq will do that either.  I am sure that BIND9 does it all.

---

