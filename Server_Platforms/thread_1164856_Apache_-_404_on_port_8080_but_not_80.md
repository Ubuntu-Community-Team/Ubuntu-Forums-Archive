---
title: "Apache - 404 on port 8080 but not 80"
date: 2009-05-20
forum: Server Platforms
---

### Post by peedeeramone on 2009-05-20
Ive got a desktop/home server that i want to get apache running on. ive got apache2 on it and have it set to listen to both port 80 and port 8080 in the ports.conf file. Port 80 works fine locally, but port 8080 gives me a 404 not found error. I want to be able to get it online but my isp blcoks port 80. I went ahead to get port forwarding enabled on my router (tomato) for port 8080. I setup a host name at [www.dyndns.com](www.dyndns.com) to forward to port 8080. Tomato also has a setup to automatically report its ip to dyndns (nice!). I cant get to it find it remotely.

Any suggestions? theres gotta be something i missed..

---

### Post by peedeeramone on 2009-05-20
bump

---

### Post by Iowan on 2009-05-20
Does Tomato give you the option to forward port 8080 to port 80?

---

### Post by peedeeramone on 2009-05-20
yeah ive tried that. still no go. i now have it set up to listen on port 80 and port 8080. locally both work, neither work from outside.

---

### Post by auszen on 2010-03-17
[Dead Thread?]

I had a same problem.

IP:80 - Works || internal & external
IP:8080 - internal works || 404 Error external

My fix, 
```
sudo gedit /etc/apache2/sites-available/default
```
In default make a second copy of <VirtualHost *:80> ~~~~ </VirtualHost>
On the second copy Change <VirtualHost *:80> to <VirtualHost *:8080>
Save and Exit.
```
sudo /etc/init.d/apache2 restart
```

IP:80   - Works || internal & external
IP:8080 - Works || internal & external

---

