---
title: "Ubuntu Server 8.04 as a second webserver"
date: 2008-04-26
forum: Server Platforms
---

### Post by smadahar on 2008-04-26
I have a webserver already running which I can access from the outside world on port 80, and it is running just fine. 

I have now created a 8.04 server, with all the services running. It is connected to the same network as the webserver, and internally the 8.04's apache installation is working, as you can get to it's index.html without a problem. 

I would like to make the 8.04 server into a Moodle server, but have run into problems accessing it from the outside world. I have tried port forwarding via the router, but apart from this am a little bit stuck. 

Does anyone have advice on how to run two separate webservers on the same network, with both being accessible from the outside world?

thanks

---

### Post by adamos on 2008-04-26
bind dns is your friend :) I dont know much what you want to do.

---

### Post by gekkio on 2008-04-26
You have basically two options:
[LIST=1]
[*]Use mod_proxy on the not-8.04-webserver (if you are using Apache) to forward some requests to your 8.04-webserver
[*]Forward some port (not 80 because it is already in use!) from your router to the 8.04-webserver
[/LIST]
Both webservers can be running on port 80, because with mod_proxy it doesn't really matter and if you forward ports, the external port can differ from the internal port.

Examples:
**1. Mod_proxy**
Fist you need to have mod_proxy installed. Then you can simply do something like this on the not-8.04:
```

Proxy /moodle http://hardywebserver:80/moodle

```
Now when you go to url *[http://nothardywebserver/moodle](http://nothardywebserver/moodle)* you'll see the stuff you have on the hardy web server. This also works from the outside world (going to *[http://myexternalip/moodle](http://myexternalip/moodle)* works)

**2. Port forwarding**
You'll have to use a different port (from the outside world perspective), because you cannot forward one port to two servers.
I assume you have a port forwarding like this:
External port: 80
->Internal IP: nothardywebserver
->Internal Port: 80

You'll want to forward another port, something like this:
External port: 8080
->Internal IP: hardywebserver
->Internal Port: 80
Thus, from the internal network you can access your stuff from *[http://hardywebserver/moodle](http://hardywebserver/moodle)*, and from the outside world you'll need to use *[http://myexternalip:8080/moodle](http://myexternalip:8080/moodle)*

Hope this helps. :)

---

### Post by smadahar on 2008-05-02
Thanks Gekkio, 

I had actually tried port forwarding to my Ubuntu server, but I get no results. Today, in desperation I simply forwarded port 8181 to my own office computer, which has a webserver installed. It worked! 

So to summarise, I can get a normal OS X client machine to be available on port 8181 from the outside world and inside my LAN, but I can't get the Ubuntu Webserver to accessible. 

Apache2 must be working, because I can access the Ubuntu server within the LAN, simply by typing it's internal IP address into any web broswer on any computer on my LAN. When I type in [http://address:8181](http://address:8181) I get a time out. 

Any ideas? This one really has be stumped!

---

### Post by smadahar on 2008-05-13
Ok, I've tried Port Forwarding, and even installed Ubuntu Desktop to check whether Ubuntu Server had security that was blocking outside attempts at reaching the webserver. 

I have port forwarding on my Router that points port 80 requests to the main website, and port 8181 is pointing to the Ubuntu Webserver. Again, internally all is working with the Ubuntu Webserver, but from the outside world, I get timeouts. 

To remind you, if I point the router to my office Mac using port 8181, from the outside world all I can see it's web pages. 

Is there a default setting on Ubuntu Server and Desktop that blocks all webpage requests from the outside by default?

---

### Post by RWells on 2008-05-13
Just throwing out Ideas, have you set apache to listen on 8181?

Rusty

---

### Post by gekkio on 2008-05-14
I've got another idea...

Check whether your web server is listening on both ipv4 and ipv6 ports. I had a similar problem (access from LAN worked, from the outside it didn't) before and I noticed that my web server only listened on the computer's ipv6 address. Disabling ipv6 (so that the webserver switched to listening on the ipv4 address) worked.

Run on your web server
```
netstat -ant
```
and make sure you have both tcp and tcp6 lines like this:
```
tcp        0      0 0.0.0.0:myport             0.0.0.0:*               LISTEN
tcp6       0      0 :::myport                  :::*                    LISTEN

```
or at least the tcp one. If you only have the tcp6 line, you could try disabling ipv6.

AFAIK there is no firewall by default on Ubuntu Server boxes, so this problem simply cannot happen because of that. I'm guessing this ipv6 issue is what causes your problems.

---

### Post by opus on 2008-05-14
Here are my thoughts:

[LIST=1]
[*]Make sure your router is routing inbound port 8181 to your hardy server on port 80.
[*]Make sure your hardy box is listening on port 80.
[*]Make sure you aren't trying to access your hardy box using the external address from inside your network.  That doesn't usually work very well.
[/LIST]

---

