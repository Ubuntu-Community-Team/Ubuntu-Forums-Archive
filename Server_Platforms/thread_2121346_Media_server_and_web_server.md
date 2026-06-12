---
title: "Media server and web server"
date: 2013-03-01
forum: Server Platforms
---

### Post by NYCSavage on 2013-03-01
I have Ubuntu Server 12.10 setup on a computer as a media and file server that streams content to a separate base unit, laptop, and apple TV and would like to add a web server function to the server.

I need to add Shorewall and allow access through ports 21, 22, and 80 for the web access but what ports do I need to allow for access from my home computers for the media files?  The router already has a DMZ connected to the media server's IP address.

Thank you

---

### Post by aerokid240 on 2013-03-06
hard to help when no one knows what software you are using. You can use tcpdump/wireshark while streaming content to determine the ports that need to be open.

---

### Post by SeijiSensei on 2013-03-06
You could just permit your local network globally.  I don't use packaged firewalls like Shorewall, but the relevant iptables rule would be something like

```
/sbin/iptables -A INPUT -s 192.168.1.0/24 -j ACCEPT
```

That allows all traffic originating on the 192.168.1.0/24 network.  If the forwarding router is also in the same network space, which I'd guess it is, then you'd probably need something more limiting like

```
/sbin/iptables -I INPUT -s 192.168.1.1 -p tcp --dport 21 -j ACCEPT
/sbin/iptables -A INPUT -s 192.168.1.1 -p tcp --dport 22 -j ACCEPT
/sbin/iptables -A INPUT -s 192.168.1.1 -p tcp --dport 80 -j ACCEPT
/sbin/iptables -A INPUT -s 192.168.1.1 -j REJECT
/sbin/iptables -A INPUT -s 192.168.1.0/24 -j ACCEPT

```

That permits traffic from the router on ports 21, 22, and 80 and rejects any other traffic coming in from the Internet.  All the machines on the local network are permitted.

Of course, it might be easier to do all this on the router and use no firewall on the Ubuntu box.

---

