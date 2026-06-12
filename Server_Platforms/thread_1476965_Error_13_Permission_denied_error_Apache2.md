---
title: "Error 13: Permission denied error Apache2"
date: 2010-05-08
forum: Server Platforms
---

### Post by Jarige on 2010-05-08
Hey guys,

So, I wanted to setup a local Apache2 server for some programming and testing. I installed and got Apache2 working with PHP, MySQL and all works fine.
Now I wanted to add an additional directory to somewhere in my /home. And that's where things went wrong.
I went to edit /etc/apache2/sites-available/default. This is it:
```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
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
	LogLevel debug

	CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

	Alias /po/ "/home/name/web"
    	<Directory "/home/name/web" >
		#Options Indexes MultiViews FollowSymLinks
		#AllowOverride None
		Order allow,deny
		Allow from all
        	#Allow from 127.0.0.0/255.0.0.0 ::1/128
    	</Directory>

</VirtualHost>

```
I can go to [http://localhost](http://localhost) and see the index.php I created there. But when i go to [http://localhost/po/](http://localhost/po/) it sais
```
You don't have permission to access /po/ on this server.
```
So I go to the logfile; which says this:
```
[Sat May 08 16:43:51 2010] [error] [client 127.0.0.1] (13)Permission denied: access to /po/ denied
```

And there I am. I tried a lot of stuff using chmod and chown, but all to no avail... I tried to change the ownership of the /home/name/web to root, and to www-data, I changed file permissions to allow executing the files. I changed a lot of stuff, but it didn't help at all.
And now I don't know what to do anymore.

Is there anyone that could help me doing this? What are the steps to do?

---

### Post by Jarige on 2010-05-09
BUMP 1 :)
Still looking for an answer on this, but this is my first time using Apache on Linux, so I don't know exactly where to look. Just using Google atm.

---

### Post by Bachstelze on 2010-05-09
You must also make sure www-data has read and search permission to /home/name, otherwise it won't be able to reach /home/name/web at all, regardless of what the permissions for it are.

---

### Post by Jarige on 2010-05-09
> You must also make sure www-data has read and search permission to /home/name, otherwise it won't be able to reach /home/name/web at all, regardless of what the permissions for it are.
I'm currently figuring out how to do that with chmod, but I can't really find the good command. Could you help me with that?

---

### Post by Jarige on 2010-05-09
Finally, I got it working.
I had to do this on every subdirectory until the php/html files except for /home:
sudo chmod +x mapname

```
[name@example name]$ ls -ld /home /home/name
/home/name/web
drwxr-x--x  111 root     root           4096 Mar 11 18:56 /home
drwxr-x--x   24 name     name           4096 Apr  9 10:19 /home/name
drwxr-x--x   32 name     name           8192 Apr  9 11:05 /home/name/web

```
This is how it eventually became (although I have more subdirectories with these permissions until the html files).

Thanks for the help, Bachstelze, you've made me more confident about whether I was on the right path.

I've found a push in the right direction here:
[http://defindit.com/readme_files/apache_13_error.html]("http://defindit.com/readme_files/apache_13_error.html")
But I couldn't find the commands to do so. Now I figured it out :)
Hope this might help others :)

---

### Post by dave2008713 on 2010-11-11
Thanks a lot ! It just solved my problem!

---

### Post by James78 on 2010-11-12
I don't know if anyone touched on this though, but here's a little tidbit. You can have /home/user1 owned by user1:user1, and still have apache read it without having any public read/write/execute permissions (face the fact, I don't want other users on my system to have even read access to my users home; where all my web stuff is. I like the permissions 0750 (-rwxr-x---))

Anyways, to give apache read access to your user with those permissions above, just do something like "sudo adduser www-data user1", which will add www-data to user1's group, thus giving www-data read only access, but no one else but you. I call it the safe permission configuration.

> **Jarige said:**
> I'm currently figuring out how to do that with chmod, but I can't really find the good command. Could you help me with that?
You can do that by giving public read only access to everything, but that's a bad idea in my opinion because who wants everyone to be able to read your personal stuff. Check above for, what I believe, is a much much better solution to the problem.

P.S. I see above that you solved your execution problem with public execute permissions, I believe you can just use what I've said at the top of my post, and give it 0750 (-rwxr-x---) permissions and still have it execute fine, using my method. It should be more secure doing it this way, that way everyone won't have permission to execute your files.

---

### Post by AlexNagy on 2011-10-16
Yes, I know this is an old thread, but I'm having the same issue and I don't want to move my directory.

> **James78 said:**
> I don't know if anyone touched on this though, but here's a little tidbit. You can have /home/user1 owned by user1:user1, and still have apache read it without having any public read/write/execute permissions (face the fact, I don't want other users on my system to have even read access to my users home; where all my web stuff is. I like the permissions 0750 (-rwxr-x---))

Anyways, to give apache read access to your user with those permissions above, just do something like "sudo adduser www-data user1", which will add www-data to user1's group, thus giving www-data read only access, but no one else but you. I call it the safe permission configuration.

I've tried
```
sudo adduser www-data user1
```
Substituting my name for user1, and still no go. I still get  a 403 Forbidden. I've even moved the old www director

from var I:
```
mv www www-bak; ln -s /home/user1/path/to/www/ www
```
Still with 403 Forbidden. 

Running Oneiric Ocelot. The path to www is served by an offsite backup service (not Ubuntu One) that isn't very flexible in whether or not the folders could be scattered.

---

### Post by Jarige on 2011-10-16
AlexNagy, are you sure that you've changed all the permissions in /home/user1/path/to/www recursively? You can do so by doing this:

```
sudo chmod 0750 -R /home/user1/path/to/www
```
The -R is the key here.

It helped me solve some problems before, it might just be the thing you overlooked :)

Anyways, if this doesn't help, could you give me the output of this:

```
ls -la /home/user1/path/to/www
```

I might be able to help (although you might have tried al the things I come up with already, I don't know what you've tried yet)

---

### Post by AlexNagy on 2011-10-21
> **Jarige said:**
> AlexNagy, are you sure that you've changed all the permissions in /home/user1/path/to/www recursively? You can do so by doing this:

```
sudo chmod 0750 -R /home/user1/path/to/www
```The -R is the key here.

It helped me solve some problems before, it might just be the thing you overlooked :)

Anyways, if this doesn't help, could you give me the output of this:

```
ls -la /home/user1/path/to/www
```I might be able to help (although you might have tried al the things I come up with already, I don't know what you've tried yet)

I've tried that but will do so again, I might not have executed the command correctly. Thanks! (:

---

### Post by AlexNagy on 2011-10-22
> **Jarige said:**
> AlexNagy, are you sure that you've changed all the permissions in /home/user1/path/to/www recursively? You can do so by doing this:

```
sudo chmod 0750 -R /home/user1/path/to/www
```The -R is the key here.

It helped me solve some problems before, it might just be the thing you overlooked :)

Anyways, if this doesn't help, could you give me the output of this:

```
ls -la /home/user1/path/to/www
```I might be able to help (although you might have tried al the things I come up with already, I don't know what you've tried yet)
```
root@localhost:/# chmod 750 -R /home/user1/path/to/www/
root@localhost:/# ls -la /home/user1/path/to/www/
total 52
drwxr-x--- 11 user1 user1  4096 2011-10-10 20:24 .
drwxr-xr-x  5 user1 user1 12288 2011-10-19 09:20 ..
drwxr-x---  5 user1 user1  4096 2011-10-02 16:29 bandages
drwxr-x---  2 user1 user1  4096 2011-10-02 16:30 cablegate
drwxr-x---  6 user1 user1  4096 2011-10-02 16:29 current
drwxr-x---  4 user1 user1  4096 2011-10-15 13:08 generic
drwxr-x---  6 user1 user1  4096 2011-10-10 20:24 joseph-a-nagy-jr.us
drwxr-x---  3 user1 user1  4096 2011-10-02 16:30 LegalTorrents Collections - Web Development Icons Superset
drwxr-x---  5 user1 user1  4096 2011-10-10 20:24 templates
drwxr-x---  4 user1 user1  4096 2011-10-02 16:29 testing
drwxr-x---  5 iser1 user1  4096 2011-10-15 22:11 underground-church
```Don't yell at me for being root. I've been using Linux since before there was an Ubuntu. q:

Here is my Apache conf (from 
```
/etc/apache2/sites-enabled
```):
```
<VirtualHost *:80>
        ServerAdmin my@email.com

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
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

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```From the error log:
```
[Sat Oct 22 09:13:31 2011] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www
[Sat Oct 22 09:13:31 2011] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www
[Sat Oct 22 09:13:31 2011] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www
[Sat Oct 22 09:14:39 2011] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www
[Sat Oct 22 09:14:40 2011] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www
```New error message, but as you can see, FollowSymLinks is turned on in the configuration.

---

