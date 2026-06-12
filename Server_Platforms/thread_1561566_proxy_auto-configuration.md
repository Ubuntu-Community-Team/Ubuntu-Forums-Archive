---
title: "proxy auto-configuration"
date: 2010-08-26
forum: Server Platforms
---

### Post by slick666 on 2010-08-26
Dear Community,

What I'm trying to do seems pretty straight forward but I can't seem to find any documentation on this searching the "internets" but I think I'm getting mixed in with all the other proxy documentation.

What I'm trying to do is basically replicate the proxy settings from a desktop machine to a server machine. I have Ubuntu 10.04 Desktop running fine on a corporate network using the Automatic Proxy Configuration option and supplying the appropriate URL that I pulled for a corporate issued windows machine. I would like to do this on Ubuntu server 10.04 as well.

What I've got so far is coping out the proxy information from the .pac file and setting the http proxy value directly but I want to follow the URL so that the system follows any changes that come down the road.

Does anyone know how to integrate a .pac (Proxy auto-config) url into ubuntu server?

---

### Post by Vishal Agarwal on 2010-08-27
[http://helpdeskgeek.com/networking/proxy-pac-file/](http://helpdeskgeek.com/networking/proxy-pac-file/)

---

### Post by slick666 on 2010-08-27
That link explains how PAC files work but it does not get me closer to my solution. Under Gnome in Ubuntu desktop network manager I think it the program that handles setting system proxy settings via a pac file. I'm looking to what could do this in a server environment.

---

### Post by slick666 on 2010-08-30
After looking around it looks like the network manager app is handling the interpretation of the url configuration. I guess I'm looking for an application (network manager) that will do this but from the command line only.

---

