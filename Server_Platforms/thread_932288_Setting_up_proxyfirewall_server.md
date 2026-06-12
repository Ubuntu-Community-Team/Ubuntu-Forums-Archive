---
title: "Setting up proxy/firewall server"
date: 2008-09-28
forum: Server Platforms
---

### Post by Smithamax on 2008-09-28
I want to set up a server with the following things
Squid Proxy
DHCP
Firewall
some kind of D/L Quota thing
and maybe DNS but i don't really need that

and webmin to manage it all

the main thing I want to know is if its okay to have all this stuff on the same box, mostly the Firewall and Proxy

Thanks, Smithamax

---

### Post by jamesrfla on 2008-09-28
Ubuntu already has a firewall called iptables so you don't need to do anything with that. Hear is webmin [http://sourceforge.net/project/downloading.php?groupname=webadmin&filename=webmin_1.430_all.deb&use_mirror=internap](http://sourceforge.net/project/downloading.php?groupname=webadmin&filename=webmin_1.430_all.deb&use_mirror=internap)
To get a DHCP server, DNS, and squid server do ```
sudo apt-get install dhcp3-server pdns-server squid3
``` in terminal.

---

### Post by Smithamax on 2008-09-28
but is it okay to have the proxy and firwall on the same box?

---

### Post by jamesrfla on 2008-09-28
It should be okay.

---

