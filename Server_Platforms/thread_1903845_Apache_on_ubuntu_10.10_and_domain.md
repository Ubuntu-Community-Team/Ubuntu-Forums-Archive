---
title: "Apache on ubuntu 10.10 and domain"
date: 2012-01-03
forum: Server Platforms
---

### Post by nickos on 2012-01-03
Sorry if that is the wrong section but anyway:

I have used an old pc(amd athlon dual core,4 gb ram) to make it into a web server.i have been trying for over a month and  i successfully installed apache2,mysql,php,in general i made a LAMP server.i also included webmin,phpmyadmin and squirrelmail.i type localhost and i get the server page.I port forwarded it , it was accessible using its IP but now its taking too loong to respond and cant establish connection( [http://192.168.2.2](http://192.168.2.2)) dont know why though :(

my concern is connecting it to a domain from godaddy,how will i do so?

```

<VirtualHost *:80>
    ServerAdmin webmaster@localhost

    DocumentRoot /var/www
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```all i have to do is add ServerName "www.site.com" and ServerAlias "www.site.com" and im done?is it that simple or am i wrong somewhere?

Thanks for any help ubunters!

---

### Post by rsvancara on 2012-01-03
Not necessarily. If you are only hosting one site on this server, then you just need to ensure the "default" works properly.  So you do not have to include ServerName and ServerAlias.  If you plan on having more than one virtual host, then might I suggest you leave the default alone and create a new configuration file in /etc/apache2/sites-available with a different file name, other than default and then use a2ensite to create the symbolic link in /etc/apache2/sites-enabled.  

Also, you may need to use a tool like wireshark or tcpdump to see if the requests are making it to your server and port forward is working correctly.  Also your apache logs are great source of information, especially /var/log/apache2/error.log

Furthermore, several ISP's restrict traffic on port 80 as a way to prevent people from running web servers from their homes. 

I hope this helps.

---

### Post by nickos on 2012-01-03
Hey man,thanks a lot for your help,i really appreciate your reply.


> **rsvancara said:**
> If you plan on having more than one virtual host, then might I suggest you leave the default alone and create a new configuration file in /etc/apache2/sites-available with a different file name, other than default and then use a2ensite to create the symbolic link in /etc/apache2/sites-enabled. 

yes i plan on hosting 2 sites.so i should make 2 different virtualhost files in the sites-available folder and leave the default untouched?

> Also, you may need to use a tool like wireshark or tcpdump to see if the requests are making it to your server and port forward is working correctly.  Also your apache logs are great source of information, especially /var/log/apache2/error.log
Alright,im downloading wireshark at the moment.



> Furthermore, several ISP's restrict traffic on port 80 as a way to prevent people from running web servers from their homes. 

Sorry if i didnt understand what you mean but i managed to port forward apache to my router and it was accesible with its IP by a computer outside the network and i now get the "cannot establish connection" message.

---

### Post by elico on 2012-01-03
the first thing is to make sure that there is no double ip on the same network..
and on the server use the command:
> netstat -ntlp
to know if apache is running and listening to port 80
also try to ping the host ip and see if it's connected to the lan.
also use 
> ifconfig 
to see the network interface settings.
the last thing is to make sure that you have a default route on the linux machine
so try to ping from the server to the world let say 8.8.8.8
and use the command:
> route 
to get the route list.

---

### Post by nickos on 2012-01-03
thanks for your reply.I am using my main computer which happens to have an apache server as well just for testing,its late so i will post my server's results tomorrow:


> netstat -ntlp 

```
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp6       0      0 :::80                   :::*                    LISTEN      -               
tcp6       0      0 ::1:631                 :::*                    LISTEN      -               

```

> ifconfig

```

eth0      Link encap:Ethernet  HWaddr 00:16:17:93:a5:47  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:16:17:93:ab:f4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:47 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2672 (2.6 KB)  TX bytes:2672 (2.6 KB)

wlan0     Link encap:Ethernet  HWaddr f0:7d:68:6c:11:01  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::f27d:68ff:fe6c:1101/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:752948 errors:0 dropped:0 overruns:0 frame:0
          TX packets:457408 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1086493251 (1.0 GB)  TX bytes:46181062 (46.1 MB)

```

> route
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0


```

---

