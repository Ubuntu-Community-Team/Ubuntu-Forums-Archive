---
title: "squid + dansguardian + multi connection"
date: 2007-11-27
forum: Server Platforms
---

### Post by myitanium on 2007-11-27
I have 3 internet connection and squid in same box.
at first, i did what LARTC method to create multiple connections and use squid to separate all connection through eth1, eth2, eth3 (localnetwork on eth0). And everything is fine. All of connection had been separated, depends on squid ACL.

then i installed dansguardian to create web content filter.
at first, dansguardian p**censored** all client IP to 127.0.0.1 which is dansguardian IP as it in same box with squid. All of my ACL wont work anymore. So after I googling several time, I put option Follow-X-Forwarded in squid and dansguardian. And voila.! my ACL get recognized again.

But then another problem show up. Squid was unable to separate each client (according to my ACL). So all connection only passed through eth1 because squid recognized it as 127.0.0.1.

Anyone know how to fix this problem?

---

