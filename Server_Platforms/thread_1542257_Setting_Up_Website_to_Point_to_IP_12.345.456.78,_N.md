---
title: "Setting Up Website to Point to IP 12.345.456.78, NOT personal.example.net"
date: 2010-07-30
forum: Server Platforms
---

### Post by domino1241 on 2010-07-30
Helllo All,

I installed Apache, PHP and MySQL and have made a simple personal website in /var/www.  I can access this site by going to 127.0.0.1 or [http://localhost/](http://localhost/).  I want to access the site using my personal ip that I get from whatismyip.com.  For example, at work I can just open Firefox and type [http://12.345.456.78/index.php](http://12.345.456.78/index.php) and have the site pop up.

Is there any way to do this, without registering mydomainname.com or using a site like no-ip.com?  Do you have a link with more information?  I'd greatly appreciate it.

I have searched endlessly on Google for this, but the keywords: website, ip, "without domain name", apache, "hosting from home" etc, all span such a wide array of topics I cannot isolate the solution to this problem myself.

Using Ubuntu 9.10 on an Eee PC with broadband connection.

Thanks.

---

### Post by stlsaint on 2010-07-30
You need to setup port forwarding on your router. If you do not have a router you may want to get one. ON the router you forward port 80 (or whatever port you apache listening on) to your personal ip address where the site is hosted. IE: 192.168.1.143.
Then you will be able to go to your public address in your browser and you will enter your site.

---

### Post by cdenley on 2010-07-30
> **stlsaint said:**
> Then you will be able to go to your public address in your browser and you will enter your site.

For many routers, you will not be able to access your server by the router's public IP from within your network, but it will work from outside your network.

---

### Post by domino1241 on 2010-07-30
stlsaint- I checked /etc/apache2/ports.conf and it says I am using port 80.  I forwarded "inbound port" 80 and "private port" 80 for my private ip (192.168.2.2) for TCP and UDP.  I chose this ip because it is the one my desktop is using, which is where the apache2 server is running.  I restarted the router, but I still get nothing when I go to [http://12.345.456.78/index.html](http://12.345.456.78/index.html)

cdenley- I SSH/VNCed to my school server and tried it from Firefox there, and still nothing (The connection has timed out.  The server at 12.345.456.78 is taking too long to respond.)

Any more suggestions?

---

### Post by cdenley on 2010-07-30
So apache works from within your LAN?
[http://192.168.2.2/](http://192.168.2.2/)

But it does not work when accessing your router from outside?
[http://12.345.456.78/](http://12.345.456.78/)

And you haven't configured any firewall rules to filter the traffic?
```

sudo iptables -n -L INPUT

```

And you have no other networking devices such as a hardware firewall which may be filtering traffic?

Either your router is not port forwarding to your server, or your ISP does not allow you to host a server on that port. You can try a different port.

---

### Post by domino1241 on 2010-07-30
cdenley- I don't have any other physical firewall besides the router, but I do have firestarter installed (I needed it way back when to get ssh to connect).  I set a policy to allow it to forward port 80 and now my website works, even from my home!  Thanks for your help.


For others with this problem, the solution was to open firestarter:
```
$ sudo firestarter
```

Switch to the tab that says "Policy."  There are two tables, one that says "Allow connections from host" and one that says "Allow service|Port|For".  Right-click in that second table in the white space below "Allow service" and click "Add Rule."

Name: HTTP
Port: 80
When the source is: Anyone
Comment: Web Hosting

Click "Add," press F4 to close Firestarter, and now it should work!

Note: Some websites suggested I open port 443.  This turns out to be unnecessary.  I use Firestarter 1.0.3 (check by typing $firestarter -v)

---

### Post by cdenley on 2010-07-30
> **domino1241 said:**
> I don't have any other physical firewall besides the router, but I do have firestarter installed (I needed it way back when to get ssh to connect).

Configuring a firewall to allow connections on a specific port is only necessary if you previously configured the firewall to deny connections on all ports. By default, nothing gets filtered. If you insist on using a firewall configuration interface to filter traffic, I recommend using one that is still maintained and supported, like GUFW. If you decide not to use firestarter or to use something else instead, make sure you purge firestarter.
```

sudo dpkg -P firestarter

```

---

