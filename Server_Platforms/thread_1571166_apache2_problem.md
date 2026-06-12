---
title: "apache2 problem"
date: 2010-09-09
forum: Server Platforms
---

### Post by Thyagaraj on 2010-09-09
Under /var/www2/site I have multiple directories and files(.css, .html, .js) and I could access these on the browser.
In this location(/var/www/site) I have a directory called 'javascript' and it has multiple files with .css, .html. .js ... exentions. I could not access any files of this 'javascript' directory on the browser and I'm getting following error.

**Not Found**

 The requested URL /javascript/design.js was not found on this server.


But if I copy this 'javascript' dir to something like 'javascript3', I could access all of the files under 'javascript3' on the browser. 
Renaming this directory would be problem for the programmers in my office as they have to modify every where they specified.

I could not figure out this issue, can any one help me?

---

### Post by Thyagaraj on 2010-09-13
The following are my apache configuration

vim /etc/apache2/sites-enabled/site1


<VirtualHost *:80>
DocumentRoot "/var/www2/mysite"
ServerName [www.mysite.com](www.mysite.com)
ServerAlias mysite.com
<Directory "/var/www2/mysite">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

I could access every thing under /var/www2/mysite except a directory named 'javascript' and if I rename this 'javascript' to something 'javascript2' then it is accessible on the browser. It even has the permissions what other directories have.
Need help...

---

### Post by Thyagaraj on 2010-09-13
I tried giving an alternate path by appending the following to the file '/etc/apache2/sites-enabled/site1' and now it is accessed on the browser. But I'm asked to do this without any additonal configuration.


Alias /javascript /var/www2/mysite/javascript
<Directory /var/www2/mysite/javascript>
AllowOverride FileInfo AuthConfig Limit Indexes
Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
</Directory>


hope this may help any one to figure out this issue

---

### Post by BkkBonanza on 2010-09-13
I've never heard of javascrpt having any special treatment so this is pretty odd. What happens if you make it a symbolic link?

ln -s /var/www2/site/javascript2 /var/www2/site/javascript

I'd grep your Apache conf files to make sure there isn't some odd directory setting.

grep -r javascript /etc/apache2

---

### Post by Ryan Dwyer on 2010-09-13
Have a look at /etc/apache2/conf.d/javascript-common.

```

Alias /javascript /usr/share/javascript/

<Directory "/usr/share/javascript/">
	Options FollowSymLinks MultiViews
</Directory>

```

You either have to change the config (comment that code), or get your devs to use a different folder.

---

### Post by Thyagaraj on 2010-09-13
I don't know how to appreciate you people. Thanks bonanza!.
My saviour Ryan thanks to you.

Many tried this but not successful so far. But I'll tell in my office that I have done this:D

Please reply to this that if comment out the line in "/etc/apache2/conf.d/javascript-common.conf" will there be any problem and why this directory/file is actually for?. When this file is created?

Thanks a lot!

---

### Post by Ryan Dwyer on 2010-09-13
If you install any javascript libraries from the repository (jQuery, MooTools, etc) it will put them in /usr/share/javascript/ and enable the alias.

You can do this:
ls /usr/share/javascript/

Then for each item in there:
apt-cache search itemname # to get the package name
apt-cache show packagename # to see more info about it so you can decide if you really want to uninstall it
sudo apt-get purge packagename # to remove completely

Note that some of them might be required by any web-based tools you might have installed from the repos.

---

