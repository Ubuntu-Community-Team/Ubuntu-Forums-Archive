---
title: "named is listening on the wrong port."
date: 2010-07-11
forum: Server Platforms
---

### Post by wlraider70 on 2010-07-11
update: 
```

luke@media:~$ sudo service bind9 restart
 * Stopping domain name service... bind9                                                         rndc: recv failed: connection reset
                                                                                          [ OK ]
 * Starting domain name service... bind9                                                  [ OK ] 
luke@media:~$ sudo service bind9 start
 * Starting domain name service... bind9                                                  [ OK ] 
luke@media:~$ 


```


As far as i can tell named is listening to the wrong port.
I've run alot of coded that don't make too much sense



I ran 

luke@media:~$ named -g -p 53

```

11-Jul-2010 16:18:59.562 starting BIND 9.5.1-P2.1 -g -p 53
11-Jul-2010 16:18:59.563 found 1 CPU, using 1 worker thread
11-Jul-2010 16:18:59.563 using up to 4096 sockets
11-Jul-2010 16:18:59.570 loading configuration from '/etc/bind/named.conf'
11-Jul-2010 16:18:59.571 max open files (1024) is smaller than max sockets (4096)
11-Jul-2010 16:18:59.571 using default UDP/IPv4 port range: [1024, 65535]
11-Jul-2010 16:18:59.571 using default UDP/IPv6 port range: [1024, 65535]


11-Jul-2010 16:18:59.575 listening on IPv4 interface lo, 127.0.0.1#53
11-Jul-2010 16:18:59.576 could not listen on UDP socket: permission denied
11-Jul-2010 16:18:59.576 creating IPv4 interface lo failed; interface ignored
11-Jul-2010 16:18:59.576 listening on IPv4 interface eth0, 10.10.10.2#53
11-Jul-2010 16:18:59.576 could not listen on UDP socket: permission denied
11-Jul-2010 16:18:59.598 creating IPv4 interface eth0 failed; interface ignored
11-Jul-2010 16:18:59.599 not listening on any interfaces
11-Jul-2010 16:18:59.605 automatic empty zone: 254.169.IN-ADDR.ARPA
11-Jul-2010 16:18:59.606 automatic empty zone: 2.0.192.IN-ADDR.ARPA
11-Jul-2010 16:18:59.606 automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
11-Jul-2010 16:18:59.606 automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
11-Jul-2010 16:18:59.606 automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
11-Jul-2010 16:18:59.606 automatic empty zone: D.F.IP6.ARPA
11-Jul-2010 16:18:59.606 automatic empty zone: 8.E.F.IP6.ARPA
11-Jul-2010 16:18:59.606 automatic empty zone: 9.E.F.IP6.ARPA
11-Jul-2010 16:18:59.606 automatic empty zone: A.E.F.IP6.ARPA
11-Jul-2010 16:18:59.606 automatic empty zone: B.E.F.IP6.ARPA
11-Jul-2010 16:18:59.615 couldn't add command channel 127.0.0.1#953: permission denied
11-Jul-2010 16:18:59.616 couldn't add command channel ::1#953: permission denied
11-Jul-2010 16:18:59.616 the working directory is not writable
11-Jul-2010 16:18:59.616 ignoring config file logging statement due to -g option
11-Jul-2010 16:18:59.616 couldn't open pid file '/var/run/bind/run/named.pid': Permission denied
11-Jul-2010 16:18:59.616 exiting (due to early fatal error)
luke@media:~$ 


```


so how do i make it change to port 953?

Iv tried commands like 
named -p 953

it seems to do nothing


I also tried this, though i dount really understand it


luke@media:~$ sudo netstat -punta | grep named

```

tcp        0      0 10.10.10.2:953          0.0.0.0:*               LISTEN      8517/named      
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      8517/named      
tcp6       0      0 ::1:953                 :::*                    LISTEN      8517/named      
udp        0      0 10.10.10.2:53           0.0.0.0:*                           28307/named     
udp        0      0 127.0.0.1:53            0.0.0.0:*                           28307/named     
udp        0      0 10.10.10.2:53           0.0.0.0:*                           28032/named     
udp        0      0 127.0.0.1:53            0.0.0.0:*                           28032/named     
udp        0      0 10.10.10.2:53           0.0.0.0:*                           32557/named     
udp        0      0 127.0.0.1:53            0.0.0.0:*                           32557/named     
udp        0      0 10.10.10.2:53           0.0.0.0:*                           32290/named     
udp        0      0 127.0.0.1:53            0.0.0.0:*                           32290/named     
udp        0      0 10.10.10.2:53           0.0.0.0:*                           31915/named     
udp        0      0 127.0.0.1:53            0.0.0.0:*                           31915/named     
udp        0      0 10.10.10.2:53           0.0.0.0:*                           31558/named     
udp        0      0 127.0.0.1:53            0.0.0.0:*                           31558/named     
udp        0      0 10.10.10.2:953          0.0.0.0:*                           8517/named      
udp        0      0 127.0.0.1:953           0.0.0.0:*                           8517/named      
udp6       0      0 :::53                   :::*                                28307/named     
udp6       0      0 :::53                   :::*                                28032/named     
udp6       0      0 :::53                   :::*                                32557/named     
udp6       0      0 :::53                   :::*                                32290/named     
udp6       0      0 :::53                   :::*                                31915/named     
udp6       0      0 :::53                   :::*                                31558/named     
luke@media:~$ 

```

and

```

luke@media:~$ sudo netstat -paln | grep 953
tcp        0      0 10.10.10.2:953          0.0.0.0:*               LISTEN      8517/named      
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      8517/named      
tcp6       0      0 ::1:953                 :::*                    LISTEN      8517/named      
udp        0      0 10.10.10.2:953          0.0.0.0:*                           8517/named      
udp        0      0 127.0.0.1:953           0.0.0.0:*                           8517/named      
unix  3      [ ]         STREAM     CONNECTED     6953     2602/dbus-daemon    
luke@media:~$ 

```

---

### Post by gombadi on 2010-07-11
> 
As far as i can tell named is listening to the wrong port.

so how do i make it change to port 953?


The normal port for bind is udp port 53 for dns requests and port 953 for control purposes.

> 
I also tried this, though i dount really understand it
luke@media:~$ sudo netstat -punta | grep named


This command shows what ports the named process is using.

> 
luke@media:~$ sudo netstat -paln | grep 953
tcp        0      0 10.10.10.2:953          0.0.0.0:*               LISTEN      8517/named      
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      8517/named      
tcp6       0      0 ::1:953                 :::*                    LISTEN      8517/named      
udp        0      0 10.10.10.2:953          0.0.0.0:*                           8517/named      
udp        0      0 127.0.0.1:953           0.0.0.0:*                           8517/named


This shows that named is currently listening on port 953.

Why are you trying to change the port for bind? It should work fine on the standard ports.

---

### Post by wlraider70 on 2010-07-11
I thought that I was supposed to set it to port 953.

I must have been confused by the difference, so do i need go back to conf and stuff and set it back to 53.

---

### Post by wlraider70 on 2010-07-12
I tried running it on 53 like guess im supposed to

i have these out puts

```


luke@media:~$ **sudo service bind9 restart**
 * Stopping domain name service... bind9                                        rndc: connection to remote host closed
This may indicate that
* the remote server is using an older version of the command protocol,
* this host is not authorized to connect,
* the clocks are not syncronized, or
* the key is invalid.
                                                                         [ OK ]
 * Starting domain name service... bind9                                        named: chroot(): No such file or directory
                                                                         [fail]
luke@media:~$ **sudo service bind9 start**
 * Starting domain name service... bind9                                        named: chroot(): No such file or directory
                                                                         [fail]
luke@media:~$ **named -g -p 53**
11-Jul-2010 22:13:57.087 starting BIND 9.5.1-P2.1 -g -p 53
11-Jul-2010 22:13:57.088 found 1 CPU, using 1 worker thread
11-Jul-2010 22:13:57.089 using up to 4096 sockets
11-Jul-2010 22:13:57.095 loading configuration from '/etc/bind/named.conf'
11-Jul-2010 22:13:57.095 none:0: open: /etc/bind/named.conf: permission denied
11-Jul-2010 22:13:57.096 loading configuration: permission denied
11-Jul-2010 22:13:57.096 exiting (due to fatal error)
luke@media:~$ 

```

---

### Post by wlraider70 on 2010-07-13
for posterity sake 

I had to stop app armor

"sudo service apparmor stop"


Then I had to run 

"sudo named -g -p 53"

running it as root was important. This continually spit out errors and i had to work on them.






Lastly, it did stay as running, however i still don't have internet on this box. I don't know if its related to bind9 or not.

---

