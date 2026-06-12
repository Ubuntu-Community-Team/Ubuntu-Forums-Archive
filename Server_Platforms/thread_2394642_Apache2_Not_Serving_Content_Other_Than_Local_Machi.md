---
title: "Apache2 Not Serving Content Other Than Local Machine"
date: 2018-06-19
forum: Server Platforms
---

### Post by geoffrey-p on 2018-06-19
Until sometime last night, the Apache2 server was reliably serving pages to the LAN including RStudio, Adminer, PHP and standard web content. I did run a system update from the official servers but somehow nothing is working other than if I'm directly on the server machine (still serves locally).

Ubuntu 18.04, Apache 2.4.29

```
sudo netstat -lntpActive Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1077/mysqld         
tcp        0      0 127.0.0.1:5038          0.0.0.0:*               LISTEN      1261/asterisk       
tcp        0      0 0.0.0.0:2000            0.0.0.0:*               LISTEN      1261/asterisk       
tcp        0      0 0.0.0.0:8787            0.0.0.0:*               LISTEN      972/rserver         
tcp        0      0 127.0.0.53:53           0.0.0.0:*               LISTEN      849/systemd-resolve 
tcp        0      0 127.0.0.1:8118          0.0.0.0:*               LISTEN      1055/privoxy        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      877/cupsd           
tcp6       0      0 :::80                   :::*                    LISTEN      1118/apache2        
tcp6       0      0 ::1:631                 :::*                    LISTEN      877/cupsd  
```

```
geoffrey@geoffrey-Satellite-L745:~$ cat /etc/hostnamegeoffrey-Satellite-L745
geoffrey@geoffrey-Satellite-L745:~$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    geoffrey-Satellite-L745


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

```
geoffrey@geoffrey-Satellite-L745:/etc/apache2$ cat ports.conf
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default.conf


Listen 80


<IfModule ssl_module>
    Listen 443
</IfModule>


<IfModule mod_gnutls.c>
    Listen 443
</IfModule>


# vim: syntax=apache ts=4 sw=4 sts=4 sr noet

```
I disabled the firewall and this did not fix the problem. I have reenabled it as I have ruled that out as a cause. (I also made no changes to the UFW or IPTables rules).

Any help is greatly appreciated!!!

---

### Post by geoffrey-p on 2018-06-24
Nevermind, it magically began working again. I assume some kind of bug was introduced between a couple of daily updates.

---

