---
title: "Connection &quot;Open&quot; but cannot connect with hostname"
date: 2008-07-31
forum: Server Platforms
---

### Post by Xpyd3r on 2008-07-31
Okay, I can connect to my server with [https://(Internal](https://(Internal) IP), and I have DDClient installed on it, and I'm forwarding port 81 to the server from the router, and I made a hosting service with DynDns.org that forwards my hostname to the external IP,  It looks as though everything should work, but it doesn't.  It says cannot establish a connection to the server, and says, though the site seems valid, the browser was unable to establish a connection.  Any Ideas?

---

### Post by cdenley on 2008-07-31
How are you trying to connect?
[http://user.dyndns.org](http://user.dyndns.org)
[https://user.dyndns.org](https://user.dyndns.org)
[http://user.dyndns.org:81](http://user.dyndns.org:81)
[https://user.dyndns.org:81](https://user.dyndns.org:81)
[http://[WAN](http://[WAN) IP]
[https://[WAN](https://[WAN) IP]
[http://[WAN](http://[WAN) IP]:81
[https://[WAN](https://[WAN) IP]:81

What is the output on your server for...
```

cat /etc/apache2/ports.conf
grep VirtualHost /etc/apache2/sites-enabled/*

```

If you post your domain name and/or WAN IP, it might be easier to help.

---

### Post by Xpyd3r on 2008-07-31
anything that is outside the network won't give me anything.  External IP (currently is 96.253.215.126) and Dyn don't give me anything (XpyPro.dnsdojo.com), but I can connect with the local Ip (192.168.1.37).  When I do [http://[LAN](http://[LAN) IP], it fails to connect, when I do [https://[LAN](https://[LAN) IP] I get my sample page, when I do [http://[LAN](http://[LAN) IP]:81, it says bad request, and when I do [https://[LAN](https://[LAN) IP]:81, it says security connection failed.  

as far as the outputs go
> root@XpyServer1:~# cat /etc/apache2/ports.conf
Listen 81
Listen 82
Listen 443

and then
> root@XpyServer1:~# grep VirtualHost /etc/apache2/sites-enabled/*
#NameVirtualHost *
<VirtualHost *>
</VirtualHost>


---

### Post by cdenley on 2008-08-01
You're running an SSL site on port 81. Is that what you wanted? If you connect to [https://XpyPro.dnsdojo.com/](https://XpyPro.dnsdojo.com/), the browser will attempt to connect using port 443, which you have apparently also configured in your router. [https://XpyPro.dnsdojo.com:81/](https://XpyPro.dnsdojo.com:81/) works fine for me as well. Of course, since you're using a self-signed SSL certificate, you get the usual warning.

Did you want to create a seperate vhost without SSL? It looks like you don't have any vhosts configured for port 81 or 443. Did you put your vhost configuration in a different file, like apache2.conf or httpd.conf?

---

### Post by Xpyd3r on 2008-08-01
Well, this is my first time playing around with everything to this extent, but https is what I was aiming for, although I suppose there is no reason I need it.  But you can connect to [https://XpyPro.dnsdojo.com?](https://XpyPro.dnsdojo.com?)  Because my main problem was the fact that I cannot access that, but if you can externally I don't know why I couldn't internally?  And I don't understand what you mean by my vhost configuration?  And lastly I would like to have a vhost without SSL, but how would I go about doing that?

---

### Post by cdenley on 2008-08-01
[https://XpyPro.dnsdojo.com/](https://XpyPro.dnsdojo.com/) works fine for me. If it doesn't work for you internally, maybe your router won't "port forward" connections to itself from the LAN (I think it's called "local loopback"). It's always best to test your routing externally (or through a proxy).

If you're trying to setup a regular http site, the default /etc/apache2/sites-available/default should work. Are you trying to use port 81 instead of port 80, though? It's a little difficult to walk you through it since you seem to have added site (vhost) configurations in a non-standard way. 

If you start from scratch, edit /etc/apache2/sites-available/default as necessary. To change the port number to 81
```

NameVirtualHost *:**81**
<VirtualHost *:**81**>

```

Then, to enable SSL, copy the default vhost/site configuration...
```

sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/ssl

```
change the ports to 443, enable SSL, edit /etc/apache2/ports.conf if necessary, enable the SSL vhost/site and restart...
```

sudo a2ensite ssl
sudo /etc/init.d/apache2 restart

```

---

