---
title: "Fingerd setup"
date: 2008-03-26
forum: Server Platforms
---

### Post by Dr Small on 2008-03-26
I completely understand the security problems of running fingerd, but I want to test with it, and it seems like it is having a difficult time.

So I installed it:
```
sudo apt-get install fingerd
```

Then I looked for it:
```
drsmall@mycroft:~$ whereis fingerd
fingerd:
```

No results... hrm.
There are also no man pages on it, and when I try to connect to it, I get this:
```
drsmall@mycroft:~$ finger @localhost
[localhost]
finger: connect: Connection refused
```

What am I doing wrong, or what did I fail to do?

Dr Small

---

### Post by Dr Small on 2008-03-26
Scrap that...
I figured out how to get inetd to work, have ffingerd installed, and when inetd is started I get:
```
drsmall@darkghost:~$ finger drsmall@192.168.0.70
[192.168.0.70]
```

When inetd is stopped, I get:
```
drsmall@darkghost:~$ finger drsmall@192.168.0.70
[192.168.0.70]
finger: connect: Connection refused
```

Here is the finger entry in inetd.conf:
```
finger          stream  tcp     nowait  nobody  /usr/sbin/tcpd  /usr/sbin/ffingerd
```

Dr Small

---

