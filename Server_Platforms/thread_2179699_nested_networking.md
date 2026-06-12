---
title: "nested networking"
date: 2013-10-09
forum: Server Platforms
---

### Post by Erika_Valentine on 2013-10-09
Greetings,
I want to setup a network nested within a network.

existing network: corporate windows based network 

Ubuntu 12.04.3 Server NAT01.test.lab (3NIC's: eth0-WAN DHCP, eth1-LAN gateway Static {192.168.200.1}, eth2-LAN static {192.168.200.200} |Linux Firewall,isc-dhcp-server,bind9DNS, LAMPserver, Samba,Webmin)  Hardware= HP Proliant ML370G3 (Intel dual port PCIex card installed)

New lan: test.lab

I can get the NAT01 server to reach the internet through the existing network using webproxy.(the big corporate megolith).com and some port configuration.  I want the devices attached to test.lan to see the internet through NAT01 without needing to configure proxy settings on them.  the conversion of traffic through the proxy server of the corporate network needs to be transparent to the test.lab network and the test.lab network needs to be invisible to the big corporate megolith.

1. Is this possible?  It seems like it ought to be, but I can't find any information on how.
2. How?

Help?
-E

---

### Post by SeijiSensei on 2013-10-09
If I understand you correctly, you want packets intended to be sent to port 80 on remote machines to be forwarded to the corporate proxy instead?  You might be able to do this with an iptables rule along the lines of:

```
/sbin/iptables -t nat -A PREROUTING -o eth0 -p tcp --dport 80 -j DNAT --to-destination ip_of_corp_proxy:port
```

This sends all traffic that would normally go to the default gateway via eth0 to the IP and port specified in the --to-destination field.  This specification keeps traffic intended for port 80 on local machines, that would be going out the eth1 or eth2 interfaces, from being forwarded.  That may or may not be what you want.

Of course, you need to activate packet forwarding in /etc/sysctl.conf by setting net.ipv4.ip_forward=1.

---

### Post by Erika_Valentine on 2013-10-10
Thank You!   Thank you for your assistance I think that will work nicely.  As I understand it I simply need to make a rule for each internal port that I want to route to the proxy port.  that sounds simple enough.  Where do I tell it the address of the proxy server to talk to?
:-)
-Erika

---

### Post by SeijiSensei on 2013-10-10
> **Erika_Valentine said:**
> Where do I tell it the address of the proxy server to talk to?

The proxy's IP and port follows the "--to-destination" parameter as in the example above.

---

### Post by Erika_Valentine on 2013-10-10
AHH yes, I see that now.  thank you for the clarification.  I'm eager to implement this :-)

---

### Post by Erika_Valentine on 2013-10-14
Hello again,
when I input this:
/sbin/iptables -t nat -A PREROUTING -o eth0 -p tcp --dport 80 -j DNAT --to-destination **.**.***.195:8080

it tells me that -o is not a valid argument for PREROUTING

any thoughts?
-E

---

### Post by SeijiSensei on 2013-10-14
Oh, right.  The PREROUTING chain cannot specify the output interface, only the input one.  (The opposite principle applies to the POSTROUTING chain.)  Replace "-o eth0" with "-i eth1" and see if that works. 

Are there internal webservers that people need to reach on the 192.168.200.0/24 network?  If so, we might to do some additional fancy footwork to maintain access to them.  Otherwise all HTTP traffic will be forwarded to the proxy.

---

### Post by SeijiSensei on 2013-10-17
So, Erika, is it working?

---

