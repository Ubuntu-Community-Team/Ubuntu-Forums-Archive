---
title: "How do you close &quot;smtp port 25&quot;..?"
date: 2009-08-18
forum: Security
---

### Post by DonaldJ on 2009-08-18
"Shields-Up" security test website found "SMTP port-25" open, in one of my scrapper carefree/careless surfing hd's...  

Why would port-25 be open..?

How do I close port-25 permanently, given that I don't have Evolution set-up for emails..?  I use only freebie outside email accounts, namely Fastmail and Yahoo...

---

### Post by sasho_zl on 2009-08-18
Enable your firewall. The easiest way is to install gufw.

---

### Post by cariboo on 2009-08-18
You may have an email server running, shut that down.

---

### Post by HermanAB on 2009-08-18
You probably have Postfix installed and running.

---

### Post by sasho_zl on 2009-08-18
There are a few ways to see what mail server is running on that port. The easiest is to open a terminal and type:** telnet localhost 25**
When you connect the server will identify itself with a greeting message. It's probably Postfix.  You can remove it from synaptic.

---

### Post by hessiess on 2009-08-18
What is the structure of your network/how is your computer connected to the net?

Shields-Up tests the open ports on the device which has your public IP adress, which is normally a NAT router(wireless router), if your machine is connected through a NAT changing the local firewall settings will have no effect whatsoever. Check the port-forwarding settings on your router, and disable UpNP then restart the router (unplug it).

Listen to episodes 3, 25, 26 and 27 of the Security Now! pod cast, also from GRC [https://www.grc.com/securitynow.htm](https://www.grc.com/securitynow.htm)

---

### Post by Rob_H on 2009-08-18
If you've checked your computer and firewall and don't see a problem there, it's also possible your ISP is intercepting traffic on that port. I have heard of ISPs doing this as a "protective" measure for their customers, although usually the symptom is the opposite of what you're seeing: A person is *trying* to run a mail server, but traffic to port 25 is blocked by the ISP.

---

### Post by DonaldJ on 2009-08-18
Thanks!..  I looked at UFW, but couldn't figure how to block things with it...  All it says is "firewall is enabled"...

I uninstalled Postfix, then tested it with Shields-Up again..  Everything got a stealth rating, but it answered a ping...
What do I need my PC answering pings for?  
How do I shut answering-pings off?

---

### Post by sasho_zl on 2009-08-19
When  packets is sent to one of your machine ports there are 3 ways those packets can be processed:
1 - packets can be received on that port because a service is listening (waiting) for connection there. The port is reported open
2 - The packets are refused with a message informing the other computer about the refusal. That way the other computer can't connect to your machine on this port but it is informed that your machine is switched on and is connected to the internet.
3 - The packets are silently dropped without sending a message to the other computer. That way your computer seem like it's switched off or even that there is no computer connected to the internet  on this IP address. This is called Stealth. Have in mind that most of the network scanning tools can detect and scan a computer even when he is in stealth mode.
About the pings you can see if there is a ICMP shutdown  option in gufw and enable it. That way your machine will not reply to a ping request. Unless you need to ping your machine to run a dignostic on your network you don't need ping enabled.

---

