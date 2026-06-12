---
title: "Opening Port 8080"
date: 2009-01-22
forum: Security
---

### Post by lsToronto2008 on 2009-01-22
I have Jboss installed on my Ubuntu machine on my network. Works fine.

I would like to test an application I am working on from my windows machine (on the same network):

Window ---HTTP:8080---> Ubuntu

However I can't connect to port 8080 (on Ubuntu) from my windows machine via HTTP. I can ping the Ubuntu machine from windows, also Ubuntu is able to hit the Tomcat running on my windows machine on 8080, so I think my network is fine.

Ubuntu ----HTTP:8080---> Windows (works)

I decided to try working with a firewall on Ubuntu and did the following:

```

desktop:~$ sudo ufw enable
Firewall started and enabled on system startup
desktop:~$ sudo ufw allow 8080
Rules updated
desktop:~$ sudo ufw allow 8080/tcp
Rule added
desktop:~$ cat /etc/services | less
desktop:~$ sudo ufw allow webcache
Rules updated
desktop:~$ sudo ufw status
Firewall loaded

To                         Action  From
--                         ------  ----
8080:tcp                   ALLOW   Anywhere
8080:udp                   ALLOW   Anywhere
8080:tcp                   ALLOW   Anywhere

```

It looks to me like Ubuntu should be allowing traffic on 8080, but I am not able to telnet to 8080 on Ubuntu from windows.

Any idea what I could try next?

Thanks,

Luke

---

### Post by Titan8990 on 2009-01-22
> It looks to me like Ubuntu should be allowing traffic on 8080, but I am not able to telnet to 8080 on Ubuntu from windows.


This is most likely because the Ubuntu box does not have a telnet daemon listening on port 8080. You have to have a service to connect to....

---

### Post by lsToronto2008 on 2009-01-22
"You have to have a service to connect to.... "

Well telnet was just part of my testing to diagnose this. I see now why that didn't work, thank you. However my main issue is getting Jboss on port 8080 available to other machines on my network.

Do I need to set up a Jboss service then?

Thanks,

Luke

---

### Post by cdenley on 2009-01-22
Is there actually a program listening on port 8080? Post this output:
```

sudo netstat -tlnp

```
Do you have any iptables rules other than the ones create by UFW? Post this output:
```

sudo ufw disable
sudo iptables -L -n

```
If your firewall rules are all cleared, and there is a process listening on 0.0.0.0:8080 which can handle http connections, then try again.

---

### Post by lsToronto2008 on 2009-01-22
Output of netstat below
```

Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3873          0.0.0.0:*               LISTEN      7232/java       
tcp        0      0 127.0.0.1:1090          0.0.0.0:*               LISTEN      7232/java       
tcp        0      0 127.0.0.1:4712          0.0.0.0:*               LISTEN      7232/java       
tcp        0      0 127.0.0.1:8009          0.0.0.0:*               LISTEN      7232/java       
tcp        0      0 127.0.0.1:4713          0.0.0.0:*               LISTEN      7232/java       
tcp        0      0 127.0.0.1:54729         0.0.0.0:*               LISTEN      7232/java       
tcp        0      0 127.0.0.1:4457          0.0.0.0:*               LISTEN      7232/java       
tcp        0      0 127.0.0.1:1098          0.0.0.0:*               LISTEN      7232/java       
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      5865/mysqld     
tcp        0      0 0.0.0.0:57995           0.0.0.0:*               LISTEN      7232/java       
tcp        0      0 127.0.0.1:1099          0.0.0.0:*               LISTEN      7232/java       
tcp        0      0 127.0.0.1:8080          0.0.0.0:*               LISTEN      7232/java       
tcp        0      0 127.0.0.1:8083          0.0.0.0:*               LISTEN      7232/java       
tcp        0      0 127.0.1.1:51413         0.0.0.0:*               LISTEN      7232/java       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5787/cupsd      
tcp        0      0 127.0.0.1:4444          0.0.0.0:*               LISTEN      7232/java       
tcp        0      0 127.0.0.1:4445          0.0.0.0:*               LISTEN      7232/java       
tcp        0      0 127.0.0.1:4446          0.0.0.0:*               LISTEN      7232/java  

```
Looks like java is listening on 127.0.0.1:8080 not 0.0.0.0:8080. Does this explain why I can hit Jboss locally but not remotely? If so how can I fix this?

Here is the IpTables output:
```

desktop:~/Desktop$ sudo ufw disable
Firewall stopped and disabled on system startup
desktop:~/Desktop$ sudo iptables -L -n
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

Thanks,

Luke

---

### Post by cdenley on 2009-01-22
```
tcp        0      0 **127.0.0.1:8080**          0.0.0.0:*               LISTEN      7232/java
```
The process is listening on "127.0.0.1". Your Jboss server is apparently not configured to allow connections from other hosts.

---

### Post by Titan8990 on 2009-01-22
Since I do not know anything about jboss to assist you, I recommend looking at the jboss documentation.

---

### Post by lsToronto2008 on 2009-01-22
Thank you!

The pointed me in the right direction.

I found this in the Jboss docs:
> Remote connection to the JBoss AS server
JBoss AS now binds its services to localhost (127.0.0.1) by default, instead of
binding to all available interfaces (0.0.0.0). This was primarily done for security
reasons because of concerns of users going to production without having secured
their servers properly. To enable remote access by binding JBoss services to a
particular interface, simply run jboss with the -b option. To bind to all available
interfaces and re-enable the legacy behaviour use -b 0.0.0.0. In any case, be
aware you still need to secure your server properly.


I started the server with a run.sh -b 0.0.0.0 and all is well.

Thanks,

Luke

---

### Post by Titan8990 on 2009-01-22
Good to hear :)

---

