---
title: "Ubunutu Web Server, on Ubuntu Desktop"
date: 2009-11-11
forum: Server Platforms
---

### Post by AgentZ86 on 2009-11-11
Hi all

I'm wanting to install Ubuntu Web Server / Email Server to replace my existing Server OS
I won't be using it as a desktop, but only when installing packages maybe, but probably will install things via ssh as root anyhow but just FYI

Considering Ubuntu Desktop with Ubuntu Server ontop.

This way I can use synaptic gui to install packages, because I don't really like the command prompt much.

Anyhow, what recommendations you have for the LAMP install and Cpanel or Webmin etc.

And can all this be done from synaptic ? Or does it have to be done via Console ?

Separate Question:
I see the server Cloud and Enterprise Cloud ? That seem to have a Gui, but is that on Amazon EC2 or is that for download and install on my own server ? I don't understand this topic ?

Please advise
Thanks

---

### Post by Jekshadow on 2009-11-11
1) Install Ubuntu Desktop Edition (however you want), or if you want a GUI on a server that already has Ubuntu Server installed, run this to install the standard Ubuntu Desktop:
```
sudo apt-get install ubuntu-desktop
```

2) Run this command to install Apache 2, PHP 5, Apache's PHP Library and MySQL Server.
```

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server
```

3) Configure however you want

---

### Post by AgentZ86 on 2009-11-13
> **Jekshadow said:**
> 1) Install Ubuntu Desktop Edition (however you want), or if you want a GUI on a server that already has Ubuntu Server installed, run this to install the standard Ubuntu Desktop:
```
sudo apt-get install ubuntu-desktop
```

2) Run this command to install Apache 2, PHP 5, Apache's PHP Library and MySQL Server.
```

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server
```

3) Configure however you want

Thanks for the help.

Sorry for the multi question here

Does it matter if I install the desktop first and then all the server stuff second, or should I install the server and then the desktop ON top of it ? Or does it make NO difference at all ?

And what about cpanel or perhaps webmin and things like that ?

Can I host multiple website for a few freinds and family who already have their own domains ?

Can this all be installed from the synaptic gui ?

I just don't want to get too much deeper into the command prompt if I can avoid it ?

All advise is greatly appreciated, thanks

---

### Post by JonRohan on 2009-11-13
Thanks for the help.

Sorry for the multi question here

Does it matter if I install the desktop first and then all the server stuff second, or should I install the server and then the desktop ON top of it ? Or does it make NO difference at all ?

**It makes no difference. **

And what about cpanel or perhaps webmin and things like that ?

**Again you can put these onto a desktop although it is not recommended. I don't think cpanel support debian though (you'll have to check) **

Can I host multiple website for a few freinds and family who already have their own domains ?

**Sure if you want to. :D**

Can this all be installed from the synaptic gui ?

**Yep. **

I just don't want to get too much deeper into the command prompt if I can avoid it ?

**Why not. ;) :p. **

All advise is greatly appreciated, thanks

---

