---
title: "BIND9 DNS Server"
date: 2009-06-02
forum: Server Platforms
---

### Post by Pakia on 2009-06-02
A quick question, can you run a bind9 DNS server and an Apache server on the same machine? Some posts say you can some say you cannot. One post said all you have to do is forward DNS querries to your internal IP address, or can you use a virtual IP (available in webmin networking) specifically for the DNS server but under the IP where the Apache server is running. I am using ddclient as I do not have a static IP. Any comments appreciated

---

### Post by LepeKaname on 2009-06-02
Yes, I think is possible. I personally don't use BIND9 but I use other DNS server and happens the same. The reason is that if you forward for example, web.localserver to localhost (which may bind to 127.0.0.1) then when a client try to access web.localserver will forward to their own 127.0.0.1 and thus never will display the website. So, what you need to do is to use for example web.localserver to 192.168.0.X (or whatever your LAN IP is).

---

