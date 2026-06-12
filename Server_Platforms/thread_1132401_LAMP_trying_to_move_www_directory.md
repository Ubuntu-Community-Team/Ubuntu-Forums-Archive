---
title: "LAMP trying to move www directory"
date: 2009-04-21
forum: Server Platforms
---

### Post by lenamtl on 2009-04-21
Hi,

I follow a few tutorial 

I have install LAMP local web server that was working ok.

I have install PHPMyadmin (+link)

I have change Mysql folder location to home/mysql
and this was ok too

Now what I want to do is to change var/www to home/www

here what I did
```

I have created a folder www in home location
sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/mysite 
gksudo gedit /etc/apache2/sites-available/mysite
I have replace var/www for home/www
sudo a2dissite default && sudo a2ensite mysite
sudo ln -s /home/www /var/www
echo "ServerName localhost" | sudo tee /etc/apache2/conf.d/fqdn
sudo /etc/init.d/apache2 restart


```

When reloading Apache I got this error in comand line
Restarting web server ache2                                                Syntax error on line 4 of /etc/apache2/sites-enabled/mysite:
Invalid command 'DocumentRoot/home/www/', perhaps misspelled or defined by a module not included in the server configuration

Browsing for localhost = Failed to Connect

I'm new to Ubuntu I guess I did something wrong... or forgot to do something...

I don't remember the code line to give access to a folder (create-copy-paste etc)

Thanks for your help!

---

### Post by R.Bucky on 2009-04-21
It sounds like you want to move your web directory. Visit /etc/apache2/sites-available/default and change the directives for your home folder, similar to what is below. Or, am I misinterpreting your intent?

```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin user@localhost 
	
	DocumentRoot /home/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride All
	</Directory>
	<Directory /home/www/>
		Options -Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>
```

---

### Post by BkkBonanza on 2009-04-22
This error,
Invalid command 'DocumentRoot/home/www/',
Is telling you that you have typed the command wrong. It needs a space after the word Root like,

DocumentRoot /home/www/

Also as poster above mentioned - you are better off moving your web content under /home/www and changing the referring command lines rather than just adding a symlink like you did. Using the symlink doesn't make any sense unless you need to have it available via both directories.

---

### Post by niqmk on 2009-04-22
```

<VirtualHost *Your IP*>
[INDENT]DocumentRoot /home/*userhome*/websites[/INDENT]
</VirtualHost>

```

Make sure your directory exist

---

### Post by lenamtl on 2009-04-22
ok it is more clear now.

but I still need some help to complete:

-how can I remove this symlink?

-also there is a link for PHPMyAdmin 
that is in var/www how can I move this to the new home/www? 

-how can I give rights to the home/www folder to be able to use it?

Thanks!

---

### Post by BkkBonanza on 2009-04-22
You can remove the symlink with,

sudo rm /var/www

The rm command won't remove directories or recurse down but it will remove files and symlinks. 

You can change permissions/ownership with the chmod and chown commands. You should read a bit first by typing,

man chmod
man chown

There are different ways of setting up web content permissions but the way I usually do it is to run apache as user www and set the web content as owned by me but readable by group www. I'm sure others have variants on this.

one way, (user "me" is just for example - I use my actual username there)
set apache to run as user/group "www" in apache conf.
set your www directories as chown me:www and chmod 750
set actual content as chown me:www and chmod 640
you'll find sometimes a few files need different permissions if they need to be written to by a script or something.

This allows me to have admin control over the web content but apache to get read access. PHP usually takes on apache user when it runs under apache as a mod.

Using chown and chmod will require sudo as well, eg.
sudo chmod 750 /home/www

---

### Post by lenamtl on 2009-04-22
BkkBonaza you where right about the missing space thanks

the sudo rm /var/www gave me an error 
rm: cannot remove `/var/www': Is a directory

The chmod is working ok thanks.

Everything is working now the switch is done.

Thanks a lot :P

---

### Post by BkkBonanza on 2009-04-23
Hmmm. Must have it backwards then. To remove symlink try the other way,
sudo rm /home/www
I wasn't sure which way your symlink was pointing but I knew it wouldn't remove the real directory so was safe to do. Anyway, if it's working then good, the symlink is superfluous and could be left or removed.

---

