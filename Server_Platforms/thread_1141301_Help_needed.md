---
title: "Help needed"
date: 2009-04-28
forum: Server Platforms
---

### Post by pastorblue on 2009-04-28
We have a small network, one server, previously running Windows 2003 and XP Pro on the desktops. The desktops logged into the network (user name and password) and accessed internet by DHCP plus home folders etc on the server.
The desktops now have Ubuntu 9.04 on, the server has been replaced and 8.04 has gone on nicely (9.04 server would not recognise the internet connection, although apparently detected the network card OK).
I have downloaded Webmin.
How do I get the desktops to log in to the server? Do I need NIS on the server?

I am about as ignorant as I can be at this point.

Graham

---

### Post by HermanAB on 2009-04-28
Howdy,

If you have only a handful of desktop clients, then you can manually ensure that the usernames, passwords, UIDs and GIDs are the same on the clients and the servers and then you don't need NIS.

If you have more than about ten client machines, then that quickly becomes tedious and NIS is called for.

For sharing files on the server, use NFS, but first get the UIDs and GIDs fixed as above before trying to use NFS else you'll just waste your time.

---

