---
title: "can't start apache2"
date: 2008-12-16
forum: Server Platforms
---

### Post by hugohugo on 2008-12-16
hey,

i get the next problem if i strat or restrat apache2:

hugo@webserver:~$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                       (98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

i look what is on port 80 an that is:

hugo@webserver:~$ sudo netstat -lnp | grep '80'
[sudo] password for hugo: 
unix  2      [ ACC ]     STREAM     LISTENING     17162    5164/seahorse-agent /tmp/orbit-hugo/linc-142c-0-31cd3df3cbe80
unix  2      [ ACC ]     STREAM     LISTENING     18411    5266/bluetooth-appl /tmp/orbit-hugo/linc-1492-0-1fc5cdd18026c
unix  2      [ ACC ]     STREAM     LISTENING     18536    5280/gnome-power-ma /tmp/orbit-hugo/linc-1490-0-7f5346a98a14
unix  2      [ ACC ]     STREAM     LISTENING     18620    5265/evolution-alar /tmp/orbit-hugo/linc-1491-0-5801ba41fd38

nothing i think..

My host file see not to be oke ;) :
127.0.0.1	localhost
127.0.1.1	webserver

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

my ip from my local network is: 192.168.0.12, and the name of my server is webserver.

standard my httpd.conf was emtyp..

i have a the flowing lines:
listen *:80,
ServerName "localhost"

So what i do wrong?

Greets Hugo

p.s. sorry for my bad English ;)

---

### Post by cariboo on 2008-12-16
You should check to see that apache is already running, at the prompt type:

```
ps ax | grep apache
```

if apache is already running the result should be something like this:

```
 ps ax | grep apache
22131 pts/0    R+     0:00 grep apache
24653 ?        Ss     0:06 /usr/sbin/apache2 -k start
27606 ?        S      0:00 /usr/sbin/apache2 -k start
27607 ?        S      0:00 /usr/sbin/apache2 -k start
27608 ?        S      0:00 /usr/sbin/apache2 -k start
27609 ?        S      0:00 /usr/sbin/apache2 -k start
27610 ?        S      0:00 /usr/sbin/apache2 -k start
```

Jim

---

### Post by hugohugo on 2008-12-16
Jim my output is:

hugo@webserver:~$ ps ax | grep apache
16743 pts/0    S+     0:00 grep apache

so thats not good?!

---

### Post by MJN on 2008-12-16
Try **sudo lsof -i :80 **to see what's listening on port 80.
 
Has this only just happened? Or has it never worked?
 
Mathew

---

### Post by cdenley on 2008-12-16
You probably have a line like "Listen 80" defined twice in your configuration.
```

grep Listen /etc/apache2/sites-enabled/* /etc/apache2/mods-enabled/* /etc/apache2/*.conf

```

---

### Post by hugohugo on 2008-12-17
> **cdenley said:**
> You probably have a line like "Listen 80" defined twice in your configuration.
```

grep Listen /etc/apache2/sites-enabled/* /etc/apache2/mods-enabled/* /etc/apache2/*.conf

```

The server was the first days oke..

my output by sudo lsof -i :80 is nothing..

but i cat another error: 
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

i have delete the line listen to 80 from my htppd.conf..

something wrong whit my ports now??

thnx

---

### Post by cdenley on 2008-12-17
The output from the command I suggested might help.

---

### Post by MJN on 2008-12-17
> **hugohugo said:**
> (13)Permission denied: make_sock: could not bind to address 0.0.0.0:80Permission denied? You are still using sudo to attempt to start Apache, right?

Mathew

---

### Post by hugohugo on 2008-12-18
> **MJN said:**
> Permission denied? You are still using sudo to attempt to start Apache, right?

Mathew

Damn.. That was stupid.. forgot sudo..

It works local now :)

but externally it won't work :(..

Have this something to do whit my port now?!

thnx

---

### Post by MJN on 2008-12-18
You will need to provide more information than 'it doesnt work'.
 
Mathew

---

### Post by hugohugo on 2008-12-18
> **MJN said:**
> You will need to provide more information than 'it doesnt work'.
 
Mathew

yeah you are right!

if i reload en restart i get this:

hugo@webserver:~$ sudo /etc/init.d/apache2 reload
 * Reloading web server config apache2                                          apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
hugo@webserver:~$ sudo apache2ctl restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

If i change my ip in my hosts file to 192.168.0.12 i get the same error..

Hopeful you can help me now :)

thnx

---

### Post by cdenley on 2008-12-18
I wouldn't worry about that "error", but you can edit /etc/hostname to set your hostname to a fully qualified domain name, then run
```

sudo hostname mydomain.com

```
and edit /etc/hosts so that hostname resolves to your IP address.

---

### Post by Iowan on 2008-12-18
Adding the line ```
127.0.1.1 <hostname>
``` to /etc/hosts *might* make the error go away. You can also put the FQDN in first:```
127.0.1.1 <hostname.domain> <hostname>
```

---

### Post by MJN on 2008-12-19
> **hugohugo said:**
> yeah you are right!
 
if i reload en restart i get this:
 
hugo@webserver:~$ sudo /etc/init.d/apache2 reload
* Reloading web server config apache2 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[ OK ]You still haven't said in what way it is working locally and not externally!
 
Describe what it is you're trying to do, what you expected to happen and what actually happened.
 
If by external you mean the Internet then also tell us the URL then we can check the DNS configuration is correct and attempt a connection from the outside.
 
Mathew

---

