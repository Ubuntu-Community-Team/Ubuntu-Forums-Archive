---
title: "can I connect to a local webpage by use of the server's hostname?"
date: 2007-11-05
forum: Server Platforms
---

### Post by Sammi on 2007-11-05
I am aiming to make it possible to connect to a local intranet webpage by use of only the servers hostname, but haven't been able to make this work.

The webserver is one I set up on my workplaces. It's basically Gutsy Gibbon + AMP running a mediawiki webpage. At the moment employees are able to connect to the webpage by use of the static LAN IP address and a domain name that is configured on the DHCP server to point to this IP address. 

I haven't been able to make it possible to connect to the webpage, by use of only the server's hostname, which I think would be the most convenient way to do it. That way no one need to remember a full domain name (example.domail.com) or IP address, but only a short and simple hostname.

If anyone has got any ideas or pointers for me, then I would be very grateful.

---

### Post by primski on 2007-11-05
hm, if you enter target's hostname into clients hosts file... i can connect just fine using only that... but how could you do that dynamically, with dhcp, or dns? i have no idea :p doing it manually for each client would not be very practical.

---

### Post by HermanAB on 2007-11-05
If you have 5 or so clients, then put the IPaddress/hostname pair in the /etc/hosts file (Windows c:\windows\system32\devices\etc\hosts).

If you have more clients, install BIND.

Cheers,

H.

---

### Post by md5hash on 2007-11-05
i had this problem before.. i installed samba then it works..

---

