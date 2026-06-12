---
title: "Installing a printer for sharing via shell"
date: 2008-02-12
forum: Server Platforms
---

### Post by vitiate34 on 2008-02-12
Hello,

I've taken some what of a plunge into the Linux world, I'm an advanced computer user and on and off have been using Linux at a basic level for the last 3 years now. I've recently decided to convert my home server to a Ubuntu 7.10 server installation, forcing me into the world of the shell and thusly forcing me to learn more about Linux the way I had orginally intended.

I finally have it up and running with Samba, and now I'm trying to share a printer via samba. The problems I am faced with are:

1) installing the printer
2) configuring the printer
(all via shell)

How can I go about this? I can't find an article on the net, but then again, I don't know enough to narrow my search.

Printer is an old Epson Stylus color 740 and works fine with linux after configuring it through a gui.

Cheers!

---

### Post by crush304 on 2008-02-12
i don't know how to do it through the shell but have you looked into using cups

you can access it through a web interface @ [https://YourComputer:631](https://YourComputer:631)  you probably need to enable remote connections it been a while but i think you can do that in /etc/cups/cupsd.conf

---

### Post by crush304 on 2008-02-12
if you really want to get nuts you can probably edit the config file manually, start with 'man printers.conf' you'll probably also need a ppd file, but I've never done the setup that way, I always use the web interface

---

### Post by vitiate34 on 2008-02-13
Thanks for the info! I edited the CUPS config file to allow remote administration via a browser and approached it that way. All works fine now!

---

