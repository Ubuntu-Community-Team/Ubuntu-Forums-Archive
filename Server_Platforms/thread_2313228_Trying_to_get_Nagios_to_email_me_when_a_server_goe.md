---
title: "Trying to get Nagios to email me when a server goes down"
date: 2016-02-10
forum: Server Platforms
---

### Post by crizpiz on 2016-02-10
Hello I am trying to get postfix set up and working so I can get Nagios to email me whenever a server goes down, raid fails, etc. 
The machine I have up is an Ubuntu server running in a virtual machine in hyper V. 
The machine is on the network and can ping the servers I want monitored, they are already configured to monitor, just not email me. I already have an exchange server running on actual hardware, as opposed to a VM, however it is my understanding that I still need postfix for Nagios to email me. I have Nagios running Apache2 and Postfix running. Their service status shows active (running). I get no errors when I restart their respective services. However whenever I telnet into postfix to send an example email to me. [email]name@address.com[/email] for example it gives me the error: 451 4.3.0 [email]name@address.com[/email]: temporary lookup failure. I am rather new to postfix and Nagios, so please forgive any new mistakes.

I can post the contents of any logs or config files necessary, however I do not know in advance what you need to see. Thanks for your time!

---

### Post by sandyd on 2016-02-11
Moved to *Server Platforms*

---

