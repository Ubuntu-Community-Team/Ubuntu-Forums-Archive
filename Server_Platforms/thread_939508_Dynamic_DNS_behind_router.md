---
title: "Dynamic DNS behind router"
date: 2008-10-06
forum: Server Platforms
---

### Post by link2008 on 2008-10-06
How do I use dynamic DNS behind a router? I am trying to use dyndns.org. with my domainmonger.com domain. I have a dynamic IP address behind a router. Currently, my public IP address is  67.160.192.174, and my ip address behind the router is 192.168.0.4. I am using Ubuntu 8.04.

---

### Post by oavicena on 2008-10-06
Hi there, you must point to your router public IP from dyndns and then you must tell your router to point whatever port (80 for web, 21 for ftp, etc) you wish to your computer.
In your dyndns control panel there is an option to get your router public IP and assign it to the domain you have chosen, it does automagically if you get into your account from your computer.
Then you must tell your router to pass the requests to the computer you want to, that is, if your public IP is 67.160.192.174 and your private IP is 192.168.0.4, you must tell the router to pass any request (i.e. to the port 80 for a web server) to the computer 192.168.0.4. This set up depends on the each router. Common ports I use: 80 web, 21 ftp, 22 ssh.

Good luck, 
Borja

---

### Post by link2008 on 2008-10-07
Thank you!

---

