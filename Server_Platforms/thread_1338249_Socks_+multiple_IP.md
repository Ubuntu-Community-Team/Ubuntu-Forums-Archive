---
title: "Socks +multiple IP"
date: 2009-11-26
forum: Server Platforms
---

### Post by alephiej on 2009-11-26
Hi guys. I run a hosting server on ubuntu, that has 10 virtual interfaces, with their own IP's. 
Now, I need to run socks proxy on that, and while I had no problems with configuring and running ss5, I still have an issue that I can't overcome. I've spent a week so far, and google didn't bring me any valuable results.
The problem is, when I connect to the server, using one of virtual IP's, the connections are being sent via main IP, and I'd like the situation, when I connect to virtual IP, that IP is used for outgoing connections. 
Can you please help me with that?

Here's how it is now:

Connecting to 192.168.1.10
whatismyip.com shows my ip as 192.168.1.1

And I'd like:

Connecting to 192.168.1.10
whatismyip.com shows my ip as 192.168.1.10

(The ip's are for reference only. I'm using valid public adresses).

---

### Post by alephiej on 2009-11-28
shameless bump ;)

---

