---
title: "Isc-dhcp-server help"
date: 2012-07-12
forum: Server Platforms
---

### Post by jwsicomputing on 2012-07-12
Hi there,

I have isc-dhcp-server up and running perfectly, but the thing is none of the clients are able to get internet access. I think the problem lies in my iptables which i think i have messed up:

my ip tables photo is attached if you could look and identify any errors that would be great.


Basically internet/WAN is on eth1 and DHCP clients are on eth0

If you need any other info don't hesitate to ask.

Many thanks,
James

---

### Post by SeijiSensei on 2012-07-15
Did you enable TCP packet forwarding in /etc/sysctl.conf?  Find the line that reads "net.ipv4.ip_forward=1" and enable it by removing the hash mark at the beginning of the line.  Forwarding is disabled by default as a security precaution.

You can simply reboot at this point, but you can do a couple of simple things at the command line to enable forwarding without rebooting:

1)  First check to see that forwarding is disabled by running "cat /proc/sys/net/ipv4/ip_forward".  If it returns zero, that's the problem.

2)  Turn on forwarding by running "sudo echo '1' > /proc/sys/net/ipv4/ip_forward".  See if your clients can connect now.

---

