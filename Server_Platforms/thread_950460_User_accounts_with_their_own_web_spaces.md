---
title: "User accounts with their own web spaces"
date: 2008-10-17
forum: Server Platforms
---

### Post by Nigelkennington on 2008-10-17
Hi all,

I've managed to get an Ubuntu server up and going, apache et al all seems happy, webmin installed and accessible and everything there seems all good thanks to some of the excellent (and legion)howto / tutorial websites available.

However, I've now hit a wall. With webmin, I seem able to create new users just fine, but what I want is to be able to have each user have their own webspace with a subdomain or even just a [www.server.net/~username](www.server.net/~username) style address, either is fine. Although the many "set up your own web server" tutorials are excellent, they all seem to assume that there will be only the person setting up the server actually using it to develop on.

Is there a tutorial available or is it so obvious I just can't see it?

Sorry, Ubuntu is still a bit of a mystery to me...

---

### Post by ianhaycox on 2008-10-17
Running

```
sudo a2enmod userdir

```
will enable the module for [www.server.net/~username](www.server.net/~username) style addresses.

Or if you prefer you can manually create a link in /etc/apache2/mods-enabled/ to /etc/apache2/mods-available/ for the module you wish to enable.

e.g.

sudo ln -s /etc/apache2/mods-available/userdir.conf /etc/apache2/mods-enabled/userdir.conf 
sudo ln -s /etc/apache2/mods-available/userdir.load /etc/apache2/mods-enabled/userdir.load 

Restart Apache afterwards.

---

### Post by Nigelkennington on 2008-10-22
Thanks Ian.

---

