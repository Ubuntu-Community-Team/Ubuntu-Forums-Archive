---
title: "Viewing HTML file from different computer on home network"
date: 2019-03-22
forum: Server Platforms
---

### Post by neutronforrest on 2019-03-22
Dear All,

I have successfully  setup a server on an ubuntu computer.  I used Nginx and setup an example  .html file.  To see the server on this local computer in the web browser I had to add this  to /etc/hosts

192.168.x.x [www.example.com]("http://www.example.com")

I can now login into the web browser and see my simple text from the  .html file.  My issues is that I cannot see this file from another  computer within my home network.  I can see the default nginx page using  the IP address 192.168.x.x but I am unable to see [www.example.com]("http://www.example.com").  I have disabled the ufw.  Here is my simple .conf file.

server {
    listen 80;
    listen [::]:80;
    root /var/www/example;
    index index.html;
    server_name [www.example.com;]("http://www.example.com;")
}

When I type wget -O- [http://192.168.1.101/var/www/example.index.html](http://192.168.1.101/var/www/example.index.html)

--2019-03-21 09:59:48--  [http://192.168.1.101/var/www/example.index.html](http://192.168.1.101/var/www/example.index.html)
Connecting to 192.168.x.x:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2019-03-21 09:59:48 ERROR 404: Not Found.

Any help is appreciated.

---

### Post by TheFu on 2019-03-22
Put 
```
192.168.x.x www.example.com
```
into every /etc/hosts file on the other computers you want to have access. Use the real IP, and it should be static --- for the web server.
If DHCP is used by the web-server, then the IP can change.

---

