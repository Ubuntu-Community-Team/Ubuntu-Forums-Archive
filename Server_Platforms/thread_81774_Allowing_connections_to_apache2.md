---
title: "Allowing connections to apache2?"
date: 2005-10-25
forum: Server Platforms
---

### Post by hcker2000 on 2005-10-25
I did the basic server install and then installed apache2, webmin, sshd, and some apache modules.

For some reason when I try and connect to the http server from out side the network it never makes it there. I have varified that my routing and every thing is set up ok (I will dubble check if no one has any better ideas) but still no connection. Any one know what I might be doing wrong here?

PS: If any one knows a way to get webmin to work better with apache2 would be great.

---

### Post by adwait on 2005-10-25
If you are able to access the site from within your network, then the server is correctly setup. Theres probably a problem with your routing and port forwarding.

---

### Post by hcker2000 on 2005-10-26
Alright I think the issue may be with ipkungfu. Here is how I had it set up.

inet port 82 to 10.10.10.1 port 80 (my current working server)
inet port 85 to 10.10.10.35 to port 80 (my test server)

I think I may be runing into issues with the ipkungfu setup sence both are on port 80 inside the network.

---

### Post by Z3K3 on 2005-10-26
FYI: I posted this somewhere else but it may be helpful to this issue, or similar.

Ok,

The reason that this borks initially, where you can only browse to [http://localhost](http://localhost) but pages are not displayed when browsing to [http://you.isp.ip.address](http://you.isp.ip.address) is because apache2 is setup to listen to IPv6 by default, and since most people do not use IPv6 in home, they use IPv4 (ip.ip.ip.ip) it will not display the site.

The fix is even simpler than above.

edit your /etc/apache2/ports.conf

change from:
Listen 80
to
Listen 0.0.0.0:80

restart apache2

It will now listen for requests on IPv4, which will allow your page to work from outside the router.

FYI: I found this info here:

[http://lists.debian.org/debian-apach.../msg00029.html](http://lists.debian.org/debian-apach.../msg00029.html)

Looks like they are working on an upstream patch that will set it back to IPv4 by default.

Cheers

Z3K3

P.S

If you wish to see the difference on how apache is listening run this before and after the change above:

netstat -tupan | grep apache2

---

### Post by hcker2000 on 2005-10-27
That dosn't seem to fix any thing the web site is accessible at 10.10.10.35 but not at [http://ww1.hnetinc.com:85](http://ww1.hnetinc.com:85) (at least not from inside my network its not). From out side the network people can go to that url just fine. 

Some thing weird going on.

---

