---
title: "Apache only works locally"
date: 2008-08-20
forum: Server Platforms
---

### Post by sudo_chop on 2008-08-20
Hey everyone, I just set up an apache server, but now I am testing it out and it seems to only work locally... i can't get the test page up from another host on the network, and it also doesn't answer telnet on port 80. Yes, im a noob, so I probably overlooked something obvious. Help please!

---

### Post by amo-ej1 on 2008-08-20
How did you configure it ? If you goto /etc/apache2/ and type 

```

e@lapedb:/etc/apache2$ grep -ir Listen *
ports.conf:Listen 80
ports.conf:    Listen 443
e@lapedb:/etc/apache2$ cat ports.conf 
Listen 80

<IfModule mod_ssl.c>
    Listen 443
</IfModule>

```

Here it is specified with me to listen on all interface on port 80. Also when I type 

```

edb@lapedb:~$ sudo netstat -anp | grep 80
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      6518/apache2    
...

```

It shows that a process called 'apache2' is listening on port 80 tcp on any interface.

---

### Post by zccpop on 2008-08-21
I have the same question.
can you tell more detailly.

---

### Post by cariboo on 2008-08-21
In a bone stock setup without changing any of the config files you should be able to access your web server by either ip address or hostname. try :

```
wget http://ip_address
```

where ip_address is the ip address of your web server. If it downloads the index.html file, you should be able to access it.

Jim

---

### Post by Retaliation on 2008-08-27
I am having the same problem as the OP. I can view files locally, but cannot get other to view them. Where do I need to specify my ip address others can connect to, and where do I need to redirect my router. Thanks in advance.

---

### Post by patrickballeux on 2008-08-27
Make sure that you did not install a local firewall thus preventing connection from remote desktop.

Also, keep in mind that if you have a router, there is a builtin firewall that you need to open for port 80 (and 443 for HTTPS)...

On way to know that a local firewall is installed is to launch the "dmesg" command in a console.  If you see a lot of data telling that there was incoming connection from port X to destination port Y, you have a firewall...

Also, make sure that your Apache is listening on the network, not only locally.  By default, it should be on the network.

---

### Post by windependence on 2008-08-27
If he can reach the server from other computers on the LAN, Apache is listening on port 80, that isn't the problem.

To the OP, go to [www.canyouseeme.org](www.canyouseeme.org) and check to make sure your port 80 is not being blocked by your ISP. If it is, you will either need a static IP or you will need to sign up for a dynamic DNS service such as no-ip.com.

-Tim

---

### Post by Iowan on 2008-08-27
Somewhere, the server name needs to be changed from 127.0.0.1 (or localhost).  The **/etc/apache2/conf.d/fqdn** file if you built one to eliminate the "apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName" error.  Otherwise, an entry in the **/etc/hosts** file for **127.0.1.1 hostname **might solve the problem. (My server has only the **/etc/hosts** file entry).

---

### Post by cariboo on 2008-08-28
Just as point of reference this is my /etc/hosts file:

```
/etc/hosts
127.0.0.1	localhost
127.0.1.1	Willy.xx.xxxxxxxxx.net	Willy
```

Jim

---

### Post by windependence on 2008-08-28
> **Iowan said:**
> Somewhere, the server name needs to be changed from 127.0.0.1 (or localhost).  The **/etc/apache2/conf.d/fqdn** file if you built one to eliminate the "apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName" error.  Otherwise, an entry in the **/etc/hosts** file for **127.0.1.1 hostname **might solve the problem. (My server has only the **/etc/hosts** file entry).


You can solve this problem by adding the ServerName directive to your /etc/apache2.conf:


```
ServerName yourservername
```

then restart Apache.

-Tim

---

### Post by mbeach on 2008-08-28
like that canyouseeme
nice, easy and simple.

---

### Post by Iowan on 2008-08-29
Another option: Verify that **/etc/apache2/ports.conf** contains the line **Listen 80** - NOT **Listen 127.0.0.1:80**

---

### Post by Bliepo32 on 2008-08-29
Are you connected to the internet by a router? Because it might be that it is blocking the incoming traffic.

---

