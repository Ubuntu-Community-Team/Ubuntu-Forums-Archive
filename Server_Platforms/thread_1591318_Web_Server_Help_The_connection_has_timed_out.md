---
title: "Web Server Help The connection has timed out"
date: 2010-10-09
forum: Server Platforms
---

### Post by Zero++ on 2010-10-09
I'm trying to set up a personal web server just for fun an practice. I am having issues accessing my server from the Internet. 

I have working apache2 server I can access it from local host / 127.0.0.1
I am using dyndns.com and my IP and port test fine according to their port tester. 
I use DDclient to update DynDns and it updates without errors. 
My firewall is off (for testing purposes)

If I try to access my IP or address I receive a time out error.

Any help is greatly appreciated. 

I'm using the newest apache 2 (from LAMP).
I'm using Ubuntu 10.4
I have a Dlink router with the port forwarded and my ISP is not blocking the port. The same problem occurs when I plug directly into my modem.

"The connection has timed out"

---

### Post by mvklingeren on 2010-10-09
Weird question maybe but, can you try to access it by ip/or dns name from the same subnet as in 

from another computer in the network, or maybe by cell-smartphone on wifi?

---

### Post by Zero++ on 2010-10-09
Good call. I can access the server from other computers within my local area network. This is very perplexing. I can access the server from my LAN. DynDns tells me my ip and port are available yet no wan access. Any help is appreciated.

---

### Post by lisati on 2010-10-09
Is your ISP blocking port 80 by any chance?

---

### Post by Zero++ on 2010-10-11
Good call they are blocking port 80 but Apache is listening at port 8080 and the tests i get back from dyndns.com are telling me that port 8080 on my ip address is open. So are all of the networking tests from my server. I have my router firewall forwarding port 8080 too.

---

### Post by arrrghhh on 2010-10-11
If they're blocking 80, they're probably blocking 8080... but you said dyndns.com tells you that it is open?  Have you tried hitting it from mutliple WAN connections, they all fail?

UFW?  You said it's off, just want to ensure.  Also, do you use iptables at all?

---

### Post by Zero++ on 2010-10-11
**DynDns report 8080** is **open** and accepting connections. This indicates the port is not being blocked by either a firewall or your ISP and is currently operational.

I've attempted to access the computer from 2 outside networks with no luck. 
No firewall
No IP tables

---

