---
title: "iptables dnat working, but server logs local source IP instead of original source IP"
date: 2008-02-14
forum: Server Platforms
---

### Post by nothsa on 2008-02-14
I have a mail server on a local network ( 192.168.233.128 ), and I am forwarding/redirecting SMTP and POP3 traffic from the Firewall machine to the mail server with the following iptables DNAT rules:

iptables -t nat -A PREROUTING -d $FIREWALL_EXTERNAL_IP -p tcp --dport 25 -j DNAT --to-destination 192.168.233.128:25
iptables -t nat -A PREROUTING -d $FIREWALL_EXTERNAL_IP -p tcp --dport 2525 -j DNAT --to-destination 192.168.233.128:25
iptables -t nat -A PREROUTING -d $FIREWALL_EXTERNAL_IP -p tcp --dport 110 -j DNAT --to-destination 192.168.233.128:110

This forwards correctly (i.e. all traffic on those 3 ports is redirected to the mail server), but the logs of the mail server say that all the connections are coming from 192.168.233.1 (i.e. the Firewall's IP for the local network). Apart from being annoying because I don't know what IP the mail is actually coming from, the server is rejecting some mail from domains with SPF entries, which is a big problem.

Does anyone know how I can set up the forward/redirect so that my mail server will log the original source IP address (i.e. the server sending the mail) instead of the Firewall's IP address?

---

### Post by nothsa on 2008-02-14
Solved!

The mail server is actually a VMWare virtual machine, and I had set it up with a "host-only" network card, which appears to add an SNAT value to make everything appear to be coming from the Firewall's local IP (in this case, 192.168.233.1).


Here's what I did, if anyone is facing the same problems:

I switched the card from "host-only" to "NAT" ("bridged" would have worked too, if I had the external IP addresses to spare), and then I edited the /etc/vmware/vmnet8/nat/nat.conf file to forward the ports to the mail server (in my case: 192.168.87.128). I then set up iptables to forwarded the ports to the NAT server (in my case, 192.168.87.1).

---

