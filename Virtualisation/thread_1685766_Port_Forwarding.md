---
title: "Port Forwarding"
date: 2011-02-11
forum: Virtualisation
---

### Post by couper on 2011-02-11
Hi everyone,
 
I have huawei hg521 adsl modem.
My host OS is windows 7 ultimate.
I run ubuntu server with gnome gui on vmware.
My windows ip is 192.168.1.5 and I forward port 80 to this.
I use dyndns and I can connect iis web server from outside.
I forward port 8090 to 192.168.1.4 which is the ip of ubuntu.
I can reach 192.168.1.4:8090 in local network. I configured /etc/init.d/netwotking and /etc/init.d/ports.conf.
 
But I can not reach ubuntu from outside.For example: [http://myname.dyndns.com:8090](http://myname.dyndns.com:8090)
I can reach iis [http://myname.dyndns.com](http://myname.dyndns.com)
In ubuntu I installed apache+php+mysql.
I want to use both of them (ubuntu, windows) for web server.
 
What is my mistake?
 
Thank you...

---

### Post by aromo on 2011-02-11
You need either:
* port translation: Set up your router to forward traffic to myname.dyndns.com on port 8090 to ubuntuhost port 80
* listen on port 8090: Set up your ununtuhost to listen for http connection requests on port 8090

Hope this helps.

---

### Post by couper on 2011-02-11
Hi
Second one is suitable for me:
listen on port 8090: Set up your ununtuhost to listen for http connection requests on port 8090

How can I do that?

---

