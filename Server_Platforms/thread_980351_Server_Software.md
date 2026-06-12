---
title: "Server Software?"
date: 2008-11-12
forum: Server Platforms
---

### Post by basicxman on 2008-11-12
Is there some sort of software/script that I can enter the URL of a domain I want to host and it does the rest from there?
Basically I want something that can turn my old dusty computer to [www.example.com](www.example.com)

Is there a tutorial for this?

---

### Post by spiderbatdad on 2008-11-12
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

it seems like you are asking about running a server on your machine. If your machine has ubuntu installed, just enter this in a terminal```
sudo apt-get install apache2
```then open your web browser and type localhost into the address bar.
Domain names must be registered, free or purchased, with a naming service. Otherwise you would access your page via ip address.

So I think the answer to your question is no. There is no simple script that will do everything for you, as far as web hosting goes.

---

### Post by oneloveamaru on 2008-11-12
Or you can just create a host entry on your client computer and point it to your server and never register a domain name. :) Until you want outside people being able to connect to it, this should work for you. Edit /etc/hosts with your favorite editor. :)

---

### Post by basicxman on 2008-11-18
What is required to get from localhost to [www.example.com?](www.example.com?)

---

### Post by spiderbatdad on 2008-11-18
> **basicxman said:**
> What is required to get from localhost to [www.example.com?](www.example.com?)


This question is a bit vague. Are asking how to register a domain and access your server from the internet? You can do this for free by regitering a name with dyn.dns. You  can also use your ip address. If you have a router you must configure it to forward port 80 to the internal ip of your server. 
You should look for some apache how to guides:[http://www.linux.com/feature/118471](http://www.linux.com/feature/118471) ...for example. Note, you will have to familiarize yourself with the config files. I noticed that how-to uses httpd.conf...while Ubuntu's default installation of apache2 includes directives from that file...much configuration is done in apache2.conf, sites-enabled, and conf.d/security.
It isn't to difficult once you read a few tutorials on basic operation of apache.

---

