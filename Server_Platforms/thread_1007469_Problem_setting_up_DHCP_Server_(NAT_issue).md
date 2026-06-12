---
title: "Problem setting up DHCP Server (NAT issue?)"
date: 2008-12-10
forum: Server Platforms
---

### Post by Kermos on 2008-12-10
I'm having some problems getting my server configured for DHCP.

The actual DHCP part seems to be working ok. I can hook up systems to the server and they're given addresses as they should be and can see each other on the local area network.

However, they can't access the outside world.

Eth0 is connected to the incoming connection from the outside.
Eth1 is where the clients connect for the DHCP server.

I'm using the script at

[http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/firewall-examples.html#RC.FIREWALL-IPTABLES](http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/firewall-examples.html#RC.FIREWALL-IPTABLES)

to setup my ip forwarding and i've run all the tests at [http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/testing.html](http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/testing.html) and all of them succeed until 5.8

I'm pretty much totally out of ideas at this point in time.

Any suggestions would be greatly appreciated!

Thanks!

---

### Post by Kermos on 2008-12-10
Solved the problem, came out to a typo in the script that sets up the iptables. Everything is solved now. =)

---

