---
title: "fail2ban"
date: 2009-02-24
forum: Server Platforms
---

### Post by mistypotato on 2009-02-24
Trying to get fail2ban to run...

I keep getting this....

ERROR  Could not start server. Maybe an old socket file is still present. Try to remove /var/run/fail2ban/fail2ban.sock. If you used fail2ban-client to start the server, adding the -x option will do it


Tried removing the file as suggested with no results but a return of the file and this message.

---

### Post by mansonthomas on 2009-02-25
sudo service fail2ban start

didn't work ?

---

### Post by mregister on 2009-02-25
Maybe your config is telling fail2ban to run in more than one instance? 

> fail2ban-server should not be used directly except in case of debugging. The option -s <FILE> is probably the most important one and is used to set the socket path. Thus, it is possible to run several instances of Fail2ban on different sockets. However, this should be not required because Fail2ban can run several jails concurrently. 

If fail2ban-server crashes (does it?), it is possible that the socket file has not been removed correctly. The -x option tells the server to delete the socket file before start-up. If the socket file of a running server is removed, it is not possible to communicate with this server anymore. 

The server handles the signals SIGTERM and SIGINT. When receiving one of these signals, fail2ban-server will quit nicely. 



Try: [http://www.fail2ban.org/wiki/index.php/MANUAL_0_8](http://www.fail2ban.org/wiki/index.php/MANUAL_0_8)

---

### Post by mistypotato on 2009-02-25
deleting the SOCK file seems to have helped


thx

---

