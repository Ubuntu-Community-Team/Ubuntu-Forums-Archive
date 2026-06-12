---
title: "Apache (?) is not accepting connections from outside"
date: 2005-06-29
forum: Server Platforms
---

### Post by adl on 2005-06-29
Hello.

I've been trying to get my http server running with Kubuntu, but it seems that Apache won't accept connections outside my LAN. Apache is listening port 80, my ip is set to 192.168.0.100 and my router is forwarding port 80 to that ip.

Almost all my configure files are at their defaults. I don't have a firewall installed either, but I'm not sure if this is an Apache problem or not.

Everything worked fine with Fedora, but I disliked the distro so I changed to Kubuntu..

"netstat -na | grep tcp" gives
```

tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN     
tcp        0      0 192.168.0.100:32774     217.75.98.138:6667      ESTABLISHED
tcp6       0      0 :::80                   :::*                    LISTEN     
tcp6       0      0 ::1:25                  :::*                    LISTEN
```

Any solutions?

---

### Post by lorenzo on 2005-06-29
Have you tried to edit:

/etc/apache2/sites-available/default

NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		#allow from all
                Allow from 127.0.0.0/255.0.0.0 ::1/128
                #Deny from all


and to change allow from....

Maybe it works.

Ciao,
Lorenzo

---

### Post by LordHunter317 on 2005-06-29
If a different machine on your LAN can access the box, then the issue isn't with your server, but with the port forwarding on your router.

---

### Post by adl on 2005-06-29
It makes no difference.. Tried many allow from settings, but it just doesn't work.

Perhaps this hasn't anything to do with Apache? Are there any (Ubuntu) settings I could change?

[QUOTE=LordHunter317]If a different machine on your LAN can access the box, then the issue isn't with your server, but with the port forwarding on your router.[/QUOTE]

I'll make a double-check then.. But it worked fine yesterday.. :(

---

### Post by adl on 2005-06-29
Hmm.. Strange, there really was a problem with my router. I reset my settings and rebooted the router. Must have been a glitch or something.  I shouldn't really trust 50-buck-routers..

Well thanks for the replies :)

Case solved.

---

