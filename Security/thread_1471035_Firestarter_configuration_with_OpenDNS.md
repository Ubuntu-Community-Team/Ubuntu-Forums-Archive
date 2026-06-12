---
title: "Firestarter configuration with OpenDNS"
date: 2010-05-03
forum: Security
---

### Post by olki on 2010-05-03
Hello,

I needed to secure the my local network so I've installed a Ubuntu machine running Firestarter as a internet firewall. Now I would like to use OpenDNS to achieve web filtering and therefore I need to add some rules to allow DNS traffic (port 53) on to OpenDNS servers, like:

iptables -A FORWARD -p udp -m udp -d 208.67.222.222 --dport 53 -j ACCEPT
iptables -A FORWARD -p tcp -m tcp -d 208.67.222.222 –dport 53 -j ACCEPT
iptables -A FORWARD -p udp -m udp -d 208.67.220.220 –dport 53 -j ACCEPT
iptables -A FORWARD -p tcp -m tcp -d 208.67.220.220 –dport 53 -j ACCEPT
iptables -A FORWARD -p udp -m udp –dport 53 -j DROP
iptables -A FORWARD -p tcp -m tcp –dport 53 -j DROP

I can't do it, because it seems that Firestarter does not allow exceptions on blocked traffic. Is it correct? I had a look at Gufw but it looks the same. It would probably possible with the iptables, but as I'm using Firestarter now, I don't know how to switch to Iptables.

Thank you for your help.

---

### Post by dino99 on 2010-05-03
[http://www.linuxsecurity.com/content/section/9/161/](http://www.linuxsecurity.com/content/section/9/161/)
[http://bodhizazen.net/Tutorials/psad/](http://bodhizazen.net/Tutorials/psad/)

---

### Post by Cosma on 2010-05-03
if you want to use that box just as firewall, then you should take a look at [http://www.pfsense.org](http://www.pfsense.org)

---

### Post by Jive Turkey on 2010-05-03
You need to rethink your whole approach I believe.  Firstly, Firestarter is obsolete, use ufw or gufw.  Also, you might want to set up the server to be your DNS and get its settings from OpenDNS.

There are some whole distros set up specifically for use as a firewall that you might want to look into.  If your intention is to restrict what the other computers on your LAN can get access, then I suggest you look into installing and configuring the box as a proxy server.

---

