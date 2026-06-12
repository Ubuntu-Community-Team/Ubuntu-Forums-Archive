---
title: "Accessing Apache Virtual Host Behind Router"
date: 2010-03-16
forum: Server Platforms
---

### Post by rsteffens on 2010-03-16
I am serving 3 web sites via my own in-home ubuntu server. I've got a static public facing IP, and am serving the sites via virtual hosting.  When accessing the virtual host sites outside my LAN, everything works perfectly.  When accessing the domain names of the sites within the LAN, I get my router's configuration page.  I can get around this by using the local ip address of the server inside my LAN, (rather then the domain names of the sites, or the public facing IP), but then I only get the default virtual host, and can't access either of my other two sites.  How can I access all my virtual host sites within my LAN?

Thanks!
Randy

---

### Post by cdenley on 2010-03-16
You can either change the way the router responds to requests on its WAN address from inside the LAN (probably not possible) or have the hostnames for your vhosts resolve to a LAN address within your LAN. For the latter, you can either configure a DNS server for your network, or edit the /etc/hosts file on each client computer.

---

### Post by rsteffens on 2010-03-16
Thanks for this helpful info.  My router doesn't have the functionality to change the way it responds to WAN requests from inside the LAN.  So I have a couple questions:

Can a DNS server for my local network be run on the same computer that's serving my web-sites?  Can you recommend any particular DNS server software?

Changing the /etc/hosts file may be the easiest method -- can you point me to a site where the steps I would need to follow are documented in detail?

Thanks so much.

Randy

---

### Post by cdenley on 2010-03-16
A DNS server would be a difficult route. You would not only have to install and configure bind, but ensure that all clients get configured to use that DNS server.
[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

Configuring the hosts file would be much simpler if you don't have many clients. Simply edit the file /etc/hosts, and add an entry like
```

192.168.0.x vhost1.com www.vhost1.com vhost2.com www.vhost2.com

```
In Windows, the file will be at:
%WINDIR%\system32\drivers\etc\hosts

You will have to edit the file on every client that needs to access a vhost within your LAN.

---

### Post by rsteffens on 2010-03-16
It works!!  I searched far and wide trying to figure out how to do this, but all to no avail.  I SO much appreciate your help.  

Thanks again,
Randy

---

### Post by mindy777 on 2010-05-02
cdenley, 
Thanks a lot for your reply mate. I've been searching for answer for while and now finally found.

---

