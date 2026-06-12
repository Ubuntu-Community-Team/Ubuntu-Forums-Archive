---
title: "proftpd can only access as 127.0.0.1"
date: 2006-03-25
forum: Server Platforms
---

### Post by webfoot0 on 2006-03-25
Hi
I have sucessfully installed ProFTP on a small machine - server only, no GUI, character display only.

The problem is that while the ftp server is running and can be connected to from the terminal window ie:
ftp 127.0.0.1 
works and I can login with my usernme and password.

however:
ftp 192.168.5.206 (the IP of machine on my local network)
The reply is:
"Sorry, no server available to handle requests on 192.168.5.206"

There is the same reply attempting to connect from another machine on the network. Ping 192.168.5.206 works.

Why is this and what needs changing/fixing.

Keith

---

### Post by webfoot0 on 2006-03-26
Fixed
Needed following in /etc/proftpd.conf
ServerName     ubuntu
ServerType      standalone
DefaultServer   on

Added these and now can login across the network

Keith

---

