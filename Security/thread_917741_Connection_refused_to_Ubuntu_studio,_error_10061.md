---
title: "Connection refused to Ubuntu studio, error 10061"
date: 2008-09-12
forum: Security
---

### Post by delusion8282 on 2008-09-12
hello, I am trying to connect from a windows machine to my ubuntu through a socket, i checked on the ubuntu and the port 33337 is open (which is what i need), when i try to connect to this port, or to any other port on the ubuntu machine (except the ssh (22) one), i get an error 10061, connection refused. When i try to connect the windows machine to any other machine (with the same port) it works fine, so i guess the problem is security on my ubuntu.
I checked the hosts.allow hosts.deny, and they are empty, nothing is denied for now. 
I struggling to get this to work, I am a newbie in ubuntu. I would appreciate any help.
cheers.

---

### Post by cdenley on 2008-09-12
> **delusion8282 said:**
> hello, I am trying to connect from a windows machine to my ubuntu through a socket, i checked on the ubuntu and the port 33337 is open (which is what i need), when i try to connect to this port, or to any other port on the ubuntu machine (except the ssh (22) one), i get an error 10061, connection refused. When i try to connect the windows machine to any other machine (with the same port) it works fine, so i guess the problem is security on my ubuntu.
I checked the hosts.allow hosts.deny, and they are empty, nothing is denied for now. 
I struggling to get this to work, I am a newbie in ubuntu. I would appreciate any help.
cheers.
Are you sure there is a server listening? Have you configured your iptables firewall to block connections?
```

sudo netstat -ptunl
sudo iptables -L

```

---

### Post by delusion8282 on 2008-09-12
This is what netstat -ptunl gives for the connection I opened (port is the right one):
> 
Proto Recv-Q Send-Q Local Address Foreign Address State   PID/Program name  
tcp       0         0       127.0.0.1:33337      0.0.0.0:*     LISTEN        5876/mha  

and here is the iptables -L :
> 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination        

Is this wrong in anyway?
Thanks

---

### Post by cdenley on 2008-09-12
> **delusion8282 said:**
> This is what netstat -ptunl gives for the connection I opened (port is the right one):

and here is the iptables -L :

Is this wrong in anyway?
Thanks

Your program, mha, is binding to the local loopback device, so other computers wouldn't be able to connect to it.

---

### Post by delusion8282 on 2008-09-12
> **cdenley said:**
> Your program, mha, is binding to the local loopback device, so other computers wouldn't be able to connect to it.

Sorry for ignorance, but how can I fix it?

---

### Post by cdenley on 2008-09-13
> **delusion8282 said:**
> Sorry for ignorance, but how can I fix it?

I don't know, what's mha? It's probably just a matter of configuration.

---

### Post by delusion8282 on 2008-09-13
> **cdenley said:**
> I don't know, what's mha? It's probably just a matter of configuration.

mha is just a "signal processing framework", but it works as it is when you open it on another "linux" it works, can you explain to me how it could loopback to the local device? what is the idea?

---

### Post by cdenley on 2008-09-13
> **delusion8282 said:**
> mha is just a "signal processing framework", but it works as it is when you open it on another "linux" it works, can you explain to me how it could loopback to the local device? what is the idea?

Server software has to choose the interface which it binds to.
[http://www.rt.com/man/bind.2.html](http://www.rt.com/man/bind.2.html)
Typically, this interface is determined by settings in it's configuration file. I'm not familiar with how to configure the server you are trying to run. When it binds to 127.0.0.1, you can only access it locally by connecting to 127.0.0.1. When it binds to 0.0.0.0, it will listen for all connections on all interfaces.

---

### Post by delusion8282 on 2008-09-13
> **cdenley said:**
> Server software has to choose the interface which it binds to.
[http://www.rt.com/man/bind.2.html](http://www.rt.com/man/bind.2.html)
Typically, this interface is determined by settings in it's configuration file. I'm not familiar with how to configure the server you are trying to run. When it binds to 127.0.0.1, you can only access it locally by connecting to 127.0.0.1. When it binds to 0.0.0.0, it will listen for all connections on all interfaces.

Awesome, now i understand it. I can change that in the config files. Thanks a lot dude.

---

