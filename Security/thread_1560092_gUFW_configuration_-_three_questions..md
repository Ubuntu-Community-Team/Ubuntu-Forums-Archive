---
title: "gUFW configuration - three questions."
date: 2010-08-24
forum: Security
---

### Post by zozza on 2010-08-24
Hello, 

After reading suggestions from people on these forums I have changed my firewall client from Firestarter to gUFW.  

I have three questions.

1.  Just to confirm that gUFW modifies the iptables and the modified iptables will load on startup (even if the gUFW client does not load).  Yes?

2.  Currently for "outbound" traffic I allow: HTTP / HTTPS / Secure IMAP / Secure POP3 / Secure SMTP / and alternative HTTP on 8080.  I have not permitted DNS on port 53 but my understanding is that this is no longer necessary and anyhow the web works.  

All of these are TCP only (no UDP).  Does anyone think I have left something out (I mean something generic - I will add Skype, for example, next time I use it).  

3.   I have a direct internet connection (no NAT).  Currently my "incoming" is set to "deny" but there is nothing in the table.  Should it just be left blank or does anyone have any suggestions for a connections of my type?

Thanks.

---

### Post by uRock on 2010-08-24
For incoming, as long as the box has nothing listed, then there are no exceptions. Incoming connections will not be allowed. To test this theory, you can go to the shields up site and let it run a port scan to tell how well your firewall is set up.

---

### Post by Soul-Sing on 2010-08-25
> **uRock said:**
> For incoming, as long as the box has nothing listed, then there are no exceptions. Incoming connections will not be allowed. To test this theory, you can go to the shields up site and let it run a port scan to tell how well your firewall is set up.

True, but be aware of the fact that grc shieldsup tests your hardware modem/router if you are behind such a device, zenmap/nmap
is a better way to stress your system, and see if there are open ports.
You could also stop deamons/services on your system, if you do not use them.
Is it also possible to limit outgoing traffic with UFW.

---

