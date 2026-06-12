---
title: "Squid is driving me crazy..."
date: 2007-12-17
forum: Server Platforms
---

### Post by nncognito on 2007-12-17
I'm trying to set up squid on ubunu 7.10 server edition.  I'm using a Dyndns address through a router to the server.  This setup works by using my dyndns address for the server and port 8080 as the proxy setting for firefox.  I have port 8080 forwarded from the router to my server. It works from both the local network and from outside my lan.

The problem is I can't get this to work through an SSH tunnel.  I have port 22 forwarded from the router to ssh on my server.  I use putty to login over ssh and create a tunnel from localhost:8080 to myserver:8080.  I can see the tunnel using netstat on both my XP client and on the ubuntu server.  Netstat on the server shows the remote address of the tunnel as the internal address of my router, is this normal?  Also, nmap on the server shows port 8080 as open.

I open my browser when configured for the ssh tunnel and I get no error messages.  The status display on the lower left will indicate it is looking for the site, then waiting on a response from the site, then will indicate done, however there is only a blank white page displayed.  It does not show page not found or proxy server not found or denying request.  Just a blank page with no error message.

/var/log/squid/access.log shows no entries when configured for a ssh tunnel so it does not seem to even be reaching squid.  Is something mis configured in squid or is something wrong with the ssh tunnel?  Help!!!

---

### Post by tgilber1 on 2007-12-21
Without the actual ssh command you're using, it's difficult to know what is wrong.  In any event, if you haven't already, you could try these two website for assistance.

[http://www.linuxhorizon.ro/ssh-tunnel.html](http://www.linuxhorizon.ro/ssh-tunnel.html)

[http://www.howtoforge.com/linux_secure_browsing_squid](http://www.howtoforge.com/linux_secure_browsing_squid)

---

