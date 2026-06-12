---
title: "Configuring apache2 to use index.php as default"
date: 2009-04-01
forum: Server Platforms
---

### Post by rbfthomas on 2009-04-01
Running Intrepid x86_64 / apache 2 / php5

I'm trying to switch my apache installation to recognize an index.php file as a default document in my /var/www directory (yes, I know they say not to use that, but this is a small in-lab machine.)  

The problem is that if I set up /var/www/index.php with a very simple PHP content (phpinfo(), to be exact), when I just point my FF to [http://server/](http://server/), I get a dialog box saying:

[INDENT]Opening:
You have chosen to open

which is a: ~ file
from [http://server](http://server)

**What should Firefox do with this file?**

Open with (Browse...)
Save File

[] Do this automatically for files like this from now on[/INDENT]

I'm sure you've seen the dialog before. Here's the weird thing: if I explicitly stipulate the file - [http://server/index.php](http://server/index.php) - it displays.

Here's what I've done: 
adjusted my /etc/apache2/mods-available/dir.conf file to look like this:
[INDENT]<IfModule mod_dir.c>

          DirectoryIndex index.php index.shtml index.html index.cgi index.pl index.xhtml index.htm

</IfModule>[/INDENT]

my /etc/apache2/mods-available/php5.conf file looks like this:
[INDENT]<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>
[/INDENT]

and my /etc/apache2/mods-available/php5.load file looks like this:
[INDENT]LoadModule php5_module /usr/lib/apache2/modules/libphp5.so[/INDENT]

I also have a line in my /etc/apache2/httpd.conf file that looks like this:
[INDENT]DirectoryIndex index.php index.shtml index.html index.html.var index.htm [/INDENT]

Any hints?  Anywhere else I could look?

TIA!

---

### Post by cdenley on 2009-04-01
Are you sure your browser isn't caching the page?

---

### Post by primaxx on 2009-04-01
I'm not sure if this helps you in anyway, but I experienced the same thing on 8.04 today, and for me, the solution was to install *libapache2-mod-php5*.
(Which it seems that you have allready installed...) Sorry! :-)

---

### Post by rbfthomas on 2009-04-01
> **cdenley said:**
> Are you sure your browser isn't caching the page?Um - I'm pretty sure - how would I know that?  And why does the dialog box only show up when I stipulate the directory?  When I give it the full path, including index.php, the page displays properly.

---

### Post by cdenley on 2009-04-01
> **rbfthomas said:**
> Um - I'm pretty sure - how would I know that?  And why does the dialog box only show up when I stipulate the directory?  When I give it the full path, including index.php, the page displays properly.

When your web browser requests the URI "/index.php", it does not know that this request would be equivalent to "/", so the page it has cached for "/" is not re-used, and the request is actually sent to the server. You can clear your cache (Tools>Clear Private Data...) then restart firefox, or use another web browser.

You can also examine server responses from the terminal.
```

echo -e "HEAD / HTTP/1.0\n" | nc myhost.com 80

```
Your server's response should end with
```

Content-Type: text/html

```
It should not end with
```

Content-Type: application/x-httpd-php

```

---

### Post by rbfthomas on 2009-04-02
Thanks so much, cdenley.  Turns out I found the problem: I hadn't properly set the values in /etc/apache2/envvars.  The contents come "from the factory" looking like this:

[INDENT]export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data
export APACHE_PID_FILE=/var/run/apache2.pid
[/INDENT]
I needed to set up an apache group and apache user, and then change that to look like this:
[INDENT]export APACHE_RUN_USER=apache
export APACHE_RUN_GROUP=apache
export APACHE_PID_FILE=/var/run/apache2.pid
[/INDENT]
I also did a chmod 755 on the file, though I'm not sure if I needed to.  Once I did that and restarted the service, the directory comes up just fine.

---

### Post by cdenley on 2009-04-02
> **rbfthomas said:**
> Thanks so much, cdenley.  Turns out I found the problem: I hadn't properly set the values in /etc/apache2/envvars.  The contents come "from the factory" looking like this:

[INDENT]export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data
export APACHE_PID_FILE=/var/run/apache2.pid
[/INDENT]
I needed to set up an apache group and apache user, and then change that to look like this:
[INDENT]export APACHE_RUN_USER=apache
export APACHE_RUN_GROUP=apache
export APACHE_PID_FILE=/var/run/apache2.pid
[/INDENT]
I also did a chmod 755 on the file, though I'm not sure if I needed to.  Once I did that and restarted the service, the directory comes up just fine.

I doubt changing the user apache runs as or file permissions has anything to do with it. You probably hadn't restarted apache since enabling the php module.

---

### Post by eklem on 2009-04-17
> **rbfthomas said:**
> Um - I'm pretty sure - how would I know that?  And why does the dialog box only show up when I stipulate the directory?  When I give it the full path, including index.php, the page displays properly.

I got the same problem and just tested with another browser. It worked then. Delete the cache in your browser and I think you should be fine.

---

### Post by |Eric| on 2009-05-13
i do have same problem here 
my browser isnt caching the page (emptied the cache 3 times now) 
still not working 

it basicaly says that the requested page is unavailable or server cannot be found (IE) 

also i did recheck of the config and also a restart of the server 
still to no avail 
gona change file permissions now ...

---

### Post by cdenley on 2009-05-13
> **|Eric| said:**
> 
it basicaly says that the requested page is unavailable or server cannot be found (IE)
That's pretty vague. Is the server giving a response? If so, what is the response?
```

echo -e "HEAD / HTTP/1.0\n"|nc localhost 80

```

Is it only a problem when requesting /, or does /index.php work?

---

### Post by |Eric| on 2009-05-13
weird there must be a bug 
well i  changed the permissions & it didnt work 
(changed  to rwx on owner & group to www-data:root )
that didnt work 
i then moved the precedence of index.php in the DirectoryIndex directive in dir.conf
(moved it first ) 

that did work  for some reason ! (notice there is no index.html in the folder (i renamed it .html.bak)

---

