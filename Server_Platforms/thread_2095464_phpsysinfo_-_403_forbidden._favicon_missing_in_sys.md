---
title: "phpsysinfo - 403 forbidden. favicon missing in syslog."
date: 2012-12-16
forum: Server Platforms
---

### Post by Roasted on 2012-12-16
I have Ubuntu Server 12.04.1 running on my box, and I'm trying to utilize phpsysinfo on it. I've used phpsysinfo before, but it was on a totally different box. I get 403 forbidden when I try to access the site on my current box. The syslog has nothing relevant, but I did notce something about it.

```
[Sun Dec 16 23:22:22 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico

```

I talked to my buddy who's a web designer, who suggested the favicon insignificant in terms of the web site functioning.

I'm curious if anybody else has anything to offer, as I'm completely unsure why phpsysinfo is not working.

Thanks ahead of time!

---

### Post by lisati on 2012-12-17
The absence of a favicon file is unlikely to contribute to a 403 "Forbidden" message: the usual error code for "file not found" is 404.

A 403 error can be caused by a number of things, including settings in the website's .htacess file.

---

### Post by mladoux on 2012-12-17
Was there anything else in your /var/log/apache2/error.log? actually, considering that this is a 403 error, the issue is probably in your /var/log/apache2/access.log

---

### Post by Roasted on 2012-12-17
> **mladoux said:**
> Was there anything else in your /var/log/apache2/error.log? actually, considering that this is a 403 error, the issue is probably in your /var/log/apache2/access.log

Here's the entire log:

> 
jason@pluto:/var/log/apache2$ cat error.log
[Sun Dec 16 06:42:42 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.4 with Suhosin-Patch configured -- resuming normal operations
[Sun Dec 16 22:04:10 2012] [error] [client 192.168.1.5] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 22:04:12 2012] [error] [client 192.168.1.5] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 22:04:42 2012] [error] [client 192.168.1.5] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 22:04:43 2012] [error] [client 192.168.1.5] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 22:04:43 2012] [error] [client 192.168.1.5] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 22:04:44 2012] [error] [client 192.168.1.5] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 22:04:44 2012] [error] [client 192.168.1.5] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 22:04:45 2012] [error] [client 192.168.1.5] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 22:04:46 2012] [error] [client 192.168.1.5] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 22:04:46 2012] [error] [client 192.168.1.5] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 22:04:46 2012] [error] [client 192.168.1.5] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 22:04:46 2012] [error] [client 192.168.1.5] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 22:04:47 2012] [error] [client 192.168.1.5] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 22:04:47 2012] [error] [client 192.168.1.5] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 22:21:38 2012] [error] [client my.external.ip.here] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 22:21:39 2012] [error] [client my.external.ip.here] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 22:21:41 2012] [error] [client my.external.ip.here] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 22:21:42 2012] [error] [client my.external.ip.here] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 22:21:48 2012] [error] [client my.external.ip.here] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 22:22:38 2012] [error] [client my.external.ip.here] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 22:22:39 2012] [error] [client my.external.ip.here] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 22:24:14 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 22:24:14 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 22:39:58 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 22:39:58 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 22:39:59 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 22:39:59 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 22:39:59 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 22:39:59 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 22:39:59 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 22:39:59 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 22:54:40 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 22:54:40 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:06:01 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:06:02 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:07:55 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:07:56 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:08:07 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:08:07 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:08:24 2012] [notice] caught SIGTERM, shutting down
[Sun Dec 16 23:09:36 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.4 with Suhosin-Patch configured -- resuming normal operations
[Sun Dec 16 23:10:01 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:10:01 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:10:28 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:10:28 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:10:30 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:11:36 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:11:36 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:15:16 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:15:16 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:19:11 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:19:11 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:19:12 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:19:12 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:19:12 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:19:12 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:19:12 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:19:12 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:19:13 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:19:13 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:19:13 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:19:13 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:19:13 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:19:13 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:19:13 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:19:14 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:19:15 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:20:47 2012] [notice] caught SIGTERM, shutting down
[Sun Dec 16 23:20:48 2012] [notice] Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.4 with Suhosin-Patch configured -- resuming normal operations
[Sun Dec 16 23:20:53 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:20:53 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:20:54 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:20:54 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:21:54 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:21:54 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:22:17 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:22:17 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:22:18 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:22:18 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:22:18 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:22:18 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:22:19 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:22:19 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:22:19 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:22:19 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:22:19 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:22:19 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:22:19 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:22:20 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:22:20 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:22:20 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:22:20 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:22:21 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:22:21 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico
[Sun Dec 16 23:22:22 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo
[Sun Dec 16 23:22:22 2012] [error] [client 192.168.1.7] File does not exist: /media/storage/apache/favicon.ico



I'm a little unsure as to how it could be the .htpasswd file. I have several other web directories set up and all of them work fine with basic authentication. I don't remember having to do anything special with my last install to get phpsysinfo working, but it's been long enough since then I suppose anything is possible.

For what it's worth, here's the phpsysinfo section of /etc/apache2/sites-available/default in comparison to one entitled backup_logs, which works fine.

> 
        <Directory /media/storage/apache/phpsysinfo>
                Options Indexes FollowSymLinks MultiViews
                AuthUserFile /etc/apache2/.htpasswd
                AuthGroupfile /etc/apache2/.adminusers
                AuthName "Welcome To The Machine"
                AuthType Basic

                <Limit GET>
                require group adminusers
                </Limit>
        </Directory>


> 
	<Directory /media/storage/apache/backup_logs>
                Options Indexes FollowSymLinks MultiViews
                AuthUserFile /etc/apache2/.htpasswd
                AuthGroupFile /etc/apache2/.adminusers
                AuthName "Welcome To The Machine"
                AuthType Basic

                <Limit GET>
                require group adminusers
                </Limit>
        </Directory>


I also tried changing ownership on the phpsysinfo directory within its location at /media/storage/apache/phpsysinfo to me:me, but it changed nothing.

Not really sure what else to look at. Any hints?

EDIT - Using the awesome program known as Meld I was able to locate a capitalization error I had above, but even when I corrected that and restarted apache, nothing changed. Still getting 403 Forbidden...

---

### Post by Wim Sturkenboom on 2012-12-17
This line in your error log stands out
```

[Sun Dec 16 22:24:14 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo

```

'favico' is no issue; browser try to get one to display in the address bar.

PS
next time please use code tags instead of quote tags ;)

---

### Post by Roasted on 2012-12-17
> **Wim Sturkenboom said:**
> This line in your error log stands out
```

[Sun Dec 16 22:24:14 2012] [error] [client 192.168.1.7] client denied by server configuration: /usr/share/phpsysinfo

```

'favico' is no issue; browser try to get one to display in the address bar.

PS
next time please use code tags instead of quote tags ;)

I specifically use quote tags because it eliminates the whole scrolling thing, which I find obnoxious when you're trying to dissect logs. 

I ended up stumbling across a new link located [here]("http://ubuntuserverguide.com/2012/06/monitoring-system-resources-on-ubuntu-server-with-phpsysinfo.html") which mentions a "script" to run, which is basically just inputting several lines of text in the config. The example they show (and they even specified this) clearly shows that the config will only allow 192.168.56.2 to access it, however I wanted mine to have basic password protected access, so I altered mine accordingly.

The alterations to the "script" for my particular setup I ran was this:

> 
cat > /etc/apache2/conf.d/phpsysinfo.conf <<-EOF
Alias /phpsysinfo /usr/share/phpsysinfo
<Location /phpsysinfo>
Options None
AuthUserFile /etc/apache2/.htpasswd
AuthGroupFile /etc/apache2/.adminusers
AuthName "Welcome To The Machine"
Authtype Basic
<Limit GET>
require group adminusers
</Limit>
</Location>
EOF


This was nice because then I can tie in my existing Apache config (adminusers, etc) to it.

Once I got to this point I was getting 404'd instead of 403'd, so instead of having forbidden access, I just flat out didn't have any access since it was saying nothing was there. The error log (/var/log/apache2/error.log) was saying files in /usr/share/phpsysinfo didn't exist. Oddly enough, despite the fact phpsysinfo was installed, I ran apt-get install phpsysinfo again. This time it came back with 1 newly installed. Sure enough, /usr/share/phpsysinfo existed and F5'ing Chrome brought up phpsysinfo.

Anyway, we're good! :guitar: Thanks to everybody who helped.

---

