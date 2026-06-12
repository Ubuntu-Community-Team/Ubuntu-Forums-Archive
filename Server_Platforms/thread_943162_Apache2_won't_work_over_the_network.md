---
title: "Apache2 won't work over the network"
date: 2008-10-09
forum: Server Platforms
---

### Post by SteinbergerNate on 2008-10-09
Alright, I've been struggling with this all afternoon and have read several tutorials/howtos to get it working. 

I've gotten Apache2 installed and done some minimal configuration. I can see my (very basic) index.html from a browser on the server but when I try to get to it from a computer on the same network, it will timeout.

Basically, all the configuration I've done is copy the default site config file to one of my own and changed the root folder to one in my home directory. All other configuration should be default to the install.

I haven't tried to access it from over the internet. I'm taking it one step at a time and don't want to worry about routing until I know that the server is working properly.

---

### Post by lykwydchykyn on 2008-10-09
Are you running a firewall on the server, and if so is port 80 open?
Can you post your site config?
What is the output of:
```

sudo netstat -tunap |grep apache
apache2ctl status

```

---

### Post by SteinbergerNate on 2008-10-10
here's my configuration in /etc/apache2/sites-available:
```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /home/bassmannate/public_html
	#DocumentRoot /home/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/bassmannate/public_html/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```

The output of sudo netstat -tunap |grep apache:
```
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      30039/apache2 
```

And the output for apache2ctl status:
```
Apache Server Status for localhost

Server Version: Apache/2.2.8 (Ubuntu)
Server Built: Jun 25 2008 13:54:13

&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;

Current Time: Friday, 10-Oct-2008 07:15:17 CDT
Restart Time: Thursday, 09-Oct-2008 22:06:08 CDT
Parent Server Generation: 0
Server uptime: 9 hours 9 minutes 8 seconds
1 requests currently being processed, 5 idle workers

_W____..........................................................
................................................................
................................................................
................................................................

Scoreboard Key:
"_" Waiting for Connection, "S" Starting up, "R" Reading Request,
"W" Sending Reply, "K" Keepalive (read), "D" DNS Lookup,
"C" Closing connection, "L" Logging, "G" Gracefully finishing,
"I" Idle cleanup of worker, "." Open slot with no current process

```

As far as I know, there should be no firewall running. I was running one and then I had problems with it blocking another application so I turned it off. That application still works so it should still be off.

---

### Post by lykwydchykyn on 2008-10-10
If you have a second Linux box of any kind, install nmap and run a port scan.  Nmap might be available for Windows too, not sure.  As far as the output shows, your apache is in good working order.  Something is blocking it either at the firewall level, or at the client.

the command would be:
```

nmap ip_of_my_server

```

---

### Post by SteinbergerNate on 2008-10-10
Ok. I'll try that if I can find it for Windows (at the moment, I don't have another linux box I can use) 

Could it be anything at the router? I'm running dd-wrt firmware v.24.

---

### Post by lykwydchykyn on 2008-10-10
Typically a router is only going to filter traffic between the LAN and the WAN (ie. the Internet), not between hosts on the LAN; but I haven't had the pleasure of using dd-wrt so I don't know what it's capable of.

---

### Post by SteinbergerNate on 2008-10-10
Yeah, that's what I thought. dd-wrt is a pretty powerful firmware. Adds a lot of features you just don't find on consumer level routers.

I also ran nmap on the windows machine. gave me this the first time I ran it:
```
Starting Nmap 4.76 ( http://nmap.org ) at 2008-10-10 11:15 Central Daylight Time
Note: Host seems down. If it s really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 0.40 seconds
```

So then I ran it with -PN and it took longer and gave me this:
```
Starting Nmap 4.76 ( http://nmap.org ) at 2008-10-10 11:15 Central Daylight Time
All 1000 scanned ports on bassmannate-laptop (192.168.#.#) are filtered
MAC address: ##:##:##:##:##:## (Sony)
Nmap done: 1 IP address (1 host up) scanned in 39.92 seconds
```

---

### Post by lykwydchykyn on 2008-10-10
Well, clearly you have some kind of firewall running, because something is blocking both ICMP (ping) traffic and filtering your ports.

try this:
```

sudo iptables -L

```

That will list all active firewall rules.

---

### Post by SteinbergerNate on 2008-10-10
well crap, you were right. I do have iptables up and running. Disabled it just to see if anything works and it works perfectly well.

Thanks for sitting through my stupidity. I really coulda' swore that I had disabled it at some point.

---

