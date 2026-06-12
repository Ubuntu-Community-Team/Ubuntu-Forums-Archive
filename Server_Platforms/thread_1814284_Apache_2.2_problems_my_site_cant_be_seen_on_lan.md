---
title: "Apache 2.2 problems my site cant be seen on lan"
date: 2011-07-29
forum: Server Platforms
---

### Post by Daunus on 2011-07-29
Hi,  Im trying to just set up my web page so it can be seen on my local home Lan (then Ill try to get it on the internet). I can see the site it on my pc but other network users cant.

They can ping my computer but cant telnet to it on port 6060 (thats the one is set the server up on)

I hope somebody can tell me what's wrong with my configuration its mostly the default with a few changes that I hoped would make the site work.

my ip 192.168.1.10

Here is the sites-available default file

> 
<VirtualHost *:6060>
    ServerAdmin [EMAIL="myaddress@hotmail.com"]myaddress@hotmail.com[/EMAIL]

    ServerName 192.168.1.10

    DirectoryIndex index.php index.htm index.html
    
    
    DocumentRoot /home/daniel/Desktop/myprog/website/test/
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /home/me/Desktop/myprog/website/test/>
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
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
the ports.conf file
> 
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:6060
Listen 6060

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

the httpd.conf

> 
ServerName 192.168.1.10

I didn't change anything else.

Also does anybody know a good resource book or site or otherwise that can explain the basics of apache2 webserver. I cant find anything good, the apache documentation is alright but I think you need to already know what your doing to use it.

Thank you if anybody can provide any help, I have been trying to solve it through trial and error for over a week and I have no idea anymore.

---

### Post by ian dobson on 2011-07-29
Hi,

What do the other computers "see" when that go to [http://192.168.1.10:6060?](http://192.168.1.10:6060?) And what error message do you see in the apache error log (/var/log/apache2/error.log)

Whenever you can the conf file in apache you need to restart it, otherwise it won't read the new settings.

Regards
ian Dobson

---

### Post by Daunus on 2011-07-31
> **ian dobson said:**
> Hi,

What do the other computers "see" when that go to [http://192.168.1.10:6060?](http://192.168.1.10:6060?) And what error message do you see in the apache error log (/var/log/apache2/error.log)

Whenever you can the conf file in apache you need to restart it, otherwise it won't read the new settings.

Regards
ian Dobson
Thanks for the reply Ian, I have been restarting apache2 each time i make changes.

Other computers see a "the connection has timed out" error screen when they try to connect.

No new errors are generated when a computer from the lan tries to connect, in the error.log file. 

When I restart apache2 I do get 

> PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0

[Sun Jul 31 19:31:18 2011] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.9 with Suhosin-Patch configured -- resuming normal operations

mind you the website can still be seen on my home computer, not sure what this error is but I dont think its related. The file the error refers to has the following commands.

> # configuration for php MCrypt module
extension=mcrypt.so

---

### Post by Wim Sturkenboom on 2011-07-31
Apache also has an access log; you can check if the requests come in. As you can access the site from the PC itself (using 192.168.1.10 I assume), it's not likely an Apache issue.

Sounds more like a router issue to me (and I don't have knowledge of that) or firewall issue.

---

### Post by ian dobson on 2011-07-31
Hi,

The error you have in your log is nothing to worry about, it's just a warning that # comments are deprecated.

If you do wget  [http://192.168.1.10:6060](http://192.168.1.10:6060) on the server what do you get? Does it get the web page?

Could you try disabling the Allow from 127.0.0.0/255.0.0.0 ::1/128 line, restarting apache and try again.

Regards
Ian Dobson

---

### Post by Brad55 on 2011-07-31
Sounds like it could be your firewall, like the port is not open to allow incoming or outgoing packets. I know when I started my samba on my lan I had to change the firewall settings.

---

### Post by Daunus on 2011-08-01
> **Brad55 said:**
> Sounds like it could be your firewall, like the port is not open to allow incoming or outgoing packets. I know when I started my samba on my lan I had to change the firewall settings.

Correct its so often the simplest errors. turns out i have UFW (firewall) installed and that was blocking all incoming connections.

Thanks for the help everybody.

---

### Post by Wim Sturkenboom on 2011-08-01
Please mark your thread as solved using the thread tools just above the first post.

---

