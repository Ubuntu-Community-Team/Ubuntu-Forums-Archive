---
title: "Webmin Help"
date: 2009-12-04
forum: Server Platforms
---

### Post by tekkidd on 2009-12-04
HI i am have been using Ubuntu for about 10 months now and have a server running. I have loaded webmin on my computer and whenever i log into my computer with webmin ([https://localhost:10000](https://localhost:10000)) it works just fine but whenever i try to log into my server ([https://192.168.1.xxx:10000](https://192.168.1.xxx:10000)) it tells me that it cant make a connection. What am i doing wrong

---

### Post by tekkidd on 2009-12-04
Just figured it out you have to install webmin on both machenes

---

### Post by volkswagner on 2009-12-04
You actually only need to install webmin on the server, or machine you want to administer.

---

### Post by munky99999 on 2009-12-04
As far as I read. Webmin isn't supposed to be run on ubuntu. Which is why it's not put in the repos. The ubuntu web management is ebox or ssh.


[https://192.168.1.xxx:10000](https://192.168.1.xxx:10000)

You dont have to xxx out the ip. 192.168 is a private network.

---

### Post by Queue29 on 2009-12-05
> **munky99999 said:**
> As far as I read. Webmin isn't supposed to be run on ubuntu. Which is why it's not put in the repos. The ubuntu web management is ebox or ssh.


[https://192.168.1.xxx:10000](https://192.168.1.xxx:10000)

You dont have to xxx out the ip. 192.168 is a private network.

If webmin isn't supposed to run on ubuntu you might want to tell these guys [http://www.turnkeylinux.org/](http://www.turnkeylinux.org/) .

Webmin is just a way to interact with your server over the internet. In runs on the **server** and delivers webpages to administer from, not the host machine.

And webmin is in the ubuntu repositories. 
```
aptitude search webmin
```

---

### Post by tekkidd on 2010-01-06
> **munky99999 said:**
> As far as I read. Webmin isn't supposed to be run on ubuntu. Which is why it's not put in the repos. The ubuntu web management is ebox or ssh.


[https://192.168.1.xxx:10000](https://192.168.1.xxx:10000)

You dont have to xxx out the ip. 192.168 is a private network.


really works just fine for me

---

### Post by Skidbladniir on 2010-01-07
Yes, but it requires an SSL certificate... X_X I don't have one.  Anyway, it's true.  192.168.0.0 to 192.168.255.255 are all private IP addresses.  People can't type them in and go to a website.  They're only useful for LAN sites (Such as a router login) and port forwarding (Forwarding requests to a router to a local IP address if you have multiple servers.).

---

### Post by dalitso on 2010-01-07
What is in your /etc/hosts
```
sudo nano /etc/hosts
```

---

