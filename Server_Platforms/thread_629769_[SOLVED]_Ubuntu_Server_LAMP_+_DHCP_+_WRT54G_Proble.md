---
title: "[SOLVED] Ubuntu Server LAMP + DHCP + WRT54G Problems?"
date: 2007-12-02
forum: Server Platforms
---

### Post by charper_99 on 2007-12-02
I have Ubuntu Server installed in a VM (with bridged ethernet).  Everything works great over the LAN in any and all configurations.   However, the whole idea is to get it up and running over the internet.  Straight out of the box, If I forward port 80 on my Linksys WRT54G router everything works great.  Unfortunately, when I assign a static IP to the system, I can't get port forwarding to work.

In short:
DHCP IP: 192.168.1.109 (for example)... forwarding on 80 All Good
Static IP: 192.168.1.5 ... forwarding on 80 FAILS

Other computers on the LAN can still access this computer by [http://192.168.1.5](http://192.168.1.5)

I've updated my router with the latest firmware.  So I assume I'm missing something when I assign a static IP.  Is there anything else I need to do?

Currently methods:
```
ifconfig eth0 192.168.1.5 netmask 255.255.255.0 up
```
or edit the /etc/network/interfaces file to reflect
```

auto eth0
iface eth0 inet static
     address 192.168.1.5
     netmask 255.255.255.0
     network 192.168.0.0
     broadcast 192.168.1.255
     gateway 192.168.1.1

```

Thanks in advance for any and all help!

---

### Post by Maxtorm on 2007-12-02
> **charper_99 said:**
> 
```

     network 192.168.0.0
     broadcast 192.168.1.255

```
Not 100% sure this would be your issue, but the network and mask don't mesh. Network should be 192.168.1.0. I believe you can leave "network" and "broadcast" out and they will be calculated automatically.

---

### Post by charper_99 on 2007-12-05
Didn't seem to fix it.  Those numbers were originally pulled from the autoconfig.  -but thanks anyway.

---

### Post by Maxtorm on 2007-12-05
If you're feeling adventurous, you could temporarily put the 192.168.1.5 box in the DMZ on the WRT54G. That would at least tell you whether the problem is the forwarding rule or the server itself (maybe something weird in the arp table?). If putting it into the DMZ works, then it would seem to indicate the problem is the forwarding rule.

---

### Post by charper_99 on 2007-12-07
Yeah, I tried the DMZ before with no success.

---

### Post by Maxtorm on 2007-12-07
What do the following commands return?  ```
netstat -nl
ifconfig eth0
```

---

### Post by charper_99 on 2007-12-08
Currently configured to listen on port 8081

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:121             0.0.0.0:*               LISTEN     
tcp6       0      0 :::8081                 :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ACC ]     STREAM     LISTENING     12844    /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     12999    /var/run/proftpd/proftpd.sock





eth0      Link encap:Ethernet  HWaddr 00:0C:29:8A:00:4A  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe8a:4a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60789 errors:0 dropped:0 overruns:0 frame:0
          TX packets:154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5866788 (5.5 MB)  TX bytes:28107 (27.4 KB)
          Base address:0x1070 Memory:e8820000-e8840000 
```

P.S. Thanks a bunch Maxtorm.  You're always very quick to reply; sorry it's taking me so long.

---

### Post by Maxtorm on 2007-12-09
> **charper_99 said:**
> Currently configured to listen on port 8081

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:121             0.0.0.0:*               LISTEN     
tcp6       0      0 :::8081                 :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     

```P.S. Thanks a bunch Maxtorm.  You're always very quick to reply; sorry it's taking me so long.

No prob. And I wouldn't thank me until the problem is fixed! :)  

I don't mean to ask a stupid question, but your original post indicated you were forwarding port 80 at the router. I'm assuming you're using the  Port Range Forward section under Applications & Gaming. If so, the forwarded traffic is going to be looking for a response on port 80 on the internal server, but the server is listening on 8081; hence, no connection. Or are you using a different technique so that incoming port 80 traffic ends up at the server on 8081?

What is bizarre is that your local connections can browse to the box. Are you just browsing directly to [http://192.168.1.5/](http://192.168.1.5/) or explicitly specifying the port as in [http://192.168.1.5:8081/]("http://192.168.1.5:8081/?")  ?

---

### Post by charper_99 on 2007-12-09
> **Maxtorm said:**
> 
What is bizarre is that your local connections can browse to the box. Are you just browsing directly to [http://192.168.1.5/](http://192.168.1.5/) or explicitly specifying the port as in [http://192.168.1.5:8081/]("http://192.168.1.5:8081/?")  ?

Yes... I'm using :8081.  As I said in my previous reply, I've just had it temporarily set to 8081.  When I can correctly forward to my box (DHCP-assigned IP address), the external link works as [http://(external-ip):8081](http://(external-ip):8081) .  

To avoid further confusion, I"ll set it back to port 80 now.

---

### Post by charper_99 on 2007-12-09
> **charper_99 said:**
> To avoid further confusion, I"ll set it back to port 80 now.


Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:35684           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:121             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:36349           0.0.0.0:*               LISTEN     
tcp6       0      0 :::80                   :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
udp        0      0 0.0.0.0:32769           0.0.0.0:*                          
udp        0      0 0.0.0.0:965             0.0.0.0:*                          
udp        0      0 0.0.0.0:111             0.0.0.0:*                          
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ACC ]     STREAM     LISTENING     12844    /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     12999    /var/run/proftpd/proftpd.sock

---

### Post by Maxtorm on 2007-12-09
I'm definitely out of my depth asking this question because I know very little about how the network stack works when switching back and forth between IPv4 and IPv6, but on my Ubuntu server box, the port listener shows up as tcp rather than tcp6. Is it possible this is the cause? It might explain the odd local/remote behaviour because the other hosts inside your LAN could be talking IPv6 while the router is not.

What does /etc/apache2/ports.conf look like on your server? I'm running 7.10 Server and it is handling port forwarding fine. First line of ports.conf is ```
Listen 80
```. I believe you can explicitly tell it to listen on the IPv4 address using ```
Listen 192.168.1.5:80
```

---

### Post by charper_99 on 2007-12-14
Sorry - I didn't realize this post went to 2 pages.  I feel like an idiot.

It was just listen 80, but I tried your suggestion to no avail.

---

### Post by Maxtorm on 2007-12-14
When you made the modification, did netstat then list the port as tcp or was it still showing as tcp6?

---

### Post by jamelb on 2007-12-14
in your router what do you have your dhcp port range to start at? by default it starts at 100 so 192.168.1.5 would not work but 192.168.1.105 would? hope that helps.

---

### Post by charper_99 on 2007-12-15
> **jamelb said:**
> in your router what do you have your dhcp port range to start at? by default it starts at 100 so 192.168.1.5 would not work but 192.168.1.105 would? hope that helps.

Yes, it's starting at 100.  The problem, however, with assigning a static IP to 105 is that it may cause a conflict.  I'm one of those very fortunate people that has to reboot my router every few days, so conflicts would become likely.

You do bring up a good point though.  I can't do it right now, but I'll try setting a static to 105 as a test.

---

### Post by charper_99 on 2007-12-15
> **Maxtorm said:**
> When you made the modification, did netstat then list the port as tcp or was it still showing as tcp6?

Yep - TCP

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:35684           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     
tcp        0      0 192.168.1.5:80          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:121             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:36349           0.0.0.0:*               LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
udp        0      0 0.0.0.0:32769           0.0.0.0:*                          
udp        0      0 0.0.0.0:965             0.0.0.0:*                          
udp        0      0 0.0.0.0:111             0.0.0.0:*                          
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ACC ]     STREAM     LISTENING     12844    /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     12999    /var/run/proftpd/proftpd.sock

```

---

### Post by Maxtorm on 2007-12-15
A few more thoughts:

Having a static address outside the range of assigned DHCP addresses should not affect the port forwarding; in fact, it is advisable. However, some routers will not allow you to access your public IP address from within the router's LAN (I think this has something to do with the NAT implementation on the router) -- I think Linksys falls into this category. I know you have been able to access the server on the public IP when you're using DHCP, but if the NAT/public IP issue only affects static IP nodes, this could explain the problem. Have you ever tested the statically assigned IP implementation from a remote public IP address? An easy way to do this without having to rely on someone at a remote site is to use [CentralOps]("http://centralops.net/co/")'s Domain Dossier and select Service Scan -- though this will only work if you have your web server running on Port 80.

Is it possible that your ISP is blocking web servers? Again, it would not explain how you have been able to access the server under DHCP and not static IP, though some ISPs actively watch for traffic on common non-standard ports like 8080 and 8081 -- so who knows -- perhaps coincidence that your port forwad under DHCP snuck under the ISP's radar and the static mapping didn't? Maybe try a port up above 40000 and see if the behaviour is the same? I know ... it's a long shot.

---

### Post by WIGGMPk on 2007-12-16
EDIT:  Wrong Thread

---

### Post by WIGGMPk on 2007-12-16
> **Maxtorm said:**
> A few more thoughts:
However, some routers will not allow you to access your public IP address from withing the router's LAN (I think this has something to do with the NAT implementation on the router) -- I think Linksys falls into this category.

I would have to argue that point. Long time ago (when I still used Linksys's firmware) I have hosted several services behind a WRT54G router. The only issues I ever encountered was ports being blocked by ISP's (ie: 80 & 8080)

I would definatly try to keep the static IP within the range of the DHCP tables. Reasons why? Because its Linksys! Not a big fan  here. Anyway, there should be a section in the router to declare static IP's by MAC address. Which could eliviate your concern on an IP conflict.

Another solution. Not the best.. Flash your router with OpenSource firmware. You'll get ton's more control out of it. Or you can make your server do DHCP using ipTables you can redirect anything you want wherever you want. Add webmin into the mix and everything just gets easier.

My 2 Cents

---

### Post by charper_99 on 2007-12-17
> **WGGMk said:**
> I would definatly try to keep the static IP within the range of the DHCP tables.

That worked.  As jamelb and wggmk said, it appears the problem was with my router the whole time.  It worked when I set the static to 105.  Just to keep it reasonably out of the range of DHCP, I assigned it an IP of 192.168.1.199.

Thank you everybody for your help!

---

### Post by charper_99 on 2007-12-17
P.S.

> Anyway, there should be a section in the router to declare static IP's by MAC address. Which could eliviate your concern on an IP conflict.
Nope... that would be nice though.

> Another solution. Not the best.. Flash your router with OpenSource firmware.
I agree 100% if that's an option.  I ran openwrt on my older WRT54G.  This one, however, is a newer model and does not have enough storage capacity.

---

### Post by Banthaman on 2007-12-24
I know this is solved already but I believe on the wrt54g you do have the option to reserve an IP address even inside the dhcp range.

---

