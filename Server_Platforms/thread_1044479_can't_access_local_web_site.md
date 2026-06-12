---
title: "can't access local web site"
date: 2009-01-19
forum: Server Platforms
---

### Post by Nitewalker on 2009-01-19
I can't access my web site that is on Apache2 from my local machine that is the web server, but I can access it from other computers not on my network?  I have read several different posts on the subject but not having any luck in getting it to work.  I am using a dynamic IP and have ports 80 open and firewall shut down, but still work access from local machine?:confused:

---

### Post by Maheriano on 2009-01-19
Try going to:
[http://localhost](http://localhost)
or
[http://127.0.0.1](http://127.0.0.1)

If not that, then run /ifconfig in terminal and post the output here. There should be a 10.0.0.x IP there, try pointing your browser to that.

---

### Post by Nitewalker on 2009-01-19
I should have been more clear, I meant to say that I can not reach my web site from the Internet when using my local machine, but I can get it with doing local IP address, sorry for not being more clear of my problem

---

### Post by TreeFinger on 2009-01-19
> **Nitewalker said:**
> I should have been more clear, I meant to say that I can not reach my web site from the Internet when using my local machine, but I can get it with doing local IP address, sorry for not being more clear of my problem

you need your router to foward requests to your webserver when incoming connections on port 80 arrive. (from both outside and inside the network)

---

### Post by Master_God on 2009-01-19
I don't think you can access your web server from the internet using a computer on the same LAN as the web server.

Try from a friend's computer or from your mobile and see if it works.

---

### Post by seagullplayer77 on 2009-01-19
> **TreeFinger said:**
> you need your router to foward requests to your webserver when incoming connections on port 80 arrive. (from both outside and inside the network)

Sounds right. If you're router isn't set to forward on port 80, then you won't be able to access your machine locally...not with a URL, anyway.

You oughta be able to login to your router (try 192.168.0.1 or 192.168.0.101 or routerlogin) and change the port forwarding settings pretty easily.

---

### Post by R.Bucky on 2009-01-20
You can also try using a proxy site such as [http://zerolike.com]("http://zerolike.com") to determine if your site is accessible from outside your network. Once you port forward on 80, restart apache using 
```
sudo /etc/init.d/apache2 force-reload
```

---

