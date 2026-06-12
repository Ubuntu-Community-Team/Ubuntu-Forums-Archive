---
title: "Port Blocking"
date: 2006-12-26
forum: Server Platforms
---

### Post by gre7g on 2006-12-26
It appears that my new Ubuntu server is blocking requests from outside of 192.168.0.*.  Why would it do that?

If I try to surf apache from within the LAN, then I have no problems.  I can see the website I'm hosting just fine, however, users from the WAN cannot.  I do have a firewall with NAT, but it is configured the same way it has always been set up before.  If I run Ethereal and sniff the traffic, I can see SYNs from the outside world go to my server, but there is never a SYN/ACK reply (unless I initiate the traffic from the LAN).

I don't see anything suspicious in iptables.

$ sudo iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Does anyone know what I should check?

Many thanks,

Gre7g

---

### Post by Brazen on 2006-12-26
Do you have "Order deny,allow" and "Allow from all" directives in your Apache config?

---

### Post by rickyjones on 2006-12-26
Do you have your router forwarding the correct ports?

---

### Post by gre7g on 2006-12-26
Yes, there are various Order Allow, Deny & Allow all type statements in the Apache configuration.  I just copied the default and put in my virtual server information, so I didn't do anything fancy there.  I looked at the statements and none of them seem suspicious.  Besides, if it was Apache rejecting the traffic, I would expect to see an error in the log or the TCP connection being completed and then rejected.  As it is now, the connection is just never ACKed.

Yes, I do have port 80 being forwarded to the correct IP address in the firewall configuration.  I am sniffing on the LAN so I know the firewall is attempting to forward the connection to the server.  The problem is that the server is ignoring requests that come from the IP addresses of the outside world.

Gah!  Why me?

---

### Post by gre7g on 2006-12-26
I got it!

It turns out that I was missing a gateway statement in /etc/network/interfaces.  The machine could find local address, but without a gateway, it couldn't understand how to forward.

Thanks for the help!

Gre7g

---

