---
title: "problem with saned - can't share scanner"
date: 2009-01-09
forum: Server Platforms
---

### Post by neill on 2009-01-09
hi

i'm trying to share my scanner over the LAN

scanner is attached to a headless 8.04 server and all client PCs are on the same subnet

scanner works fine at server end

```
sudo scanimage -L
device `epson:libusb:002:004' is a Epson Perfection1200 flatbed scanner
```

as per the official documentation i start saned with xinetd

```
sudo nano /etc/xinetd.d/saned

service saned
{
socket_type = stream
server = /usr/sbin/saned
protocol = tcp
user = saned
group = scanner
wait = no
disable = no
}
```

also on the server side

```
/etc/services
...
sane-port       6566/tcp        sane saned      # SANE network scanner daemon
...
```

and

```
/etc/sane.d/saned.conf
...
192.168.17.0/24
...
```

and

```
 sudo netstat -nap|grep 6566
tcp        0      0 0.0.0.0:6566            0.0.0.0:*               LISTEN      5908/xinetd
```

by my reckoning that means the scanner should be configured correctly on the server side

on the client (in this case II 8.10)

```
/etc/sane.d/net.conf
...
localhost
192.168.17.50 #the server IP
...
```

but on the client

```
sudo scanimage -L
No scanners were identified ....
```

and, incidentally although i don't know it's relevant,

```
nmap 192.168.17.50
``` doesn't show 6566 listening

i'm clearly missing a (simple) trick as the same server runs samba, ssh and printing services for all the LAN clients without issue

any ideas ?? :confused:

ta

/neill

---

### Post by ecowan on 2009-10-17
Me too.
I've been searching here, there and everywhere for info. Some of what I've found is contradictory (Should I modify udev rules or not?) and much is unclear (Do I put the changes on the server or the client side?)
This is the closest description I have found yet of my own situation, so I add my two cents worth, despite the fact that this thread is nine months old, and has no responses.
- Erny

---

### Post by ecowan on 2009-10-17
Found it!
See
[http://ubuntuforums.org/showthread.php?t=199147&highlight=saned.conf](http://ubuntuforums.org/showthread.php?t=199147&highlight=saned.conf)
- Erny

---

