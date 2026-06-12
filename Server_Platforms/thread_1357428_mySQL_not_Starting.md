---
title: "mySQL not Starting"
date: 2009-12-17
forum: Server Platforms
---

### Post by itsonlybarney on 2009-12-17
I stopped my server for the first time in a few months today, was setup to have Apache2, PHP5 and mySQL5 as a webserver.

When I restarted the server, all services started except mySQL.  After trying a number of solutions, I tried changing the bind-address in /etc/mysql/my.cnf to the server IP address.  It had previously been set at 127.0.0.1.

The mySQL server would only start when set at the external IP address rather than the localhost address 127.0.0.1.

Any ideas how to use the localhost address in /etc/mysql/my.cnf rather than the external IP address?

---

### Post by cj13579 on 2009-12-17
have you tried changing the bind address to 127.0.1.1?

Also, if you are wanting to use this instance of MySQL from elsewhere you will need to comment this line out.

---

### Post by itsonlybarney on 2009-12-17
I couldn't imagine the my.cnf file changing after shutting the server down.  The bind-address that was in place was the 127.0.0.1 address, so I would have assumed it had previously worked that way.   I'll try changing it to 127.0.1.1.

---

### Post by oneloveamaru on 2009-12-17
What does the error log say? If a mysqld process is still running and listening on 127.0.0.1:3306 it won't allow you to start on that IP and port.

---

### Post by lykwydchykyn on 2009-12-17
Is the loopback device up?

---

### Post by oneloveamaru on 2009-12-17
Unless someone took out "auto lo" in /etc/network/interfaces, this shouldn't be a problem.


If some dumbass did take it out, put it back and do an "ifup lo"

---

### Post by itsonlybarney on 2009-12-17
Thanks guys, I checked the /etc/network/interfaces file, and found an incorrect iptables command.  It prevented the loopback device from starting.

Thanks oneloveamaru & lykwydchykyn

---

