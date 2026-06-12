---
title: "Will Bind reverse resolution ever work in this situation?"
date: 2012-12-21
forum: Server Platforms
---

### Post by geosword on 2012-12-21
Hi Everyone,
Im trying to figure out whether or not reverse resolution will ever work in my particular situation. I've changed the domain names and IPs to protect the innocent.

Im using an old(er) pc as a dns server(running bind 9.8 on ubuntu 12.4) at my house, which is obviously running over my home broadband connection (don't worry its just a test set up, nothing mission critical!)
So my home public ip address is 1.2.3.4 and it resolves to customer1.isp.com
My DNS server is setup as the master of example.com.
The MX record is also pointing at 1.2.3.4 (the mail server is also at my home) 
So asking the dns server to resolve mail.example.com predictably resolves to 1.2.3.4

However, when I do a reverse resolution on 1.2.3.4 it doesnt resolve to mail.example.com, but to customer1.isp.com

My question is: Is it actually possible to get it to resolve (from anywhere on the internet) to mail.example.com?

From the the information Ive seen, I dont think it is, but just wanted to check my thinking was correct?

Thanks in advance, and merry christmas to one and all!
Geo

---

### Post by Cheesemill on 2012-12-21
The reverse DNS settings can only be changed by your ISP (as they are the ones that own the IP addresses).

Some ISP's will let you change the settings (sometimes for a fee), and some ISP's won't. You'll have to contact them to find out.

---

### Post by geosword on 2012-12-21
Hi Cheesemill, Thats pretty much what I thought. Thanks very much
Geo

---

