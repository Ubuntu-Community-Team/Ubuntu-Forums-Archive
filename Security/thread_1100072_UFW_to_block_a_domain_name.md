---
title: "UFW to block a domain name?"
date: 2009-03-18
forum: Security
---

### Post by LepeKaname on 2009-03-18
Hello!

I have seen in my logs that "someone" is trying to access my server from several IP addresses like this:

220-139-127-188.dynamic.hinet.net[220.139.127.188]
220-136-24-124.dynamic.hinet.net[220.136.24.124]
118-167-134-115.dynamic.hinet.net[118.167.134.115]
118-169-205-95.dynamic.hinet.net[118.169.205.95]
and so on...

I could just block each IP, but as you can see, all have in common: "dynamic.hinet.net". 

So, is there any way I can block all the domain without having to take care of the IPs (or subdomains)?

Thank you!

---

### Post by HermanAB on 2009-03-18
Install BIND, make a zone for that domain and make a wildcard entry with IP address 127.0.0.1.

You can also try putting it in /etc/hosts.

Cheers,

Herman

---

### Post by ushills on 2009-03-19
Why not give denyhosts or fail2ban a go they will stop these intrusion attempts.

---

### Post by LepeKaname on 2009-03-20
HermanAB, thank you but I was looking for something simple... I mean, I already have a script to effectively block IPs with UFW so I can just add each IP and thats all... 

Thank you ushills, I will give a look to those scripts. 

If someone know how to do this using only UFW post it here please.

---

### Post by 1ll3xc on 2011-03-08
Hello LepeKaname,

You don't mention what services you are running on your server. The ones using tcp-wrapping (like SSH) can be domain-blocked.

Configure /etc/hosts.deny and /etc/hosts.allow accordingly.

Cheers!

---

