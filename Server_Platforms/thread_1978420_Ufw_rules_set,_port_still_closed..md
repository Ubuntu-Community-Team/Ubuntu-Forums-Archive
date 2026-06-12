---
title: "Ufw rules set, port still closed."
date: 2012-05-11
forum: Server Platforms
---

### Post by moojuice46 on 2012-05-11
There are a lot of posts about this on the forums.  I have read through them with out an answer to this problem.  nmap all ports filtered, online scans port closed.  The end game is to get murmur to accept incoming connections on that port.  Ubuntu 12.04, just Ubuntu firewall no router. If someone could help me much appreciated.

```

ufw status verbose 
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
59151                      ALLOW IN    Anywhere
59151                      ALLOW IN    Anywhere (v6)

``````

netstat -ntlp
Active Internet connections (only servers)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1906/dnsmasq    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1160/cupsd      
tcp        0      0 127.0.0.1:6502          0.0.0.0:*               LISTEN      1411/murmurd    
tcp6       0      0 ::1:631                 :::*                    LISTEN      1160/cupsd 

```Any other info you need let me know.

---

### Post by The Cog on 2012-05-11
According to netstat, nothing is listening on port 59151. That's nothing to do with the firewall, that's because no application has started listening. Either your server software isn't running, or isn't configured right.

Or maybe murmur is a UDP app (I don't know what murmur is) - you only listed the listening TCP ports.

---

### Post by darkod on 2012-05-11
What if you open port 6502 that murmurd is listening on?

---

### Post by moojuice46 on 2012-05-11
Thank you for your suggestions, helped find a new path of troubleshooting. Got it listening on port 59151. I can connect through 127.0.0.1, but not my ip address.  Scans still showing filtered. Any suggestions?

```
sudo netstat -ntlp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1906/dnsmasq    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1160/cupsd      
tcp        0      0 127.0.0.1:6502          0.0.0.0:*               LISTEN      4300/murmurd    
tcp6       0      0 :::59151                :::*                    LISTEN      4300/murmurd    
tcp6       0      0 ::1:631                 :::*                    LISTEN      1160/cupsd 
```

---

### Post by darkod on 2012-05-11
But it listens on 59151 only for IPv6, not for IPv4. This should work but if you use IPv6 only.

For IPv4 it still listens only on localhost, not on all addresses.

Look at the first column, tcp, tcp6.

---

### Post by moojuice46 on 2012-05-12
I had to specify my ip in the mumble-server.ini.  Was supposed to be fixed bug while back, but didint work correctly with out it for me.  Thanks for the help.

---

