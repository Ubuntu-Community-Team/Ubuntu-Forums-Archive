---
title: "install ubuntu 6.06 desktop than ubuntu 606 server"
date: 2006-08-06
forum: Server Platforms
---

### Post by xaviero on 2006-08-06
could i install ubuntu 6.06 desktop first than i add some package from ubuntu 6.06 server ??

so, i can use X for server configuration, coz of using vim to edit server is more confusing me :(

is that can working well ???

---

### Post by az on 2006-08-06
sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

The desktop packages do not interfere with the LAMP server packages and vice versa.  It's just not best security practices to run a GUI on a production server.

You can also just install the LAMP server packages using the Server cd and then

sudo apt-get install ubuntu-deskop linux-386 
(you need the desktop kernel for some desktop hardware like some mice)

Or enable the universe repository and install a more simple GUI

sudo apt-get install x-window-system-core xterm icewm menu

pick a filemanager and whatever else you want to add to that...

---

### Post by xaviero on 2006-08-07
thanks 4 your reply...

actually i need the server application just for proxy and firewall.
other such like php i don't need it. 

is there other way that i don't need apt-get ? coz i want install it offline. :D

---

