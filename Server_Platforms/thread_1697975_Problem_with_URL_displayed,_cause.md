---
title: "Problem with URL displayed, cause?"
date: 2011-03-01
forum: Server Platforms
---

### Post by ChetsPlace on 2011-03-01
I have domain purchased through GoDaddy, forwarded to my VPS IP.

Everything works however after it is forwarded instead of displaying [http://mywebsite.com](http://mywebsite.com) it displays [http://11.11.11.11](http://11.11.11.11)

I have been trying to fix this for hours and am not sure if its an apache error, DNS, godaddy, VPS or other issue.

Any insight would be very appreciated.

Chet

---

### Post by wongo888 on 2011-03-03
Assuming that you have your name servers set up properly with your registrar. You need to set your DNS A record to point to your VPS machine's IP address. This is done on the name server by editing zone files.

If GoDaddy is hosting your DNS for you then you should contact GoDaddy support. If your VPS host is providing your DNS for you (which is probably the case) then you should contact their support.

---

### Post by James78 on 2011-03-03
I use GoDaddy, and they have an advanced control panel to that sorts of things. He can just use the control panel to add a DNS A record pointing to his IP.

Although, I have GoDaddy forward to my own domains nameservers, and it gives me complete control over DNS. GoDaddy has limits on things like subdomains. Pointing it to your own DNS server, then doing it yourself, you have no limits on anything.

---

