---
title: "Can someone explain this . . ."
date: 2010-07-19
forum: Server Platforms
---

### Post by garfonzo on 2010-07-19
I have been looking into a transparent proxy system for my home LAN using Squid and I often see this statement:

*"Finally, as far as transparently proxing HTTPS (e.g. secure web pages using SSL, TSL, etc.), you can't do it. "* [(Source- section 2.3)]("http://tldp.org/HOWTO/TransparentProxy-2.html#ss2.3")

Then, on another website tutorial I find this:

*"Squid is a caching proxy for the Web supporting HTTP, HTTPS, FTP, and more.* [(Source)]("http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html")


So, I am a little confused. My main concern is, if I am to set up a transparent proxy for caching a logging, will I still be able to do online banking? I believe the banks use HTTPS for security. From the above two statements, I'm not sure if any HTTPS sites will work, or if all of them will work. 

Can someone shed some light on this for me? 

Thanks!

---

### Post by cdenley on 2010-07-19
I'm not very familiar with squid, but for SSL connections established with a remote server, a thirdy party (you or your proxy) cannot decrypt the HTTP requests or responses. This would completely defeat the purpose of encryption. So squid cannot cache content it cannot see.

I don't know if squid can do this, but a proxy can inject its own SSL certificate for the connection between the users and the proxy, then establish a new SSL tunnel with the destination web server to proxy requests through. Of course this should result in the user's browser giving very nasty warnings about the proxy's SSL certificate being used for another server.

---

