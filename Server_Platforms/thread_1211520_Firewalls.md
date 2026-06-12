---
title: "Firewalls"
date: 2009-07-12
forum: Server Platforms
---

### Post by MalcolmCowen on 2009-07-12
I've got a new Hasty installation for use on my local network only.
As far as I can see there is no firewall installed

I'm finding that my windows system can't 

1, write to Samba windows on Ubuntu (even though Samba is set to allow any access)

2, connect to MySql with MySqlAdministrator, although I've used the MySql manual to copy the GRANT command from.

This looks as if there is a firewall involved, but I can't see any installed.

Is there some default firewall action, and if so how can I get at it?

---

### Post by abaden on 2009-07-12
There shouldn't be any firewall turned on by default in ubuntu. You can try **/etc/init.d/ufw stop** to see if you did in fact turn on the "uncomplicated firewall". 

Try running the following from your windows command line (ctrl + r, cmd):
**telnet ip_of_server 3306**
**telnet ip_of_server 139**

The top is for MySQL, and the bottom is for Samba. If you get "connection closed", the remote server is blocking it, but if the telnet goes through, then your computers are talking to each other.

Furthermore, you might try checking to make sure Windows Firewall is off - that could be blocking things too.


Alex

---

### Post by MalcolmCowen on 2009-07-15
I ran the check with telnet.
Port 139 worked, and I found my Samba problems were doler permissions within Linux.
Port 3306 failed to connect, which seems to me to confirm that somewhere there is a firewall to be switched off somehow.

Question is where!
Malcolm

---

### Post by wojox on 2009-07-15
Did you open a terminal :

```
sudo /etc/init.d/ufw stop
```

What was the error message from mysql?

---

### Post by MalcolmCowen on 2009-07-16
The reply to sudo /etc/init.d/ufw stop
was 
Skipping firewall: ufw (not enabled)

The reply to Telnet was

C:\Documents and Settings\mc>telnet ip_of_server 3306
Connecting To ip_of_server...Could not open connection to the host, on port 3306
: Connect failed

---

### Post by MalcolmCowen on 2009-07-16
Fixed it!

The secret is that the GUI in the MySqlAdmin Startup Parameters only displays the TCP Port parameter as on or off.

There's another parameter in my.cnf 
bind-address = 127.0.0.1
This says only this IP Address may be used.  So comment this line out.

I'd also tried 
/sbin/iptables -A INPUT -i eth0 -s 10.5.1.3 -p tcp --destination-port 3306 -j ACCEPT
( as suggested in [http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html]("http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html")

I think this did not do anything, but it might have been relevant.

---

