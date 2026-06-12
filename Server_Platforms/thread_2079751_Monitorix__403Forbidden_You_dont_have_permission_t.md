---
title: "Monitorix:  403Forbidden You dont have permission to access /monitorix on this server"
date: 2012-11-02
forum: Server Platforms
---

### Post by the_trooper47 on 2012-11-02
help needed plzzz

I followed the instructions given at 'http://www.monitorix.org/doc_debian.html', installed Monitorix via the repository on my ubuntu server 12.04. The installation went ok, only prob is that no network pc/ web-browser can view the log-in/ main webpage(ie. 192.168.x.x/monitorix). 

The error on both of the network pc's (using Firefox) is:

Forbidden

You don't have permission to access /monitorix on this server.
Apache/2.2.22 (Ubuntu) Server at 192.168.x.x Port 80



the /etc/monitorix.conf reads:

our $BASE_DIR = "/usr/share/monitorix/";
our $BASE_LIB = "/var/lib/monitorix/";
our $BASE_URL = "/monitorix";
our $BASE_CGI = "/monitorix-cgi";


the /etc/apache2/conf.d/monitorix.conf reads:

Alias /monitorix /usr/share/monitorix
ScriptAlias /monitorix-cgi /usr/share/monitorix/cgi-bin

<Directory /usr/share/monitorix/cgi-bin/>
        DirectoryIndex monitorix.cgi
        Options ExecCGI
        order deny,allow
        deny from all
        allow from all
</Directory>


I've google'd plenty of how-to's, & checked I had installed & configured each of the files correctly - all seems fine, each time I open up the page (above) I get the 403 Forbidden notice/error. AFAIK I have configured each of the files correctly... 

:confused: Is there a step I've missed? 
:confused: If anyone has successfully installed/ configured  monitorix... how did u do it??  :)
[-o< Any clues to how I can fix this issue with permissions?

Cheers

---

### Post by SeijiSensei on 2012-11-02
First, the directory /usr/share/monitorix must be readable by the "apache" user, which is the user the web server runs as.  Next, take a look at /var/log/apache2/error.log and see what it says the problem is.  You probably also need to add a <Directory> stanza for the main site directory since the Ubuntu default is to prohibit the web server from accessing any directory other than /var/www.

In your monitorix.conf file, try adding the following:

```

<Directory "/usr/share/monitorix">
Options +Indexes
</Directory>

```

If "Indexes" is not enabled, you cannot list a directory nor access any index.* files that reside there.

Also, make sure that /usr/share/monitorix/cgi-bin/monitorix.cgi is executable by all users, or at least by the apache user.  You might also try adding "Options +Indexes" to the <Directory> stanza for the cgi-bin directory that you have now.

---

### Post by the_trooper47 on 2012-11-04
Hey SeijiSensei, thanks for your reply

I've gone over what u've said, here's what I've got:

plz excuse my partial noobness lol!


a) ls -la /usr/share/monitorix

```
total 44
drwxrwxr-x   4 www-data www-data  4096 Nov  1 20:44 .
drwxr-xr-x 233 root     root     12288 Nov  1 20:44 ..
drwxrwxr-x   2 www-data www-data  4096 Nov  1 20:44 cgi-bin
drwxrwxr-x   2 www-data www-data  4096 Oct 16 09:40 imgs
-rwxr-xr-x   1 www-data www-data  6421 Nov  3 00:39 index.html
-rw-r--r--   1 www-data www-data  1870 Oct 16 09:40 logo_bot.png
-rw-r--r--   1 www-data www-data  4021 Oct 16 09:40 logo_top.png
-rw-r--r--   1 www-data www-data  2251 Oct 16 09:40 monitorixico.png
```

 - Re: permissions, does this look as you'd expect?
 - Does every sub-dir need to be owned by user 'www-data' to allow execute permission/ access the monitorix dir? Atm, /usr & /usr/share are owned by root.


b) /var/log/apache2/error.log: [Sat Nov 03 19:06:24 2012] [error] [client 192.168.x.x] client denied by server configuration: /usr/share/monitorix


c) is this what you were referring to? Main site <Directory> /etc/apache2/sites-available/default reads:

```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/public_html/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/public_html>
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
```


d) /etc/apache2/conf.d/monitorix.conf now reads:

```
Alias /monitorix /usr/share/monitorix
ScriptAlias /monitorix-cgi /usr/share/monitorix/cgi-bin

<Directory /usr/share/monitorix/cgi-bin/>
        DirectoryIndex monitorix.cgi
        Options ExecCGI Indexes
        order deny,allow
#       deny from all
        allow from all
</Directory>
```
Was this what you meant?


e) /usr/share/monitorix/cgi-bin/monitorix.cgi is executable by the owner & group 'www-data'.

```
drwxrwxr-x 2 www-data www-data   4096 Nov  1 20:44 .
drwxrwxr-x 4 www-data www-data   4096 Nov  1 20:44 ..
-rwxr-xr-x 1 www-data www-data 459653 Oct 16 09:40 monitorix.cgi
-rw-r--r-- 1 www-data www-data     20 Nov  3 00:39 monitorix.conf.path
```

f) > You might also try adding "Options +Indexes" to the <Directory> stanza for the cgi-bin directory that you have now. 

Not sure what u mean, which file are you referring to & can you give an example?

g) the /etc/monitorix.conf reads:

```
our $TITLE = "Ubuntu Server";
our $HOSTNAME = "";
our $THEME_COLOR = "black";
our $REFRESH_RATE = "150";
our $IFACE_MODE = "graph";
our $ENABLE_ZOOM = "Y";
our $NETSTATS_IN_BPS = "N";
our $DISABLE_JAVASCRIPT_VOID = "N";

our $BASE_DIR = "/usr/share/monitorix/";
our $BASE_LIB = "/var/lib/monitorix/";
our $BASE_URL = "/monitorix";
our $BASE_CGI = "/monitorix-cgi";
```
Does this look ok?


Cheers

---

### Post by SeijiSensei on 2012-11-04
> **the_trooper47 said:**
>  
 - Re: permissions, does this look as you'd expect?
 - Does every sub-dir need to be owned by user 'www-data' to allow execute permission/ access the monitorix dir? Atm, /usr & /usr/share are owned by root.

No, not as long /usr and /usr/share have execute permissions for all users ("drwxr-xr-x") as they do by default.

Onc you get things working, I'd start removing write privileges. You should only grant the web server user www-data write privileges in directories outside the publicly-visible web site directory for security reasons.

> b) /var/log/apache2/error.log: [Sat Nov 03 19:06:24 2012] [error] [client 192.168.x.x] client denied by server configuration: /usr/share/monitorix

d) /etc/apache2/conf.d/monitorix.conf now reads:

```
Alias /monitorix /usr/share/monitorix
ScriptAlias /monitorix-cgi /usr/share/monitorix/cgi-bin

<Directory /usr/share/monitorix/cgi-bin/>
        DirectoryIndex monitorix.cgi
        Options ExecCGI Indexes
        order deny,allow
#       deny from all
        allow from all
</Directory>
```
Was this what you meant?

Not sure what u mean, which file are you referring to & can you give an example?

You probably need only to add another stanza to monitorix.conf that looks like this:

```

<Directory /usr/share/monitorix>
     Options Indexes
</Directory>

```

Notice that the error message you cite concerns access to /usr/share/monitorix.

---

