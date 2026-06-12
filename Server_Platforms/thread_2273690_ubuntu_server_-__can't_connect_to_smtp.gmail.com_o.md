---
title: "ubuntu server -  can't connect to smtp.gmail.com or amazon SES"
date: 2015-04-14
forum: Server Platforms
---

### Post by netmastan2 on 2015-04-14
Hi, I've installed a ubuntu server.
Apache server is running fine.Some reason I can't send email from php script through smtp.gmail.com or Amazon SES server.
SMTP connection timed out. I tried to telnet ie smtp.gmail.com 587 it says connecting and timed out.
I can do telnet from other windows machine from the same network. I did not install anything but the apache web server.

Could anyone help me what could be the problem? I even turned off utfw and it's still the same.

I think ubuntu blocking port 465 and port 587

---

### Post by TheFu on 2015-04-16
Or the network gateway is blocking outbound SMTP from unapproved hosts?  That is a common config on business networks.

**telnet smtp.gmail.com 587 ** works from here.  Could the ISP/hosting provider be blocking?  Also, on Linux it is often required to run an MTA like postfix for programs to send email outbound. The programs just talk to the local MTA and expect it will forward email when/where needed.

---

