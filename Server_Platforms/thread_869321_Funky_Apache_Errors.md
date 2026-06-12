---
title: "Funky Apache Errors"
date: 2008-07-24
forum: Server Platforms
---

### Post by Initsil on 2008-07-24
Could anyone tell me how to fix this?:

```
 * Starting web server apache2
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
   ...fail!
```

Here's my ports file: 

```
administrator@Ubuntu-Webserver:~$ more /etc/apache2/ports.conf
Listen 80

```

My httpd.conf file is blank, I'm not sure if that could tell you anything: 

```
administrator@Ubuntu-Webserver:~$ more /etc/apache2/httpd.conf
administrator@Ubuntu-Webserver:~$ 
```

Any help would be appreciated.

Initsil

---

### Post by windependence on 2008-07-24
What is in your apache.conf?

-Tim

---

### Post by Initsil on 2008-07-24
Here's my conf file:

[http://pastebin.com/d5afd42c1](http://pastebin.com/d5afd42c1)

---

### Post by windependence on 2008-07-24
Sorry, I meant /etc/apache2/apache2.conf.

-Tim

---

### Post by Initsil on 2008-07-24
Here:

[http://pastebin.com/m2cc79cab](http://pastebin.com/m2cc79cab)

---

### Post by windependence on 2008-07-24
What is the ouput of 

```
hostname -f
```

-Tim

---

### Post by Initsil on 2008-07-24
It's

Ubuntu-Webserver

I actually got it working again. I had a process from aol server that I just killed.

---

### Post by windependence on 2008-07-24
aol server? Yikes, what is THAT? Yuck.

-Tim

---

### Post by Initsil on 2008-07-24
I use it for my open ssh server

when I installed it i ran this:

sudo apt-get install openssh*

it's kinda messing up the whole server. now i can't get apache2 to parse php :S

---

