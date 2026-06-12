---
title: "Add users in Apache,,"
date: 2008-08-25
forum: Server Platforms
---

### Post by IndieJr1 on 2008-08-25
Hi. First off all, iam very new too Unix =)

I installed a Ubuntu server on an old computer.
I want to use it as a Http/php server, and it seems to work allrigth. 

I use a SSH connection from my laptop to the server.
Here is the problem:
I would very much like my friend too be able to use this server as a web server aswell. 

I gave him a user and he can connect to the server just fine, 
but how can i give him a personal dir so he can manage his homepage from his /home dir ? ( something like this [http://..../](http://..../) ~myfriend ) 

Indie :)

---

### Post by de0xyrib0se on 2008-08-25
Easy, create a symlink in the apache root folder /var/www or whatever it is called in your case, to his homedir http folder. Then it would be accessible via http://<server ip>/linkname/

Syntax: ln -s <target> <linkname>

Where <target> is /home/yourfriendsname/mainhttpfolder, and <linkname> is /var/www/linkname or whatever Apache root folder you have.

---

### Post by mbeach on 2008-08-25
or enable the user module and restart (not sure if a reload will pick up a new module):
```

sudo a2enmod userdir
sudo /etc/init.d/apache2 restart

```

then by default he can use the /home/username/public_html folder.  See /etc/apache2/mods-available/userdir.conf if you need to change the 'public_html' to something else.

reference:
[http://httpd.apache.org/docs/2.0/mod/mod_userdir.html](http://httpd.apache.org/docs/2.0/mod/mod_userdir.html)

good luck
mb.

---

