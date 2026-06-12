---
title: "Apache error message"
date: 2006-08-15
forum: Server Platforms
---

### Post by mibikerguy on 2006-08-15
I have had an operating Apache server, however, I am now receiving the following error message:

root@ts:~# sudo /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server... (98)Address already in use: make_sock: could not bind to address 192.168.1.69:8080
no listening sockets available, shutting down
Unable to open logs

I have installed and operationalized SSH, however this does not require port 80 or my redirected port 8080.....

Suggestions please ??

Tom Ski

---

### Post by mlind on 2006-08-15
Some application is already using port 8080. This is common port for servlet containers like Tomcat, are you running any?

See what application has already binded port 8080
```

sudo netstat -tupl

```

What do you mean about redirected port 8080? What ports are apache using?
(cat /etc/apache2/ports.conf)

---

### Post by mibikerguy on 2006-08-15
GREAT fast response!

Humm, running the above command, I produce the following.....

root@ts:~# sudo netstat -tupl
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:mysql                 *:*                     LISTEN     7267/mysqld
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     4749/smbd
tcp        0      0 *:5900                  *:*                     LISTEN     4570/vino-server
tcp        0      0 localhost.localdo:60620 *:*                     LISTEN     4213/python
tcp        0      0 *:10000                 *:*                     LISTEN     5003/perl
tcp        0      0 localhost.localdo:56946 *:*                     LISTEN     4189/hpiod
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN     4260/cupsd
tcp        0      0 *:8888                  *:*                     LISTEN     4439/perl
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     4749/smbd
tcp6       0      0 *:ssh                   *:*                     LISTEN     4774/sshd
udp        0      0 tshikoski.ho:netbios-ns *:*                                4747/nmbd
udp        0      0 *:netbios-ns            *:*                                4747/nmbd
udp        0      0 tshikoski.h:netbios-dgm *:*                                4747/nmbd
udp        0      0 *:netbios-dgm           *:*                                4747/nmbd
udp        0      0 *:10000                 *:*                                5003/perl

Dont see anything unusual here, does anyone?

Thanks 
Tom

---

### Post by armware on 2006-10-24
i had that error, too. check your apache config files for where the log folder(s) are. turns out i needed a folder called 'logs' in /var/www/ creating that folder and issuing the command sudo /etc/init.d/apache2 restart fixed it right up.

---

### Post by MJN on 2006-10-24
Armware, the reason you had to create /var/www/logs is likely because you changed your Apache config to find them there! It's been many a year since I saw the default Apache config but I'm pretty sure they normally reside somewhere in /var/log (/var/log/apache2 perhaps) which sounds sensible!

Mathew

---

