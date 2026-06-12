---
title: "Whats happening ? I'm paranoid and anxious"
date: 2011-03-11
forum: Security
---

### Post by plunksnakotis on 2011-03-11
Hello to everyone ! I'm new to these forums and quite new to linux systems. I encountered with such security problem and if anyone can answer it would be very nice ! I'm willing to teach myself ,but at the moment I can't understand whats happening ...

So lets start ...

```


yy@xx:~$ netstat -pantu
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:7175          0.0.0.0:*               LISTEN      -               
tcp        0      0 192.168.1.205:47487     74.125.43.101:80        ESTABLISHED 1962/firefox-bin
tcp6       0      0 ::1:7175                :::*                    LISTEN      -               
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -               
udp        0      0 0.0.0.0:48236           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           -               
udp6       0      0 :::34679                :::*                                -               
udp6       0      0 ::1:35819               ::1:35819               ESTABLISHED -               
udp6       0      0 :::5353                 :::*                                -               



```As you can see there is connection to ubuntuforums.org because at the moment i'm writing this message. So only this one established connection has its PID/Program name and it's being firefox... But who is listening on local adress 127.0.0.1:7175 for ANY foreign address ? And you see tcp6 also listens to any foreign address. I'm really worried about this thing.. If someone can make this clear - please... And why there is no PID/Program name stated in any other connections ? I know 68 udp is for dhcp, but what is these other connections. Please explain to newbie someone !

lsof -Pnl +M -i4 doesn't give any output. What else should I check ? How to find out what program is listening and for what purposes ? This is desktop PC ... with Speedtouch dsl router. Thats it. Thank you alot for your help !


Sorry for this nonsense !!!! I'm dumb :))) I logged in as root and I was able to see what are these things ....
So let this thread be an example for others how not to ask dumb questions ...
So I typed :
```

su
netstat -pantu

```

and here is the output : 

```

root@kamp:/home/nhoj/Downloads/chkrootkit-0.49# netstat -pantu
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:7175          0.0.0.0:*               LISTEN      1247/postgres   
tcp6       0      0 ::1:7175                :::*                    LISTEN      1247/postgres   
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1086/dhclient   
udp        0      0 0.0.0.0:48236           0.0.0.0:*                           966/avahi-daemon: r
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           966/avahi-daemon: r
udp6       0      0 :::34679                :::*                                966/avahi-daemon: r
udp6       0      0 ::1:35819               ::1:35819               ESTABLISHED 1247/postgres   
udp6       0      0 :::5353                 :::*                                966/avahi-daemon: r

```

---

### Post by The Cog on 2011-03-13
Note that if something is listening on 127.0.0.1 or on ::1, then it is listening on the loopback address which cannot be connected to across a network - it can only talk to other processes on the same box. It is quite normal to have a few local machine services listening on the loopback port.

---

### Post by Irihapeti on 2011-03-13
It looks as though you are running a Postgresql database It's possible that it was installed automatically as a dependency of another program.

If so, then it's normal behaviour for Postgresql to be listening on the loopback address.

---

