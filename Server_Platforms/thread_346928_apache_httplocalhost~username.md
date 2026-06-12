---
title: "apache: http://localhost/~username?"
date: 2007-01-26
forum: Server Platforms
---

### Post by Ubuntuud on 2007-01-26
I set up my apache server to try some PHP code. Everything works fine, except 'http://localhost/~pieter' (pieter is my username).

How can I get this back?
I'm on Feisty btw.

pieter.

---

### Post by llamakc on 2007-01-26
What about by IP?

127.0.0.1/~pieter

instead?

What's your /etc/hosts look like?

---

### Post by thornomad on 2007-01-27
Have you tried just accessing your localhost ?  Not "/~username" ... the way my Apache is setup the files are in the /var/www folder and asking for a username, I believe, doesn't do anything.

---

### Post by chrisfay on 2007-01-27
> Everything works fine, except 'http://localhost/~pieter' (pieter is my username).

You would need to set Apache up to use /home directories rather than the default folder /var/www since [http://localhost/~pieter](http://localhost/~pieter) is actually an attempt to access pieter's home folder. 

Here is the Apache doc's on the subject:
[http://httpd.apache.org/docs/2.0/howto/public_html.html](http://httpd.apache.org/docs/2.0/howto/public_html.html)
> 
On systems with multiple users, each user can be permitted to have a web site in their home directory using the UserDir directive. Visitors to a URL [http://example.com/~username/](http://example.com/~username/) will get content out of the home directory of the user "username", out of the subdirectory specified by the UserDir directive.

---

### Post by Koybe on 2007-01-27
You just need to enable usermod. 

```
sudo a2enmod userdir
sudo /etc/init.d/apache2 force-reload
```

---

### Post by az on 2007-01-27
The userdir module should be enabled by default, but make sure you didn't turn it off.

sudo a2enmod userdir

Edit - I see I kept this tab open too long before answering.....

---

### Post by Ubuntuud on 2007-01-28
Thanks. That 'sudo a2enmod userdir' did the trick.
Thanks a lot!

---

### Post by ameseisch on 2008-03-12
Installed LAMP with taskel on gusty

 did sudo a2enmod userdir

created home/user/public_html

force reload didn't work, says:

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

went to localhost/~aa/  anyway just to see

if only htm files its shows parent directory list but if click on a file: 

forbidden

You don't have permission to access /~aa/index.htm on this server.

and if  there is a .php file in my public_html file I get

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/home/aa/public_html/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

can anyone help me figure out what is going wrong here?

---

