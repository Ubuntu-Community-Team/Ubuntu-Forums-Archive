---
title: "Port forwarding from apache to tomcat"
date: 2012-07-11
forum: Server Platforms
---

### Post by Nixforce on 2012-07-11
Im setting up a server for my hosting. I have apache installed and tomcat, as need the tomcat for my OpenBD CFML engine. I have the OpenBD running on port 8080.

What i need to do now and .cfm requests through to the port 8080 to run. I read somewhere about port forwarding or something that would pass any request in my apache through to the OpenBD.

Is this possible? and how would i start?

Thanks

---

### Post by volkswagner on 2012-07-11
You can setup apache2 as a reverse proxy.

Here are [some steps]("http://ubuntuforums.org/showthread.php?t=1920715") to get you started.

You will want to modify the proxy and proxy_pass lines to include your full url including port 8080.  If both servers are on the same machine/ip you can use localhost in the url.

---

