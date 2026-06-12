---
title: "Advises for advanced reverse proxy config."
date: 2012-07-02
forum: Server Platforms
---

### Post by trikolon on 2012-07-02
Hi,
I need some help how to realize the following setup:
First some words what I want. I have a server, which is in my LAN and provides different webserver and stuff, like my wiki, ampache or subsonic for music streaming, gateone, transmission, etc. 
So this means there a running a lot of different services on different ports. I want every connection to the bad bad internet gets ssl encrypted and a reverse proxy, so I can seperate these services by url and not by url and port.

First I have a Firewall-System which shall do the https to http translation for connections from internet to LAN.
Next I need a reverse proxy for just a single url by a service.
I tested pound and nginx as reverse proxy, but I can't get amapche and gateone working. ampache does not have any pictures, just text and I can't login. gateone is not starting at all. I guess that this apps need a websocket connection but I am absolutely not sure. 

So what setup could do this for me? stunnel and haproxy? nginx with websockets (socket.io)? 

Thanks for any advise.

Ben

---

