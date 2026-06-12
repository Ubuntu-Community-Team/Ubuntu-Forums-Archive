---
title: "ubuntu turning spyware?"
date: 2007-04-19
forum: Server Platforms
---

### Post by nixclusive on 2007-04-19
Hello everybody, I've noticed that my (k)Ubuntu Dapper Drake machine is always trying to connect to some "leningradskaya.canonical.com" all the time. I got that from the output of ```
netstat -tap
``` Something always tries to connect to leningradskaya.canonical.com:www even after I shutdown my network device. The output from netstat doesn't show any process related to that connection. Can anybody explain what's going on? Is there something installed in ubuntu 6.06 that can be classified as spyware? This is getting me wiry all over now...

---

### Post by nixclusive on 2007-04-20
hell now that I'm noticing, its connecting to somewhere else!! here's the output from netstat:
```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      1 192.168.1.2:3622        prat.canonical.com:www  SYN_SENT   7449/http           
tcp        1      0 192.168.1.2:2376        auckland.ubuntu.com:www CLOSE_WAIT 7446/http   
```

the process id 7449 and 7446 in /proc/<pid> give the file /usr/lib/apt/methods/http as the origin of these connections. Ok I understand that apt may be updating something but I don't have anything that says "prat.canonical.com" in my sources.list. And besides, is apt really supposed to update itself or anything without that invocation of "apt-get update" ??

Any help?? thanks in advance... :)

---

### Post by ubuntu27 on 2007-04-20
Hope some Knowledgeable ones will responds to this... 

Or someone so curious an knows how to look into things unlike me.

---

### Post by wormser on 2007-04-20
I found data.coremetrics.com via ntop.  There were 4.4 KB sent.  I am also interested in what it is.

---

### Post by blitzer on 2007-04-20
My guess would be "Statistics being done"   If you check System> Administration> Software Sources then the last tab and see if the box is ticked for Submit Statistical Information.   Quote "Used to improve the user experience of Ubuntu"......   :lolflag: 

If not this  :confused: 

Blitz

---

### Post by yc2 on 2007-07-25
Ubuntu sometimes tells me: "New updates available". To know this it would have to connect to the internet, I assume. Could this be the reason? But I agree, for safety I think every software should give me an option to know when and why it goes surfing the net. (Also, having "prat" in a domain-name seems a little strange, doesn't it?) :)
EDIT: The "statistics" check-box discussed above is not set in my system. It seems one has to make an active choice to agree to send statistics.

---

### Post by steveneddy on 2007-07-25
It's the update info for all versions of Ubuntu. 

These are the servers that check for updates and give users and other servers info to DL to us, the U Community, updates when they become available.

---

