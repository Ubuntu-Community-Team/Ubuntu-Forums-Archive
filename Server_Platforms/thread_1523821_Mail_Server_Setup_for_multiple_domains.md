---
title: "Mail Server Setup for multiple domains"
date: 2010-07-04
forum: Server Platforms
---

### Post by Nixforce on 2010-07-04
Im moving all my websites on a dedicated box. I had a cpanel hosting account, and now moving to a terminal and ssh system.

I need some advice on choosing my mail setup. I need POP, SMTP, with multiple domains, as host for a few clients.

I would like the most simple version.

The server will only send +- 100 mails / day.

I currently running Ubuntu Linux 10.04.

Any advice would be greatly appreciated.

---

### Post by DJYoshaBYD on 2010-07-04
Install and WebMin..

for multiple domains, there is file (i cannot remember where it is or what its called), that will redirect those requests to their respective folder..

usually a domain point to a single IP, but when 1 IP hosts multiple domains, the server has to read the header of the packets (which will have the domain listed somewhere), then it send it to that folder for that site or whatever..

i have only set that up once...

google multiple domains 1 IP ubuntu

---

