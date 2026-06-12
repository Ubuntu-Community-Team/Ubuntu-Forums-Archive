---
title: "Espresso bar."
date: 2011-07-22
forum: Server Platforms
---

### Post by dichtbijzee on 2011-07-22
We are starting an Espresso bar here in Denmark, we are thinking about giving free wifi. But there is a law here in denmark that all internet usage in companies should be logged. logging the mac and witch ip's that pc has gone to. and time and date as well.
On top of this we would like to give an hour free wifi with every purchase and additional time with a code on their receipt. and customers should login on our local site with that code and then they would get that hour. 
We were thinking about using an ubuntu proxy server for this wich would also help us a bit with possible bandwidth issues.
What's the best course of action?

---

### Post by samosamo on 2011-07-22
[http://www.wanderingwifi.com/cafes.html](http://www.wanderingwifi.com/cafes.html)

---

### Post by cariboo on 2011-07-22
Have a look here:

[http://www.howtoforge.com/wifi_hotspot_setup](http://www.howtoforge.com/wifi_hotspot_setup)

and

[http://www.howtoforge.com/wireless_hotspot_howto](http://www.howtoforge.com/wireless_hotspot_howto)

---

### Post by dichtbijzee on 2011-07-23
thank you, I am looking into it now!

---

### Post by Brad55 on 2011-07-23
I'll just sit there and drink all you Espresso. :)

---

### Post by dichtbijzee on 2011-09-26
I do now have the wifi hotspot working through [easyhotspot]("http://easyhotspot.inov.asia/") but no logging :(
I have googled for logging but I can only find stats and some monitoring, but no logging. Anyone any idea?

---

### Post by SeijiSensei on 2011-09-26
You can track all web requests with Squid and an iptables rule. Configure squid for [transparent proxying]("http://www.deckle.co.za/squid-users-guide/Transparent_Caching/Proxy"), and add these rules to the firewall:

```
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 3128
```

(Assumes you've set up squid to listen on its default port of 3128.)

This will redirect all web requests through the proxy and log them.  You might find the ability to filter requests using "ACLs" a valuable tool as well.  I'd suggest adding rules to squid.conf that block requests for .exe, .com, and .bat objects to protect your users from downloading Windows malware.  

```

# block requests for .exe files
acl noexe url_regex -i \.exe$
http_access noexe deny

```

The ACL identifies requests for files that end in .exe (using regular expressions).  The access rule blocks those files.

Note that this doesn't help with https requests.  Using a proxy for https is much more complex, since the proxy will appear to the SSL connection as a "man-in-the-middle" attack. Read [this](http://www.squid-cache.org/Doc/config/https_port/) for starters.

---

