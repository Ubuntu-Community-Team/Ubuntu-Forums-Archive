---
title: "Ubuntu Server with Public IP"
date: 2017-01-29
forum: Server Platforms
---

### Post by josuelemus on 2017-01-29
I'll try to make it short.

I have a server that will be hosting a mobile app with backend admin portal. This server is behind a router, that hold a public IP if I connect my server into the router will use NAT and use the same IP to connect to Internet and so on. 
Here is the thing, I need the server to use a different public IP but still having it behind my firewall. 
Support team will connect via SSH to provide support to our server, what kind of service do I need to use to fix this issue ?

---

### Post by wildmanne39 on 2017-01-29
*Thread moved to **Server Platforms for better support**.*

---

### Post by SeijiSensei on 2017-01-30
You need to talk to your ISP about getting an IP subnet.  You'll be expected to buy a business-class Internet connection and probably pay a bit extra to get multiple IPs.  You might ask if they support [RFC 2317]("https://tools.ietf.org/html/rfc2317") "delegation" so you can manage the reverse DNS for those addresses yourself.  Even though you only want a second address, I'd find out how much more, if any, a six-host subnet costs to give yourself room to expand in the future.

---

### Post by raja.genupula on 2017-01-30
Let me share my view as well :). 

Assume you have a internal network inside your firewall,and your DNS mapped to one public IP Address. Received valid requests will pass through your firewall and will reach to your public IP and your public will forward these requests to your internal network where application hosted. And once request served it will be forwarded to client via this public IP address. 

So this public IP network will stand as forward network for client requests.

and your support team have to connect to this application machine to maintain it right , if you have another machine in the same network then assign that another public IP to that machine and arrange key based authentication( I heard this is more secure) between Application machine and this 2nd machine.  

That's my view.

---

