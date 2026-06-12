---
title: "Tips on properly securing a local BIND9 DNS server"
date: 2010-04-30
forum: Security
---

### Post by CharlesA on 2010-04-30
Hi all,

I've set up a DNS server on my local network to do local dns resolution. It is a single master zone on the local LAN. I think it's also set to do internet lookup as well, since there are no entries telling it to forward outside lookup requests to (whatever) DNS servers.

Since it is only going to be used locally and not be placed "on the internet" outside of my firewall, are there anything specific I need to do to secure it?

Thanks.

---

### Post by noway2 on 2010-04-30
From my experience, placing it behind the firewall and not opening the port (53 I think it is) will keep you pretty safe. I have not had anyone try to make unauthorized access to my DNS server (yet).  If you used Bind, there is a setting in the configuration that you can enable (or not) allowing remote connections.  Even when I have tried to enable it and opened the port in the router it didn't work for me.

---

### Post by CharlesA on 2010-04-30
Thanks for the reply. It's currently behind both the firewall on my router and an iptables firewall on the server itself.

I've read a couple pages like the one [here]("http://corpocrat.com/2009/02/21/how-to-secure-your-dns-server/") that suggest doing all sorts of stuff to the conf file, but I don't know what would be the best things to do, since this server is behind a firewall and isn't accessible from the internet (as far as I know).

---

### Post by CharlesA on 2010-05-01
Decided to turn off recursive lookups and set my DHCP server to provide the IP of my IPS's DNS for regular lookups.

That should be theoretically more secure.

---

### Post by MechaMechanism on 2010-05-03
By default Bind9 in 9.10 and 10.04 does not allow external queries.  In other words my Bind9 is connected directly to the Internet with no firewall rules.  Regardless the outside world can not connect.  However the ports do respond to ICMP with closed.  All thats needed is to add the below into named.conf.options:

listen-on-v6 { ::1; };
listen-on { 127.0.0.1; };

There are no other config changes needed unless you have opened yourself to the outside world.

---

### Post by CharlesA on 2010-05-03
Oh, thanks. :)

I guess I am fairly safe then.

---

