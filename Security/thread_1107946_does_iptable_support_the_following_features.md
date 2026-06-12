---
title: "does iptable support the following features?"
date: 2009-03-27
forum: Security
---

### Post by firsttimeuser on 2009-03-27
Hello everyone, 

I am trying to setup a relaying box which will be used to relay some TCP and udp traffic. basically, what I want is let this box relay all the defined traffic while at the same time keeping the original IPs unchanged. 

I have been using iptable for a while, but only on the firewall side, so before I spend a lot time researching this, can any of you tell me if it is possible for iptable to perform such functionality? and which keyword should i be looking for? thanks a lot!

---

### Post by cdenley on 2009-03-27
Sounds like DNAT to me.
[http://linux-ip.net/html/nat-dnat.html](http://linux-ip.net/html/nat-dnat.html)

---

### Post by HermanAB on 2009-03-27
Iptables also has something called 'redirect':
[http://www.linuxtopia.org/Linux_Firewall_iptables/x4508.html](http://www.linuxtopia.org/Linux_Firewall_iptables/x4508.html)

---

### Post by firsttimeuser on 2009-03-27
it seems redirect is only used to redirect packets to the machine itself.

> **HermanAB said:**
> Iptables also has something called 'redirect':
[http://www.linuxtopia.org/Linux_Firewall_iptables/x4508.html](http://www.linuxtopia.org/Linux_Firewall_iptables/x4508.html)

---

### Post by lensman3 on 2009-03-27
You need a form similar to:

$IPTABLES -t nat -A PREROUTING -i $EXTERNAL -p tcp --sport 1024:65535 -d $EXT_IP --dport $GTK_GNUTELLA -j DNAT --to-destination 192.168.200.10:$GTK_GNUTELLA



EXTERNAL=ethx
$GTK_GNUTELLA=<some port number>   This is sync'ed  with gtk_gnutella listening port in the program.

--to-destination <IPNUMBER>. My IPnumber 192.168.200.10 is inside the firewall, but should work to forwardable Internet IP number.

--sport is set to the range of 1024:65535 for security reasons.  Ports below 1024 are usually consider privileged.

I've set this up for SKYPE,GTK_GNUTELLA, Bitstream (both udp and tcp connections)

Hope this helps.

---

### Post by firsttimeuser on 2009-03-30
much appreciated for the info.

Never used NAT before, and I think i will need to add a secondary and private ip on that destination loghost.

looking into nat now...


> **lensman3 said:**
> You need a form similar to:

$IPTABLES -t nat -A PREROUTING -i $EXTERNAL -p tcp --sport 1024:65535 -d $EXT_IP --dport $GTK_GNUTELLA -j DNAT --to-destination 192.168.200.10:$GTK_GNUTELLA



EXTERNAL=ethx
$GTK_GNUTELLA=<some port number>   This is sync'ed  with gtk_gnutella listening port in the program.

--to-destination <IPNUMBER>. My IPnumber 192.168.200.10 is inside the firewall, but should work to forwardable Internet IP number.

--sport is set to the range of 1024:65535 for security reasons.  Ports below 1024 are usually consider privileged.

I've set this up for SKYPE,GTK_GNUTELLA, Bitstream (both udp and tcp connections)

Hope this helps.

---

