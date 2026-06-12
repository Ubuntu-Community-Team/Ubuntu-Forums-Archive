---
title: "configuring Apache"
date: 2010-10-16
forum: Server Platforms
---

### Post by pinatano on 2010-10-16
Hi there,
I am totally new to Linux and Ubuntu so sorry for the really newbie question.  I have installed Ubuntu on my older PIII server and it runs fine but now trying to setup my website.  I created the site, copied it to /var/www/pinatano directory and made the links in sites-available and sites-enabled as per some documentation I found on the web.  

However when I go to restart my apache2 I get:

=====================================================
[COLOR=Blue] sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                                                                                         [fail]

can anyone provide guidance as to what I need to do to resolve this and anything else I should check.[/COLOR]

======================================================

My domain is registered with GoDaddy and they are doing a forward to No-IP.com which I have it sent to my public address on port 8000 since my cable ISP blocks port 80.  I have not yet configured my router to do a port translation yet from 8000 to 80 but will have to fix that once I can at least see my website on my internal LAN.

thanks for your help...

---

### Post by jtarin on 2010-10-16
[This thread]("http://www.linuxquestions.org/questions/linux-server-73/apache-giving-the-error-could-not-determine-the-servers-fully-qualified-domain-name-280677/") might help....read in its entirety first.
FQDN is the problem.

---

### Post by pinatano on 2010-10-16
thanks for the input, however this seems a bit confusing.  Let me provide you with what is in my /etc/hosts file, my /etc/apache2/httpd.conf file as well as the webite file pinatano under sites-available directory.  Maybe you can pin point where I went wrong.
thanks:

 /etc/hosts file:
============
127.0.0.1 localhost ubuntu-web1
#####127.0.1.1 ubuntu-web1 brossardsoccer.com
127.0.0.1 localhost.localdomain localhost pinatano


# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

==========================================


[COLOR=Blue]/etc/apache2/httpd.conf
[/COLOR][COLOR=Blue]===============================
# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so


# NameVirtualHost *

hostname pinatano.com
ServerName ubuntu-web1

================================[/COLOR]


[COLOR=Teal]pinatano file under sites-available directory
=============================

Listen 80
## Listen 8000
## Listen 81

NameVirtualHost pinatano:80
## NameVirtualHost 192.168.2.100:81

#
#############################################
# First virtual host --> [www.pinatano.com](www.pinatano.com)
#############################################
#
<VirtualHost pinatano:80>
        ServerAdmin [email]info@pinatano.com[/email]
        ServerName pinatano
        ServerAlias *.pinatano.com
        DocumentRoot /var/www/pinatano/

        <Directory /var/www/pinatano/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

#       ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
#       <Directory "/usr/lib/cgi-bin">
#               AllowOverride None
#               Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
#               Order allow,deny
#               Allow from all
#       </Directory>

        ErrorLog /var/log/apache2/error.log
        LogLevel warn
        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

#    Alias /doc/ "/usr/share/doc/"
#   <Directory "/usr/share/doc/">
#        Options Indexes MultiViews FollowSymLinks
#        AllowOverride None
#        Order deny,allow
#        Deny from all
#        Allow from 127.0.0.0/255.0.0.0 ::1/128
#    </Directory>

</VirtualHost>
#
#
#
#
===============================================
[/COLOR]


is there any other file that I should show you?

thanks again!

---

### Post by Joshwaa on 2010-10-16
I suggest that you check out "Xampp". Look at the Linux download, it's really easy to install! Then it's a simple "sudo /opt/lampp/lampp start" in the terminal to start it. Just a suggestion.

---

### Post by jtarin on 2010-10-16
How did you install Apache....by Synaptic?
Have you tried connecting with  [http://localhost/basic.html](http://localhost/basic.html)
[Here's]("http://www.ehow.com/how_6854200_create-new-domain-apache-server.html") some tips you might have overlooked.

---

### Post by asmoore82 on 2010-10-16
If you are simply adding files to /var/www,
You don't have to mess with "sites-available" or "sites-enabled" because /var/www is the default site.
If you put files in "/var/www/foobar" you'll just have to navigate a
browser to "http://localhost/foobar/" to see them.
And remember Linux as well as modern webservers and browsers are all case sensitive.

If you do ever need to make a change to "sites-enabled"
you can't simply start apache2 again because it is already running,
you have to stop it first; or you can take the shortcut and tell it to restart.

But, apache is a special service that also supports the reload command.
This tells it to reload its config files without having to stop/start it:
```
sudo service apache2 reload
```

---

### Post by asmoore82 on 2010-10-16
> **Joshwaa said:**
> I suggest that you check out "Xampp". Look at the Linux download, it's really easy to install! Then it's a simple "sudo /opt/lampp/lampp start" in the terminal to start it. Just a suggestion.

Avoid Xampp or any 3rd party server packages like the plague!!

Firstly, the OP may not even need MySQL or PHP.
And if you don't need it, you certainly don't want it running unchecked on a public server.

But more importantly, you want to stick with the official packages from the package manager
because they will automatically receive security updates down the road.
Xampp perpetuates a "set it and forget it" approach to software which is
bad enough in general but potentially disastrous on a public server.

Also, on Ubuntu you can simply
```
sudo tasksel
``` and select the so called "LAMP" stack to be installed.

---

### Post by pinatano on 2010-10-16
I followed the step by step instructions as indicated by jtarin (thanks by the way) and after restarting this is what I get:

[COLOR=Blue]===============================

@ubuntu-web1:/etc/apache2$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                  httpd (no pid file) not running
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                                                                           [fail]

================================[/COLOR]

and when I point to the web-server from another computer on my network it tell me that Firefox could not connect to 10.10.10.100 (the IP address of my Ubuntu Apache server)

any more ideas? :confused:

thanks for being patient!

Cheers,

---

### Post by cariboo on 2010-10-16
Moved to Server Platforms.

---

### Post by asmoore82 on 2010-10-16
> **pinatano said:**
> I followed the step by step instructions as indicated by jtarin (thanks by the way) and after restarting this is what I get:

[COLOR=Blue]===============================

@ubuntu-web1:/etc/apache2$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                  httpd (no pid file) not running
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                                                                           [fail]

================================[/COLOR]

and when I point to the web-server from another computer on my network it tell me that Firefox could not connect to 10.10.10.100 (the IP address of my Ubuntu Apache server)

any more ideas? :confused:

thanks for being patient!

Cheers,

What's currently in your "sites-enabled" ?

---

### Post by Ryan Dwyer on 2010-10-16
Better yet, please post the contents of /etc/apache2/ports.conf.

---

### Post by pinatano on 2010-10-17
in my sites-enabled directory I have 2 files 
000-default
pinatano

and the pinatano file is as follows:

[COLOR=Blue]================================================

Listen 80
## Listen 8000
## Listen 81

NameVirtualHost pinatano:80

#
#############################################
# First virtual host --> [www.pinatano.com](www.pinatano.com)
#############################################
#
<VirtualHost pinatano:80>
        ServerAdmin [email]info@pinatano.com[/email]
        ServerName pinatano
        ServerAlias [www.pinatano.com](www.pinatano.com)
        DocumentRoot /var/www/pinatano

        <Directory /var/www/pinatano/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

#       ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
#       <Directory "/usr/lib/cgi-bin">
#               AllowOverride None
#               Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
#               Order allow,deny
#               Allow from all
#       </Directory>

        ErrorLog /var/www/pinatano/error.log
        LogLevel warn
        CustomLog /var/www/pinatano1/access.log combined
        ServerSignature On

#    Alias /doc/ "/usr/share/doc/"
#   <Directory "/usr/share/doc/">
#        Options Indexes MultiViews FollowSymLinks
#        AllowOverride None
#        Order deny,allow
#        Deny from all
#        Allow from 127.0.0.0/255.0.0.0 ::1/128
#    </Directory>

</VirtualHost>
#
#[/COLOR]

---

### Post by pinatano on 2010-10-17
/etc/apache2/ports.conf file is this:

=============================
[COLOR=Red]
Listen 80
Listen 8000


<IfModule mod_ssl.c>
    Listen 443
</IfModule>[/COLOR]

==============================

---

### Post by Ryan Dwyer on 2010-10-17
In ports.conf, remove the existing Listen directives and replace with:
NameVirtualHost *:80
Listen 80

Remove the Listen and NameVirtualHost directives from your virtualhost files (all files in sites-enabled). Replace all of the opening VirtualHost blocks with <VirtualHost *:80>.

Then restart Apache.

---

### Post by pinatano on 2010-10-17
Dude,

thanks it worked!  Much appreciated.  I will now create my access list on my router so that I can access it from my public IP address. 

At lease I can now see the site from my internal LAN.

thanks

my site [www.pinatano.com](www.pinatano.com)  should be available from the outside soon.

cheers,

---

### Post by pinatano on 2010-10-18
quick question again
if I want to have apache to also respond to port 8000 as well as the default port 80 since I an redirecting my site from No-IP with a :8000 do i simply put a listen statement in ports.conf of 8000 ?  or do I have to add another line elsewhere?

thanks

---

### Post by Ryan Dwyer on 2010-10-19
An easier way would be to change the port forwarding in your router so external 8000 goes to internal 80. If you can't do that, try the following but I can't guarantee it'll work (I've never tried it):

In ports.conf, change the NameVirtualHost *:80 to just NameVirtualHost *
Add Listen 8000 (so you have Listen 80 and Listen 8000 on separate lines)
Change your VirtualHost blocks to <VirtualHost *>
Restart Apache

---

