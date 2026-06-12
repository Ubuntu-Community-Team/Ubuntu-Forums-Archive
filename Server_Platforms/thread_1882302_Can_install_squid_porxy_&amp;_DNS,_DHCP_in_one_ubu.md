---
title: "Can install squid porxy &amp; DNS, DHCP in one ubuntu server."
date: 2011-11-17
forum: Server Platforms
---

### Post by krishanthan on 2011-11-17
Dear Friends, 

i am new to Ubuntu, i want to know can i install Squid proxy server & DNS,DHCP in one Server. if it's possible please write the step. i have IBM X225 server, those option can do in this server(2.4 GHz x 2, 1GB x 2 RAM, 40GB x 2 HDD). please write the way of configuration. Virtual Machine needed also no problem but need guides to me.

thank you.

---

### Post by SeijiSensei on 2011-11-17
> **krishanthan said:**
> i am new to Ubuntu, i want to know can i install Squid proxy server & DNS,DHCP in one Server. if it's possible please write the step.

That's why people write documentation.  I'd start with the [Ubuntu Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html").

Quick summary:

1) Make sure you have two NICs, one pointing to the Internet, one connected to the internal network.

2) DNS and DHCP are provided by servers that are packaged with Ubuntu Server.  See the Guide.

3) For squid, do a Google search for "squid transparent proxy" and also read up on redirecting outbound port 80 requests using iptables.

---

### Post by krishanthan on 2011-11-18
Thanks lot, i will do and see. if any problem help me.

thanks again

---

### Post by bonezie121 on 2011-11-19
Actually you can do it with a single nic and an IPTables rule, but only advisable if its behind a pre-existing firewall.  Just google Squid with one nic and use information from all of them to get this working.  I will state though, 2Gb is kinda a small amount of ram for all of that setup.  I would suggest 4Gb minimum as the speed actually comes from Squid pulling from RAM and not cached to the hard drive as the hard drive is slower.  Though don't get me wrong, it will pull from the drive when needed though.  Search Squid3 on google and you will find bunch of info.  Mines not perfect by any means, but I've attached my squid.conf (squid.txt) file so you can see some of the MANY things that can be done with Squid.  I also have dhcpd server setup and Bind9 for DNS.  the dhcpd server allows me to send updated gateway/router/dns information to the clients.  But again i strongly suggest having at least 4Gb, I've got as many as 20 people surfing on mine and it uses about 68% of 8Gb just on Squid.  Setup bind9 to cache and it'll work beautifully, but does use a little bit on ram too.  Good luck, and let us know if you have any other problems, and remember the search option on this site is a beautiful thing.

---

