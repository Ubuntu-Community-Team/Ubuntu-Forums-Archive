---
title: "&quot;service mysql status&quot; doesn't work in Ubuntu Server 10.04.1"
date: 2010-09-30
forum: Server Platforms
---

### Post by tranduyhung on 2010-09-30
Hi!

I'm running Ubuntu Server 10.04.1 in Virtualbox environment with the host is Ubuntu Desktop 10.04.1.

I have built a LAMP server after a fresh installation of Ubuntu server (I didn't choose LAMP to install when I installed this server) , everything works fine, but when I run "service mysql status" command I get this error: 

*"status: Unable to connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory"*

I try in my desktop (also with LAMP installed) and I get the result like:

*"mysql start/running, process 1218"*

So I think there is something wrong with the server.

Can you help me figure out what's wrong and how could I fix this please?

Thank you so much!

---

### Post by loopodoopo on 2010-09-30
Hi, 

You will need root rights. 

Try: "sudo service mysql status" 

Hope that helps.

---

### Post by tranduyhung on 2010-10-01
Oh it works. I guess that's a small difference between Desktop and Server :D.
Thank you loopodoopo!

---

### Post by loopodoopo on 2010-10-01
Anytime :)

---

