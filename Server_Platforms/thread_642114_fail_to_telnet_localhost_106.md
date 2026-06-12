---
title: "fail to telnet localhost 106"
date: 2007-12-16
forum: Server Platforms
---

### Post by satimis on 2007-12-16
Hi folks,


Ubuntu 7.04 server amd64


On running;

$ telnet localhost 106```

Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

```


$ netstat -an | grep 106
$ sudo netstat -an | grep 106
both no printout


Pls advise where shall I check and how to fix the problem.  TIA


P.S. 
1)
confirmed with ISP port 106 is open

2)
I'm adding "change password" plugin on SquirrelMail.  After installing poppassd on repo I tested it whether works according to /usr/local/squirrelmail/www/plugins/change_pass/INSTALL```

Be sure to test and make certain your poppass daemon is working properly.
To test, try telneting into the daemon and changing a password:

$ telnet localhost 106
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
200 poppassd v1.8.1 hello, who are you?
user <username>
200 Your password please.
pass <oldpassword>
200 Your new password please.
newpass <newpassword>
200 Password changed, thank-you.
quit
200 Bye.
Connection closed by foreign host.

```





B.R.
satimis

---

### Post by koenn on 2007-12-16
try telnetting the real address of the machine in stead of 127.0.01

---

### Post by satimis on 2007-12-16
> **koenn said:**
> try telnetting the real address of the machine in stead of 127.0.01
Sorry I telnet on the same machine


satimis

---

### Post by koenn on 2007-12-16
> **satimis said:**
> Sorry I telnet on the same machine

I know. 
That machine has an IP address nonetheless (or it should have, otherwise it's not goung to handle much mail). 

run ```
ifconfig
```
it tells you the IP address. use that to telnet. 
There's a good change that whatever you have listening at port 106 is listening on the address of your network interface, not on the loopback interface (aka localhost).

---

### Post by satimis on 2007-12-16
> **koenn said:**
> I know. 
That machine has an IP address nonetheless (or it should have, otherwise it's not goung to handle much mail). 

run ```
ifconfig
```
it tells you the IP address. use that to telnet. 
There's a good change that whatever you have listening at port 106 is listening on the address of your network interface, not on the loopback interface (aka localhost).
I see.


$ telnet 192.168.0.10 106```

Trying 192.168.0.10...
telnet: Unable to connect to remote host: Connection refused

```


$ ifconfig```

eth0      Link encap:Ethernet  HWaddr 00:0E:A6:F9:A3:5B  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:fef9:a35b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28733 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37939499 (36.1 MiB)  TX bytes:4984171 (4.7 MiB)
          Interrupt:21 Base address:0x8000 
.....

```

satimis

---

### Post by koenn on 2007-12-16
I'm 80% sure there's nothing listening at port 106 - thats most often the cause of a "connection refused".
. I suppose you're already running squirellmail ? Maybe you have to restart it to activate the plugin ?

---

### Post by satimis on 2007-12-16
> **koenn said:**
> I'm 80% sure there's nothing listening at port 106 - thats most often the cause of a "connection refused".
. I suppose you're already running squirellmail ? Maybe you have to restart it to activate the plugin ?
SM is now working w/o problem.  I have restarted it many times.


satimis

---

### Post by syadnom on 2008-02-28
any solution here?  i have installed poppassd but dont know how to start it daemonized.  i have nothing listening on port 106 according to netstat -na|grep "LISTEN"

---

### Post by satimis on 2008-02-28
> **syadnom said:**
> any solution here?  i have installed poppassd but dont know how to start it daemonized.  i have nothing listening on port 106 according to netstat -na|grep "LISTEN"
Hi,


I solved my problem by fiddling around on iptables rules.  It was the cause of my problem.  Please run following commands;

iptables -F
iptables -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

(if having nat and mangle, add following commands after "iptable -X"```

iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X

```
)

If it works then the problem comes on the rules.


B.R.
satimis

---

### Post by syadnom on 2008-02-28
I figured it out, I just had to add openbsd-inetd to startup(with sysv-rc-conf).  it wouldnt work until I rebooted also.

---

