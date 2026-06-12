---
title: "Ubuntu 6.06 LTS"
date: 2007-09-06
forum: Server Platforms
---

### Post by Emm AAy on 2007-09-06
Hello 

i insalled Ubuntu 6.06 LTS at home for learning purpose and found very difficult because it start with CLI.
My questions are
1-Is above mentioned OS is completely a CLI or there is a way for working as GUI so that i can see features it provide to be used as a server?
2-how many type of roles it can be used like print server, web server, DHCP, DNS....e.t.c. or can i used with combination of these role without affecting its performance.

hopefully someone will reply as soon as possible.

Thanks 

Emm Aay

---

### Post by jediborger on 2007-09-06
Well the only reason that would have only a CLI system is because you have the server edition. If you want the default ubuntu desktop just run the following command. It'll take a while to download everything, but after it's done you'll have the normal Ubuntu desktop which is probably what you wanted.
```
sudo apt-get install ubuntu-desktop
```

If you don't want the entire desktop and just need a simple gui the run the following command:
```
sudo apt-get install icewm gdm xorg
```

---

### Post by Emm AAy on 2007-09-06
this mean that server edition is totally a CLI based edition, what type of roles can we make a ubuntu server

---

### Post by tgalati4 on 2007-09-06
Depending on your load, you can have the server running several hundred processes.  I routinely have 150 processes running on my server--mail, printing, mp3 serving, web serving, etc.  Server usage is typically low unless you have it deployed inside a business with several users.

For business use, the trend is to have separate servers for each  major function, so that you can take down one server at a time for maintenance.

---

### Post by ruibernardo on 2007-09-06
1- If you have another computer, you could try [webmin]("http://www.webmin.com/"). It allows you to manage your server from another computer on a normal web browser. It's more efficient than installing Gnome or any Desktop environment in an old/server computer, and it gives a "graphical" idea of what you can do in Ubuntu Server.

2- You can do all that with Ubuntu Server, starting with 160 MB of RAM without any performance problem.

---

### Post by NewbieNik on 2007-09-06
Ubuntu, at its core is a shell-based operating system as is all GNU/Linux distro&#347; (and old windows versions and the new longhorn server)
The server edition is the same as the desktop version, but without all the add-ons (Desktop, Mail clients, Open Office, etc, etc) installed. This makes it a stabler system to start with and a little faster as there is less to load.
You can add a GUI desktop such as Gnome or KED or IceWM or a multitude of others. As a newcomer to Ubuntu, this would be highly recommended and I would stick to Gnome or KDE as there is a wealth of support available for these.
As for roles for the system, here is a few (And there are many more, trust me)
Domain controller, Web-server, LDAP server, email server, remote access server, firewall, database server, file server, DNS server, cluster server, Spam and virus filter, print server ,etc,etc etc, etc, etc and on and on.
Or just as a desktop for everyday use.....The choice is yours and the possabilities are nearly limitless...welcome to the beauty of GNU/Linux.

---

