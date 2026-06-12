---
title: "Problem relaying Mail - postfix, untangle, exchange"
date: 2009-01-12
forum: Server Platforms
---

### Post by JamesN1830 on 2009-01-12
In the DMZ I have a untangle box and postfix box.  Smtp only.

In trusted network I have a exchange 03 box.

From the Untangle and Postfix boxes I can telnet on port 25 to the exchange box and successfully send a message.

If I attempt to relay mail to the exchange box from either in the DMZ, they fail.

I have whitelisted globally the IP's of the DMZ on the exchange box.

I have ran a pcap on the exchange box but never see any traffic from the dmz boxes when doing a test send.

What am I missing that's blocking messages to be sent from dmz to exchange on trusted?

Firewall is a watchguard btw.


MORE INFO



I can relay from untangle through postfix and send a test email from DMZ to my yahoo account.

If I send a test from untangle relayed through postfix dest to a internal email address, I see it hit the firewall for a DNS request then send to my MX record address which is the public IP of the firewall.  At that point I see the firewall process it and then nada.  Never see anything from the pcap on the exchange (in case it was being flagged as spam).

I'm a bit stumped.  Not sure if the firewall is the issue or the setup of the postfix.

---

### Post by JamesN1830 on 2009-01-12
I think it boils down to this...


for a email destined for my internal network, postfix is doing a MX lookup and sending it to the MX record IP which equals my eth0 interface of the firewall (public IP)....  How can I tell post fix to just send it to the exchange server internal IP instead?

---

### Post by JamesN1830 on 2009-01-12
Got it working...


> A logical line starts with non-whitespace text. A line that starts with whitespace continues a logical line. 

yeah, so my transport arguement had a space at the start of the line.  Works like a champ now and does not do a MX lookup for relay domain.

---

