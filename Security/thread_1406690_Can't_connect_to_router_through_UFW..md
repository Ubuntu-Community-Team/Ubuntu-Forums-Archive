---
title: "Can't connect to router through UFW."
date: 2010-02-14
forum: Security
---

### Post by random.manifestation on 2010-02-14
Hi all, 
I have problems connecting to several things while ufw is enabled, with the most important beeing my router(10.0.0.1) and KGpg key upload. I tried to allow all incoming traffic from 10.0.0.1 but it didn't help. With ufw disabled i can connect to the router

I use wicd and wicd-client for connection and the "cant connect to access point" error
Below are the output of ufw status numbered and portsentry(dunno if its needed)
```
   To                         Action      From
     --                         ------      ----
[ 1] 53,137,138/udp             ALLOW OUT   Anywhere (out)
[ 2] 20,21,22,25,80,139,443/tcp ALLOW OUT   Anywhere (out)
[ 3] Anywhere                   ALLOW IN    10.0.0.2 3389
[ 4] Anywhere                   ALLOW IN    10.0.0.1
[ 5] 3389                       ALLOW OUT   Anywhere (out)
[ 6] 8118                       ALLOW OUT   Anywhere (out)
[ 7] 9050                       ALLOW OUT   Anywhere (out)
[ 8] 993                        ALLOW OUT   Anywhere (out)
[ 9] 23                         ALLOW OUT   Anywhere (out)
[10] Anywhere                   DENY OUT    Anywhere (out)
``````
TCP_PORTS="1,7,9,11,15,70,79,109,110,111,119,139,143,512,513,514,515,540,635,1080,1524,2000,2001,4000,4001,5742,6000,6001,6667,12345,12346,20034,27665,3$
UDP_PORTS="1,7,9,66,67,68,69,111,161,162,474,513,517,518,635,640,641,666,700,2049,31335,27444,34555,32770,32771,32772,32773,32774,31337,54321"

```thanks in advance for any advice,

RM

---

### Post by bodhi.zazen on 2010-02-14
> **random.manifestation said:**
> Hi all, 
I have problems connecting to several things while ufw is enabled, with the most important beeing my router(10.0.0.1) and KGpg key upload. I tried to allow all incoming traffic from 10.0.0.1 but it didn't help. With ufw disabled i can connect to the router

I use wicd and wicd-client for connection and the "cant connect to access point" error
Below are the output of ufw status numbered and portsentry(dunno if its needed)
```
   To                         Action      From
     --                         ------      ----
[ 1] 53,137,138/udp             ALLOW OUT   Anywhere (out)
[ 2] 20,21,22,25,80,139,443/tcp ALLOW OUT   Anywhere (out)
[ 3] Anywhere                   ALLOW IN    10.0.0.2 3389
[ 4] Anywhere                   ALLOW IN    10.0.0.1
[ 5] 3389                       ALLOW OUT   Anywhere (out)
[ 6] 8118                       ALLOW OUT   Anywhere (out)
[ 7] 9050                       ALLOW OUT   Anywhere (out)
[ 8] 993                        ALLOW OUT   Anywhere (out)
[ 9] 23                         ALLOW OUT   Anywhere (out)
[10] Anywhere                   DENY OUT    Anywhere (out)
``````
TCP_PORTS="1,7,9,11,15,70,79,109,110,111,119,139,143,512,513,514,515,540,635,1080,1524,2000,2001,4000,4001,5742,6000,6001,6667,12345,12346,20034,27665,3$
UDP_PORTS="1,7,9,66,67,68,69,111,161,162,474,513,517,518,635,640,641,666,700,2049,31335,27444,34555,32770,32771,32772,32773,32774,31337,54321"

```thanks in advance for any advice,

RM

You are trying to configure your firewall by shaping outbound connections. This is difficult, you will need to know what port you are trying to connect to, are you using dhcp ? 

If you do not know the port(s) to allow, enable logging and look to see what traffic is blocked.

---

### Post by random.manifestation on 2010-02-14
Yep, i'm using dhcp - forgot about that =) Added ports 67,68/udp to ufw and erased them from portsentry, but it still doesn't work. How do i allow logging? i activated a debug option in wicd but it's only showing an error.  I start to miss the system-config-firewall from redhat :D

```
 To                         Action      From
     --                         ------      ----
[ 1] 53,137,138/udp             ALLOW OUT   Anywhere (out)
[ 2] 20,21,22,25,80,139,443/tcp ALLOW OUT   Anywhere (out)
[ 3] 67,68/udp                  ALLOW IN    10.0.0.1
[ 4] Anywhere                   ALLOW IN    10.0.0.2 3389
[ 5] Anywhere                   ALLOW IN    10.0.0.1
[ 6] 3389                       ALLOW OUT   Anywhere (out)
[ 7] 8118                       ALLOW OUT   Anywhere (out)
[ 8] 9050                       ALLOW OUT   Anywhere (out)
[ 9] 993                        ALLOW OUT   Anywhere (out)
[10] 23                         ALLOW OUT   Anywhere (out)
[11] Anywhere                   DENY OUT    Anywhere (out)
```

---

### Post by bodhi.zazen on 2010-02-14
You are allowing the dhcp connections in , but not out.

---

