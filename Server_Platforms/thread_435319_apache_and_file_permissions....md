---
title: "apache and file permissions...?"
date: 2007-05-06
forum: Server Platforms
---

### Post by tiger.woods on 2007-05-06
So, I think I have a file permissions issue with my server and with my virtual serving.

In my /sites-available/ I have my virtual hosted file that has the directory 'DocumentRoot' pointing to /home/mysite as opposed to /var/www. When 'DocumentRoot' was /var/www/mysite I was able to pull up the site but now I'm not, I'm assuming it's a permissions issue.

I believe this is a standard practice for hosting sites by using  /home/sitename so I'm curious what is needed to fix my problem.

Thanks.

TW,

---

### Post by bikeboy on 2007-05-06
I think the above is spam :(

Anyway...It might help if you post your /etc/apache/httpd.conf or whichever particular one you are using. The ubuntu pastebin should make it easy to: read [http://paste.ubuntu-nl.org/](http://paste.ubuntu-nl.org/)

Also, what are the permission on /home/mysite/ ? It needs to be readable by users other than yourself and your group.
```
ls -la /home/mysite/
```

---

### Post by tiger.woods on 2007-05-06
ls -la

drwxr-xr-x 3 ftpuser ftpgroup  4096 2007-05-06 20:01 .
drwxr-xr-x 6 root    root      4096 2007-04-28 15:03 ..
-rw-r--r-- 1 ftpuser ftpgroup  9642 2007-05-06 18:11 aboutus.htm
-rw-r--r-- 1 root    root     32876 2007-05-06 20:01 access.log
drwxr-xr-x 2 ftpuser ftpgroup  8192 2007-05-06 19:59 images
-rw-r--r-- 1 ftpuser ftpgroup 11026 2007-05-06 18:11 index.htm


My /etc/apache/httpd.conf  is all commented outso it basically has nothing in it... I didn't think that httpd.conf was used any longer?

TW,

---

### Post by bikeboy on 2007-05-06
Could be apache2.conf...I'm still using Apache1.3 which has httpd.conf.

Looks like your permissions are ok, are you sure apache is listening for connections at the moment?
```
netstat -l | grep tcp
```

Should list localhost:80 or something like that.

---

### Post by tiger.woods on 2007-05-06
hmmm... I don't see port :80 listed.

tcp        0      0 *:nfs                   *:*                     LISTEN
tcp        0      0 *:874                   *:*                     LISTEN
tcp        0      0 localhost:mysql         *:*                     LISTEN
tcp        0      0 *:5900                  *:*                     LISTEN
tcp        0      0 *:sunrpc                *:*                     LISTEN
tcp        0      0 *:www                   *:*                     LISTEN
tcp        0      0 *:10005                 *:*                     LISTEN
tcp        0      0 *:ftp                   *:*                     LISTEN
tcp        0      0 192.168.5.99:domain    *:*                     LISTEN
tcp        0      0 dns1.mydomain.c:domain *:*                     LISTEN
tcp        0      0 localhost:domain        *:*                     LISTEN
tcp        0      0 *:ssh                   *:*                     LISTEN
tcp        0      0 *:49976                 *:*                     LISTEN
tcp        0      0 localhost:953           *:*                     LISTEN
tcp        0      0 *:762                   *:*                     LISTEN


I'm able to view the web site via the internal lan but not the external. I can see activity at the router  trying to access the site but I get nothing.

TW,

---

### Post by bikeboy on 2007-05-06
That actually looks ok, the entry "www" is actually the port 80. Since you can't access from external, maybe it's port forwarding??? You would need port 80 to be forwarded to the LAN IP of your server.

edit: port forwarding in the router that is :)

---

### Post by tiger.woods on 2007-05-06
Yep, just doubled checked and the port is being forwarded.

I'm thinking it's somehow related to the directory's where the files reside... since I was able to see the site when it was in /var/www but since it's moved to /home/mysite I'm no longer able to see the site.

---

### Post by bikeboy on 2007-05-06
Hmm I'm running out of ideas, it seems as though the permissions for the folder itself are ok. Which means it must be something with the config file, but it could still be related to the folder as you say. I'm not an apache expert so hopefully someone else is able to offer some more suggestions.

---

### Post by dmizer on 2007-05-06
please post the contents of /etc/apache2/sites-available/default

---

### Post by gombadi on 2007-05-07
To check if apache is having trouble serving files then have a look at the log files.

For apache2 they are in /var/log/apache2

Any problems will be in error.log

---

### Post by tiger.woods on 2007-05-07
[B][I]NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www
        DirectoryIndex index.html index.cgi index.pl index.php index.xhtml
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# Uncomment this directive is you want to see apache2's
		# default start page (in /apache2-default) when you go to /
		#RedirectMatch ^/$ /apache2-default/
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
[/I][/B]

I don't see anything in the logs, Mostly it's all phpmyadmin stuff and since I'm behind a router all traffic is coming in on 192.168.*.*

Thanks,

---

### Post by dmizer on 2007-05-07
i am assuming you just have one site, and you want to host it in /home/mysite instead of /var/www

if that IS indeed the case, simply replace the above with the following:
```
NameVirtualHost *
<VirtualHost *>
ServerAdmin webmaster@localhost

DocumentRoot /home/mysite
DirectoryIndex index.html index.cgi index.pl index.php index.xhtml
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /home/mysite>
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
# Uncomment this directive is you want to see apache2's
# default start page (in /apache2-default) when you go to /
#RedirectMatch ^/$ /apache2-default/
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

restart your apache server:
```
sudo /etc/init.d/apache2 restart
```

---

### Post by tiger.woods on 2007-05-07
Currently I only have the single site but am planning on a few more. How will that impact the config file?

Would I simply just change the path if all the websites were to be below the /home directory, /home/site1, /home/site2, /home/site3, etc.?

DocumentRoot /home
DirectoryIndex index.html index.cgi index.pl index.php index.xhtml
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /home>

---

### Post by dmizer on 2007-05-07
no ... you'll have to make a new script to handle the second page.

have a good read up on it here: [http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2](http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2)

but i suggest to not use the script provided there as i couldn't get it to work.  i just copied the default script and modified it.

---

### Post by tiger.woods on 2007-05-07
Since I'm using sites-enabled, etc. and the site was reachable from the internal network it looks too me that the only piece I might be missing is with regard to /etc/hosts.

127.0.0.1 localhost.localdomain localhost dev.example.com [www.dev.example.com](www.dev.example.com)

I'm not currently running a DNS server on this end so I guess that might make some sense... godaddy only points to the server IP then apache should use the host header to determine the intended recipient, correct?

I'll give it a try tonight.

Does my logic make sense?

TW,

---

### Post by dmizer on 2007-05-07
no ... the hosts line restricts your url to your local host only.  if you want your address to be reached from the net, [www.dev.example.com](www.dev.example.com) should NOT be listed in /etc/hosts.

---

### Post by tiger.woods on 2007-05-07
So barring modifying the /etc/hosts and modifying the default site to use /home instead of /var/www any other suggestions, neither worked...

TW,

[EDIT]

I think I found the issue, although Firestarter the firewall was showing that the ports were open and correctly forwarded when I shutdown the firewall I was able to connect both internal y and externaly. 

The apache default file was irrelevant of what directory it was pointed at whether it was /var/www or /home it reallycounts in the sites-enabled virtualhost file for the site. 

Thanks for the help and suggestions.

---

### Post by dmizer on 2007-05-07
yes ... what really counts is the sites-enabled ... but the files in sites-enabled are merely symbolic links to the files in sites-available.  so by editing /etc/apache2/sites-available/default ... you are ALSO editing /etc/apache2/sites-enabled/000-default

glad to see you got it working though.

---

### Post by tiger.woods on 2007-05-08
At what point would I reach the default site? If there weren't any sites in the sites-available would that be the only way to get there?

Thanks,

---

### Post by sinaen on 2007-05-08
im trying to install torrentflux but it's little tricky. i think i restricted php-issues to not be read. 
because when i follow the link to where i have the torrentflux files. (via the link on my original homepage) it lists the contents of the php file.... not loading it

EDIT:
i would have wanted to configure my two different network cards. in my server. to one go to the outside. and the other only to the inside of my network. but how do i do that. i have to unplug the second network cable cause with the network cable and network card on i cant access anything

EDIT: or only to setup a virtual host to.. separate of my homepage

---

### Post by dmizer on 2007-05-08
> **tiger.woods said:**
> At what point would I reach the default site? If there weren't any sites in the sites-available would that be the only way to get there?

Thanks,

/etc/apache2/sites-available/default is your default script for apache.  but apache does not look in /etc/apache2/sites-available.  so if there is nothing in /etc/apache2/sites-enabled, apache can't know where to look for your home page, and you'll get an error trying to start apache.

so, to use two domains, make a second script in /sites-available/ and call it whatever you like, but something you can recognize.  then, to make your script live, you run the command:
```
sudo a2ensite script-file-name
```
this creates the symbolic link between sites-available and sites-enabled, which allows apache to make use of the script.

now ... if there is already a symbolic link in place between /sites-available/ and /sites-enabled/ then edit the file in /sites-available/ because this is the location of the ACTUAL script, and changes made to /sites-available/ will appear in /sites-enabled/.  as an asside, you may have to restart apache in order to make the changes active.

@sinaen
your problem does not seem related to this thread.  you're better off posting your own thread or posting in a more related thread.

---

### Post by saphil on 2007-05-14
I had a similar issue once, and it was solved by moving the site back to var, my issue was attempting to set up a log parser in /home/mine/...  Linux will not let you make your home folder wide open to all, and in a sense, web sites have to be wide open to all.  Anyway.  We solved it by moving the application into var/...

I am having a similar issue of 403 error on a web folder that is on a different partition and slinked to /var/www

---

