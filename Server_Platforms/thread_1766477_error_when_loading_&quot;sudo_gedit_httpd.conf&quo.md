---
title: "error when loading &quot;sudo gedit httpd.conf&quot;"
date: 2011-05-24
forum: Server Platforms
---

### Post by koshiuk on 2011-05-24
Hi,  I've installed apache2 and and when i access my URL from outside using [www.proxy-service.de]("http://www.proxy-service.de") i just get a webpage with 
**Index of /**

so i've run the command **sudo gedit /etc/apache2/httpd.conf** which give me the error:

[I] Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.2EUJVV': No such file or directory

(gedit:2509): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory[/I]

_my httpd.conf is as follows, _

Userdir public_html
Options +Indexes
Options All

ServerName localhost

<Directory "/home/gav/public_html/">
Order allow,deny
Allow from all
AllowOverride All
</Directory> 


i guess i have to set permissions somehow and then my index.html will be displayed correctly or am i missing something else? my index.html is located in /home/gav/public_html

Many thanks for your help in advance.

---

### Post by koshiuk on 2011-05-24
Ive been scouring the net and think my index.html permissions maybe wrong?

-rw-r--r-- 1 gav gav 236 2011-05-18 19:02 index.html



my public_html is set to
drwxr-xr-x 2 gav gav 4096 2011-05-24 22:52 public_html

Many thanks.

---

