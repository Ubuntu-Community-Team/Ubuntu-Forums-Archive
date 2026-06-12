---
title: "Firefox Sync Server"
date: 2012-03-22
forum: Server Platforms
---

### Post by maverickaddicted on 2012-03-22
Hi,

I have one server which is used for internal development purpose. Now, I want to create a password server for firefox, which will store all the passwords for websites, all the clients machine will be able to fill the password of sites using auto fill. There will be no need to give them new passwords everytime I change the password.

Clients machines are Windows XP, Seven, Vista and Ubuntu 11.10.

---

### Post by lovinglinux on 2012-03-22
Tell all the clients to install [LastPass]("https://lastpass.com/") extension (available for Firefox, Chrome, Opera, Safari and IE | Win | Mac | Linux)

Create an account at [LastPass]("https://lastpass.com/") and share the login details with clients.

You can even use it to share notes with the clients.

---

### Post by maverickaddicted on 2012-03-22
> **lovinglinux said:**
> Tell all the clients to install [LastPass]("https://lastpass.com/") extension (available for Firefox, Chrome, Opera, Safari and IE | Win | Mac | Linux)

Create an account at [LastPass]("https://lastpass.com/") and share the login details with clients.

You can even use it to share notes with the clients.

Thanks for your reply, I am using last pass only, but I don't want my user to see the passwords. Is there any other solutions? Like creating custom firefox sync server.

---

### Post by Groodles on 2012-03-22
I dont think that using Firefox Sync will do what you want.

If I understand you correctly, you want to sync website passwords across multiple firefox browser installation/user accounts.  However, you also dont want the users to know the sync'd passwords?

Firefox Sync will certainly sync passwords across multiple browser installations, but it wont hide the data from the users.  If they want, they can still go into Firefox's options and view the saved password data.  Sync also works the same way on ALL clients, so ANY user will be able to add/delete/change any of the passwords stored in the Firefox Sync profile.

Using a personal sync server, just means that you will store your saved data on a private machine instead of using the free account space provided by Mozilla.

---

### Post by maverickaddicted on 2012-03-22
> **Groodles said:**
> I dont think that using Firefox Sync will do what you want.

If I understand you correctly, you want to sync website passwords across multiple firefox browser installation/user accounts.  However, you also dont want the users to know the sync'd passwords?

Firefox Sync will certainly sync passwords across multiple browser installations, but it wont hide the data from the users.  If they want, they can still go into Firefox's options and view the saved password data.  Sync also works the same way on ALL clients, so ANY user will be able to add/delete/change any of the passwords stored in the Firefox Sync profile.

Using a personal sync server, just means that you will store your saved data on a private machine instead of using the free account space provided by Mozilla.

I have figured a way to disable Show password button in firefox.The reason for doing this is that I have one server and I want to use it for this purpose. Another reason is boss.

---

### Post by lovinglinux on 2012-03-22
> **maverickaddicted said:**
> I have figured a way to disable Show password button in firefox.The reason for doing this is that I have one server and I want to use it for this purpose. Another reason is boss.

It would be easy to bypass such restriction.

---

### Post by maverickaddicted on 2012-03-26
> **lovinglinux said:**
> It would be easy to bypass such restriction.

Is there any way I can do it without using third party software, because the password which I am going to store in it is very important and I cannot trust other software.

---

### Post by lovinglinux on 2012-03-26
Perhaps you could add [Public Fox](https://addons.mozilla.org/en-US/firefox/addon/3911/) extension to prevent users from enabling the show password button. However, if the user really wants to see the passwords, he could simply copy *singons.sqlite* and *key3b.db* to a different profile.

I am not an expert on this, but perhaps you should think about a different method of authenticating users on your server. I am sure there are other methods, better suited for you scenario other than passwords, that you could implement.

---

### Post by maverickaddicted on 2012-03-28
Ok, I tried to create my own sync server, using this guide

[http://docs.services.mozilla.com/howtos/run-sync.html](http://docs.services.mozilla.com/howtos/run-sync.html)

However, it is giving me this error. I am using Running behind a webserver option with Apache + mod_wsgi

```

nexusadmin@backup:/var/www$ sudo service apache2 restart
apache2: bad group name sync
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!

```

This is the configuration file

```

nexusadmin@backup:/var/www$ cat /etc/apache2/sites-available/firefoxsync
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	ServerName backup.firefox.local
	DocumentRoot /var/www/server-full
	WSGIProcessGroup sync
	WSGIDaemonProcess sync user=sync group=sync processes=2 threads=25
  	WSGIPassAuthorization On
  	WSGIScriptAlias / /var/www/server-full/sync.wsgi
  	CustomLog /var/log/apache2/example.com-access.log combined
  	ErrorLog  /var/log/apache2/example.com-error.log
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/server-full/>
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

```

---

### Post by maverickaddicted on 2012-03-29
Any idea?

---

### Post by DeweyRiley on 2012-03-29
> WSGIDaemonProcess sync user=sync group=sync processes=2 threads=25 

When telling apache to start processes, then the group and user mentioned should exist :-)

---

### Post by maverickaddicted on 2012-04-04
> **DeweyRiley said:**
> When telling apache to start processes, then the group and user mentioned should exist :-)

Thank You Very much, I should have seen it carefully.

---

### Post by maverickaddicted on 2012-04-04
Can anyone have good guide for firefox custom sync server? Apart from this - [http://docs.services.mozilla.com/howtos/run-sync.html](http://docs.services.mozilla.com/howtos/run-sync.html)

I desperately need to set sync server.

---

### Post by maverickaddicted on 2012-04-05
Has anyone tried to set firefox custom sync server?

---

### Post by maverickaddicted on 2012-04-10
?

---

