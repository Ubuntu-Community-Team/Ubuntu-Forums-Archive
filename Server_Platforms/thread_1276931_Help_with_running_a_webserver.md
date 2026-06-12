---
title: "Help with running a webserver"
date: 2009-09-27
forum: Server Platforms
---

### Post by SilverShadow118 on 2009-09-27
Hello, 

I've got two computers behind a router that's connected to a modem. When someone connects to my web server via port 80, does that mean that my other computer behind the router won't be able to to communicate through that port? How exactly does that work? 

 Also, I've been toying with the idea of adding a hardware firewall ( [http://www.instructables.com/id/Build-your-own-gateway-firewall/](http://www.instructables.com/id/Build-your-own-gateway-firewall/) ) between my modem and router. Does anyone have any ideas/suggestions for this? Any help is appreciated, thank you.

- Mason

---

### Post by nandemonai on 2009-09-27
Essentially you'll need a port forward from your router to your webserver. Any incoming requests to your external IP address (ISP assigned) will be redirected to the internal machine hosting sites (port 80 for example).

This counts for INCOMMING connections only. This wont affect any outgoing communications from your Internal LAN.

---

### Post by volkswagner on 2009-09-27
Your remaining machines will still be able to perform normal tasks via the web, as they did prior to port 80 forwarded to your server.

---

### Post by SilverShadow118 on 2009-09-27
Also, can HTTP communicate over other ports other than 80? or does each port represent only one protocol and that's that?

---

### Post by nandemonai on 2009-09-27
You can, in theory, use any port you like as long as it's not in use by another service.

The only issue with changing port on a webserver is that by default browsers try port 80.

For example:

Normal port 80 assignment:

[http://mywebsite/](http://mywebsite/)

Say you changed it to 81? Users would then have to input the address for your site like so:

[http://mywebsite:81/](http://mywebsite:81/)

---

### Post by Bachstelze on 2009-09-27
80 is the standard port for HTTP, so it's the port used if you don't specify one, but you can very well specify an alternate port, for example

[http://google.com:8080](http://google.com:8080) would connect to Google on port 8080.

---

### Post by SilverShadow118 on 2009-09-28
Thank you for your help, everyone :)

---

