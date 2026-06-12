---
title: "can't connect to the server from some parts of the internal network"
date: 2012-01-02
forum: Server Platforms
---

### Post by herbert tamayo on 2012-01-02
Hi, I have this scenario at my work:

Section 1:
-1 server and 5 pcs connected to the same network switch (swicth 1)
-these 5 pcs can connect to the server without any problem, the response time are good.

Section 2:
-6 pcs connected to another network switch (switch 2), switch 2 is connected to switch 1 using an UTP cable that is 25 mts of length.

the problem:
the 6 pcs connected in switch 2 can't connect to the server, when I say can't connect I mean I use my web browser and then type:

[http://ipserver/mysystem](http://ipserver/mysystem)

the error gotten is:
110 connection timed out

the system was coded using LAMP.

The server is ubuntu server 11.04

I'm connected to the network from switch 2, I have tried to connect to the server via ssh and it works, i can do ping to the server and also works, the TTL gotten seems ok (1 ms).

So my questions are:
1. why I can't connect from switch 2 to the server via web browser? ([http://10.10.1.3/mysystem](http://10.10.1.3/mysystem))

2. what commands should I use to check the connectivity via port 80?

3. this problem could be a networking issue? maybe the switch can't map the ip in switch 1?

4. any suggestions?

regards

---

### Post by HugoSerrano on 2012-01-02
Hello!

What's the IP address, with masks, from Server and from one of the PC's that can't connect to server?
In MicroSoft do ```
ipconfig /all
```
In all mighty Linux ```
ifconfig
```



Tests you can do:

from pc:

ping the server ```
ping 10.10.1.3
```
telnet to the http port ```
telnet 10.10.1.3 80
```
ping other pc in the switch2
ping other pc in the switch1

from server:
ping one pc in the switch2

Best Regards!!

---

