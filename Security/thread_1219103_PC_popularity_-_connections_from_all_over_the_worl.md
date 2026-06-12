---
title: "PC popularity - connections from all over the world .. why ?"
date: 2009-07-21
forum: Security
---

### Post by credobyte on 2009-07-21
```
121.23.44.54 server location: Langfang in China
122.161.244.160 server location: New Delhi in India                                    
86.108.109.180 server location: Amman in Jordan

```I'm not going to post ALL Ip's as the list is too long to fit into your monitor, but - why the ~censored~ I get these kind of connections ? I'm in EU/Latvia and connections from China/India/Jordan and almost all other countries are .. weird ? :-k
The best part is that .. almost every IP uses different port ( more over, I don't use torrent or directo-connection protocols like dc++, etc. ).

Can anybody explain, who am I and why I get these connections in such a short time ( ~ 30 new connections per minute ) ?

---

### Post by Rob_H on 2009-07-21
Is your machine protected by a firewall of any kind? If not, it should be. Are you sure these are actual connections and not just connection attempts? What tool did you use to produce this list?

Assuming they are real connections, the first thing to do is to try to figure out what program is responsible for them. This command will show you:

```
sudo netstat -taupn
``` 

Post the output and we may be able to help you more from there.

---

### Post by credobyte on 2009-07-21
More likely, connection attempts, not established connections. However, why would someone from Delhi want to connect to my PC ? :D About the list of IP's - Firestarter.

```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      2534/mysqld     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      3049/cupsd      
tcp    97235      0 94.30.182.129:43054     77.93.23.12:8000        ESTABLISHED 4082/audacious  
tcp        0      0 94.30.182.129:49456     74.125.43.138:80        ESTABLISHED 4088/firefox    
tcp6       0      0 :::80                   :::*                    LISTEN      3223/apache2    
tcp6       0      0 ::1:631                 :::*                    LISTEN      3049/cupsd      
udp        0      0 0.0.0.0:39995           0.0.0.0:*                           3025/avahi-daemon: 
udp        0      0 0.0.0.0:68              0.0.0.0:*                           3305/dhclient   
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           3025/avahi-daemon: 
```

---

### Post by jonathonward on 2009-07-21
Random stab in the dark, 
are you browsing the net when these attacks happen? it maybe web servers talking back if you are.

---

### Post by bodhi.zazen on 2009-07-21
There is nothing abnormal about what you are seeing at all.

Reading the logs is a fast route to paranoia. Crackers use all kinds of techniques to mask their IP and location and yes it is called 'www' because well it is world wide, lol.

If you run a server be sure to secure it, if these things bother you, use a firewall (ufw or gufw are default).

---

### Post by credobyte on 2009-07-21
> **jonathonward said:**
> Random stab in the dark, 
are you browsing the net when these attacks happen? it maybe web servers talking back if you are.

Yes, I do, tough, I haven't been anywhere else except this forum and localhost ( not in the past few hours ).

> **bodhi.zazen said:**
> There is nothing abnormal about what you are seeing at all.

Reading the logs is a fast route to paranoia. Crackers use all kinds of techniques to mask their IP and location and yes it is called 'www' because well it is world wide, lol.

If you run a server be sure to secure it, if these things bother you, use a firewall (ufw or gufw are default).

Ok, sounds enough good to not to worry about them, but - why do I get these connection attempts ? I'm not as much concerned about my PC's security as about the fact that I get something I haven't requested.

---

### Post by Rob_H on 2009-07-21
> **credobyte said:**
> Ok, sounds enough good to not to worry about them, but - why do I get these connection attempts ? I'm not as much concerned about my PC's security as about the fact that I get something I haven't requested.

Bodhi is right. Perfectly normal, unfortunately. These are just random probes from people or malware looking for machines to exploit on the Internet. Looks like Firestarter is doing its job.

---

