---
title: "Network connection and python"
date: 2012-01-23
forum: Security
---

### Post by MadsRC on 2012-01-23
I just reinstalled my system and removed the few applications I don't need.

Then I set up conky, with the transmission python script and sat up my conky.

Now, the funny thing is, I SSH'ed into my work server and downloaded a bash script I made to test it out.
I ran it and it utilises "sudo netstat -tupan"

When I did that, I got the following:

```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1048/cupsd      
tcp        0      0 xx.xx.xx.xx:37573      xx.work.server.xx:22        ESTABLISHED 5059/ssh        
tcp        0      0 xx.xx.xx.xx:42622      66.220.151.99:5222      ESTABLISHED 5545/telepathy-gabb
tcp        0      0 xx.xx.xx.xx:56068      64.4.61.173:1863        ESTABLISHED 4225/python     
tcp6       0      0 ::1:631                 :::*                    LISTEN      1048/cupsd      
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1456/dhclient   
udp        0      0 0.0.0.0:43763           0.0.0.0:*                           944/avahi-daemon: r
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           944/avahi-daemon: r
udp6       0      0 :::50348                :::*                                944/avahi-daemon: r
udp6       0      0 :::5353                 :::*                                944/avahi-daemon: r

```I ofcourse censored my IP and my servers IP.

From what I can read, I get that I'm connected to my work server on port 22, using 5059/ssh, I'm connected to a telepathy service using 5545/telepathy-gabb (as telepathy is running in the background).

BUUUUT I don't get the connection to 64.4.61.173:1863 though 4225/python ?
The system is pretty brand new, and the only thing I used python for is my python script for transmission (Also install transmission-cli and enabled the webclient of transmission)

Does anyone know if it is a legitimate connection and what the connection is used for?

---

### Post by MadsRC on 2012-01-23
I tried a lookup on the IP, and got this response:
```
IP address: 64.4.61.173
Host name: baymsg1020223.gateway.edge.messenger.live.com

64.4.61.173 is from United States(US) in region North America


```



From what I can see it's some messenger service. I did log on to live.com to ban a contact of mine which was spamming me. Guess that is what is causing the connection?

---

### Post by MadsRC on 2012-01-23
False alarm, after a reboot the connection is gone.

From the lookup I guess it was because of a former connection to the live.com server.

---

### Post by Rob_H on 2012-01-23
For future reference, you can run this to see the entire command line that started the Python process. Might give you some idea as to what it is:

```

sudo cat /proc/<pid>/cmdline

```

Where *<pid>* is the process ID you get from netstat.

---

