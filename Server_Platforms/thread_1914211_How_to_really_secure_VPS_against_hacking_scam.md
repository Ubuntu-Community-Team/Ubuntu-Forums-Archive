---
title: "How to really secure VPS against hacking scam?"
date: 2012-01-23
forum: Server Platforms
---

### Post by w7u64xi7 on 2012-01-23
I am new to linux and using un managed VPS and wondering if it possible to really make it secure as possible against all attacking scam.

---

### Post by rubylaser on 2012-01-24
> **w7u64xi7 said:**
> I am new to linux and using un managed VPS and wondering if it possible to really make it secure as possible against all attacking scam.

"Secure as possible" is pretty vague.  Disconnecting the ethernet cable is the safest way to secure it :)  Seriously though, there are a number of great guides in the Security forum to get you started.  Things like using keys instead of passwords for SSH, using mod_security and mod_evasive with Apache2, iptables, and Snort.

Dangertux from the Ubuntu forums had a good guide up on his site, but it's not available for some reason.  Here's a [link]("http://webcache.googleusercontent.com/search?q=cache:0t4ZCsRvqZ4J:dangertux.wordpress.com/tutorials/reasonably-secure-ubuntu-homesmall-business-server-tutorial/+&cd=1&hl=en&ct=clnk&gl=us") to the web cache of it.

---

### Post by Habitual on 2012-01-24
suhosin

---

### Post by w7u64xi7 on 2012-01-24
> **rubylaser said:**
> Dangertux from the Ubuntu forums had a good guide up on his site, but it's not available for some reason.  Here's a [link]("http://webcache.googleusercontent.com/search?q=cache:0t4ZCsRvqZ4J:dangertux.wordpress.com/tutorials/reasonably-secure-ubuntu-homesmall-business-server-tutorial/+&cd=1&hl=en&ct=clnk&gl=us") to the web cache of it.You mean it is for set up a clean vps from scratch?

---

### Post by sandyd on 2012-01-25
> **w7u64xi7 said:**
> You mean it is for set up a clean vps from scratch?
All security things are starting from scratch.

I use SELinux + Intrution/DDOS Barracuda WAF +  OSSEC, but thats probably too much.

---

### Post by w7u64xi7 on 2012-01-25
> **sandyd said:**
> Barracuda
[http://drupal.org/project/barracuda](http://drupal.org/project/barracuda)

---

### Post by sandyd on 2012-01-26
> **w7u64xi7 said:**
> [http://drupal.org/project/barracuda](http://drupal.org/project/barracuda)
[http://www.barracudanetworks.com/ns/products/web-site-firewall-overview.php](http://www.barracudanetworks.com/ns/products/web-site-firewall-overview.php)

---

### Post by w7u64xi7 on 2012-01-27
> **sandyd said:**
> [http://www.barracudanetworks.com/ns/products/web-site-firewall-overview.php](http://www.barracudanetworks.com/ns/products/web-site-firewall-overview.php)
Thanks for correcting the info.
But this one is not free I am afraid.
Please advise for which one to be used in a VPS under Ubuntu 10.4 LTS

---

### Post by sandyd on 2012-01-28
> **w7u64xi7 said:**
> Thanks for correcting the info.
But this one is not free I am afraid.
Please advise for which one to be used in a VPS under Ubuntu 10.4 LTS
Snort.
If your using apache2, add mod_security.

---

### Post by Dangertux on 2012-01-28
Keep in mind with mod_security or any WAF (even expensive ones) it is only as good as signatures that it has. For instance the barracuda device linked above is a little funny in that it will block

```

1=1

```

All day long but it will not trigger on

```

0x70=0x70

```

Go figure? Needless to say I'm a big fan of mod-security with OWASPS core rule set. 

As always it's much better to have securely written code bit if you know it is weak intelligently monitoring logs and updating IDS/WAF rules will go a long way to help you get the most out of your software or hardware appliance. 

Hope this helps.

---

### Post by sandyd on 2012-01-29
> **Dangertux said:**
> Keep in mind with mod_security or any WAF (even expensive ones) it is only as good as signatures that it has. For instance the barracuda device linked above is a little funny in that it will block

```

1=1

```All day long but it will not trigger on

```

0x70=0x70

```Go figure? Needless to say I'm a big fan of mod-security with OWASPS core rule set. 

As always it's much better to have securely written code bit if you know it is weak intelligently monitoring logs and updating IDS/WAF rules will go a long way to help you get the most out of your software or hardware appliance. 

Hope this helps.
Thats why I run selinux :), OSSEC, and Snort.
Once the snort/ossec warning levels for an IP reach a certain level, the Barracuda will automatically block the IP. (I know its not good, but I don't spend my entire life staring at the logs...)

The rest of the logs, I go through regularly.

---

