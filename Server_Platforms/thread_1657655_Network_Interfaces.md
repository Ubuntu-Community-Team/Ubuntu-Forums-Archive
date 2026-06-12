---
title: "Network Interfaces"
date: 2011-01-01
forum: Server Platforms
---

### Post by muut on 2011-01-01
I am setting up a test server using Ubuntu 6.10 Server (Edgy Eft).
Before everyone blasts me about why I using 6.10 I do have my reasons, so please...

I have been using the tutorial from HowtoForge, The Perfect Setup - Ubuntu 6.10, Linux Howtos and Tutorials.

I am now on Page 3.5, Configure The Network. The last line says: 'From now on you can use SSH client...'

I tried but cannot connect from my client workstation ( Ubuntu 10.4 LTS) and get a PuTTY fatal error, "No route to host". On the server, if I ping my client I get "Destination host unreachable". The server has Windows Server 2003 running off another disk and does connect to the network/Internet using the same Ethernet device. If I ping 127.0.0.1 or myself (server static IP  ) I get 0% packet loss. I tested SSH on the server with the command # ssh administrator@localhost and administrator@servername. That works and when connected evaluates servername to servername.domain.com - so now I'm stuck... seems like it should work! ](*,)

I would appreciate it if anyone out there could help... thanks in advance...

OK... got it figured out... my bad... there are two network adapters and I had to plug the cable into the right one! boy do I feel stupid!#-o

I was hoping to just delete this post but can't see a way to do that... maybe an admin will see this and do it for me?

---

