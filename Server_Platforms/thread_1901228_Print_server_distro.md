---
title: "Print server distro"
date: 2011-12-28
forum: Server Platforms
---

### Post by JeremySchubert on 2011-12-28
I would like to connect my  canon inkjet and  brother laser fax to a headless pc that would serve the printer to Mac, windows and Ubuntu  clients. Is there some distro (is  the right term?) that I  can just load on to a computer to act as a print server. Something like ipcop that leads you through the configuration process once and hopefully don't touch again?

---

### Post by 2F4U on 2011-12-28
Almost any Linux distribution can do that, you just need to configure CUPS and maybe Samba appropriately. Since you don't want to touch it, I would suggest you look for something with a long release cycle, for example Ubuntu Server LTS release.

---

### Post by collisionystm on 2011-12-28
yep, as mentioned, just install ubuntu 10.04 LTS server

install cups

edit your /etc/cups/cupsd.conf to allow remote access from your network

you will then be able to visit the ip of the server to manage your printers through a web interface

if your server is 192.168.1.50

you would go to 192.168.1.50:631 and have a nice gui to work in.

---

