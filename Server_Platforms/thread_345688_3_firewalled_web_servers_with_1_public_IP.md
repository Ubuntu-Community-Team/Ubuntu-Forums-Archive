---
title: "3 firewalled web servers with 1 public IP?"
date: 2007-01-24
forum: Server Platforms
---

### Post by kenquad on 2007-01-24
Hi all:

I have 3 security appliances which can act as web servers for remote monitoring.  My goal is to place an Ubuntu box in between these servers and the wild as a firewall.  In addition, I would like to know if there's any way to run all three simultaneously on only one public IP address for simplicity and economy.  Naturally, I mean a FOSS way...  Thanks in advance for any assistance you can give.

Ken Quad

---

### Post by jtc on 2007-01-24
If you want to run three webservers on one public IP...

The easy, but perhaps not convenient, way is to simply run them on diffrent ports. Otherwise you can always run a webproxy as frontend and have it forward the connection to to one of the three webservers, running as backends, depending on some suitable rules.

---

### Post by kenquad on 2007-01-24
Thanks.  Do you have a recommendation for a good, well-documented web proxy?

---

### Post by jtc on 2007-01-24
I guess you could always take a look at Apaches [mod_proxy]("http://httpd.apache.org/docs/2.0/mod/mod_proxy.html")

I haven't tried it myself, but as a general rule I kind of trust Apache.

---

### Post by MJN on 2007-01-25
I'd go for the multiple ports option, if only to keep everything nice and simple.
 
Mathew

---

### Post by kenquad on 2007-01-25
So, on the multiple ports option, could I have three domains, each mapped to a different port?  And would the mapping take place in the router or the firewall system?

---

### Post by jtc on 2007-01-25
> **kenquad said:**
> So, on the multiple ports option, could I have three domains, each mapped to a different port?

Actually, that is more like the proxy-solution. If you don't use some kind of
proxy/frontend you'll have to specify the diffrent ports in the address you give.

[http://this.server.domain:8080/](http://this.server.domain:8080/)
[http://another.service.domain:7654](http://another.service.domain:7654)
etc, etc

---

### Post by MJN on 2007-01-25
Indeed, although you could just have:
 
_[COLOR=#0000ff][http://this.server.domain:8080](http://this.server.domain:8080)[/COLOR]_
[_[COLOR=#0000ff]http://this.server.domain:7654[/COLOR]_]("http://this.server.domain:7654")
 
That is, same domain (which maps to the same IP obviously), but different ports.
 
It depends on your requirements really, particularly as far as aesthetics and accessibility are concerned (e.g. some find port numbers unsightly, other don't have a clue what they are and hence would not find working with them intuitive).
 
What are these 'applicances'? Cameras? I'm just asking in case it might have a bearing on what would be the 'best' solutin.
 
Mathew

---

### Post by kenquad on 2007-01-25
Yes, these are video-related appliances.  Sounds like the port solution is it, since counter-intuitivity is not an issue.  Now I just have to figure out how to map that into the domain provider.  Thanks for the help, people.

---

### Post by MJN on 2007-01-25
Ports are quite abstract from DNS hence all you need to worry about is getting an A record for your domain pointing to your IP address. You'll then need to ensure all the required ports are forwarded from your router to the correct internal IP addresses. You could even keep your devices running on their standard port (likely 80) if your router supports port translation.

Mathew

---

### Post by kenquad on 2007-01-26
Er, what's an A record?

---

### Post by MJN on 2007-01-26
It means 'Address' - it's the *type* of record in DNS that maps a name to an IP address.
 
Do a search on DNS as there's plenty of info about it - you'll soon find A records are the bricks and mortar of it.
 
Mathew

---

### Post by kenquad on 2007-01-26
I'll have to research it in Safari.  They have some really in-depth info :-)

---

### Post by Brazen on 2007-01-26
Using Apache to set up a reverse proxy is going to be the simplest and easiest solution.  There are two possibilities for doing it this way:

1.  You use a single dns name (ie. [www.myserver.com](www.myserver.com)) and access the 3 webservers under subfolders (ie. [http://www.myserver.com/server1](http://www.myserver.com/server1), [http://www.myserver.com/server2](http://www.myserver.com/server2), [http://www.myserver.com/server3)](http://www.myserver.com/server3)).

or 2.  You have multiple dns names all pointing to the same IP.  The Apache reverse proxy will know, based on the dns name used, which server to send the request to (ie. [www.myserver1.com](www.myserver1.com), [www.myserver2.com](www.myserver2.com), and [www.myserver3.com)](www.myserver3.com)).

If you pick one, I can give you some direction on how to set it up.  Both methods are equally simple and easy, just install apache and then add a few lines to the config file.  Also, even if you use subfolders, because of the way proxying works, the webservers will act just like they are running in the root of the website.

---

### Post by kenquad on 2007-01-29
Brazen:

Just saw your reply.  Simple and easy are my cup of tea :) Reverse proxy with Apache sounds good, and I think in my application subfolders are going to be the best arrangement on that side.  How do I go about it?

Ken Quad

---

### Post by Brazen on 2007-01-30
Do this on the proxy server:

1.  Install Ubunut Dapper Server

2.  Install Apache ```
sudo apt-get -y install apache2
```

3.  Add these lines to the virtual host section of /etc/apache2/sites-available/default (I like to use nano for this)```
ProxyPass /app1 http://ip.of.srvr.1
ProxyPassReverse /app1 http://ip.of.srvr.1

ProxyPass /app2 http://ip.of.srvr.2
ProxyPassReverse /app2 http://ip.of.srvr.2

ProxyPass /app3 http://ip.of.srvr.3
ProxyPassReverse /app3 http://ip.of.srvr.3
```

4.  Reload the Apache daemon ```
sudo /etc/init.d/apache2 reload
```

That should be it.  You can now browse to the proxy server and add the /app# subdirectories to get to the other servers.  If you need more info, just let me know.

---

### Post by kenquad on 2007-01-30
Wow, thanks for the detailed instructions!  Now if I wanted to firewall this connection as well, do you think that should be on the proxy server or a separate box for best security?  Also, can I implement additional authentication through Apache?  (an unbreakable password to supplement the firewall!)

---

### Post by Brazen on 2007-01-30
> **kenquad said:**
> ...can I implement additional authentication through Apache?  (an unbreakable password to supplement the firewall!)
[http://httpd.apache.org/docs/2.0/howto/auth.html](http://httpd.apache.org/docs/2.0/howto/auth.html)
This is not something I've had a need for yet, but it should not be difficult.

> Wow, thanks for the detailed instructions! Now if I wanted to firewall this connection as well, do you think that should be on the proxy server or a separate box for best security?
I would have a seperate box for a firewall.  But, don't you already have a firewall/router appliance?  Your internet connection must come through some router, unless every computer on your network has public IPs.  Your firewall would typically be a part of your router.  Without knowing more about your setup, it's hard to give a precise answer.  But typically your firewall/router would be a seperate appliance and appliances like this proxy would be in the DMZ, and your servers would be in the LAN, completely firewalled off from the internet.

If you really want to get paranoid, you could also configure local firewalls on the three servers and allow port 80 access ONLY from the proxy server.  That would make sure a misconfiguration somewhere doesn't open up your servers to the outside world.  There are two practical ways I see for setting up firewalls: 1) the method I use is to install Webmin and edit iptables directly, or 2) install Shorewall and use it to edit iptables.

---

### Post by kenquad on 2007-01-30
Brazen:

Thanks for, again, elucidating the matter in such detail.  This is the same installation on which you're helping me in [this thread]("http://ubuntuforums.org/showthread.php?t=349035&page=1").  So it looks like, overall, I need to put a firewall/VPN box directly behind the router (I don't want to use the router's built-in firewall because it's a very cheap [read free] router :))  and then add an Apache server in the DMZ to direct Port 80 requests to the appropriate server ("subfolder") on the LAN.  Do you see any holes in that?

Kenquad

---

