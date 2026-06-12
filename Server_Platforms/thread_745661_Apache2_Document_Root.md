---
title: "Apache2 Document Root"
date: 2008-04-04
forum: Server Platforms
---

### Post by marcks on 2008-04-04
I am new to Linux and am struggling a bit.

I have installed Apache2, PHP and MySQL.  I am attempting to change the Document Root but continually get errors.

The file I am changing is: etc/apache2/apache2.conf

There is no Document Root line so I have added:

DocumentRoot "/home/www/"  I have tried with and without ""

The error I get when I do the config test is:

Syntax error on line 297 of /etc/apache2/apache2.conf:
DocumentRoot must be a directory


Can anyone help please
Karen

---

### Post by Dr Small on 2008-04-04
Why not use /var/www/ ?
Also, as more pertaining to your question, does /home/www exist ?

Dr Small

---

### Post by egonzalez on 2008-04-04
Are you confident that the /home/www ???

You should keep the same location, it is easier !!

---

### Post by SteveHillier on 2008-04-04
I went through this pain last year when I was setting up a server.
I will see if I can find it for you.

I don't know how to link to the post but here is it's content

BEGIN INSERT

Thanks to all those who offered hints on getting my web server running.
It is now done. Three system rebuilds, and using my laptop as well, later. Many hours. The last rebuild because PHP was not working and reinstalling just didn't cut it.

Just to recap what I did in case it might help someone else.
New OS build (Dapper) --> do updates --> install Apache2, PHP5, MySql.
check php by running the phpinfo function
Add to the end of /etc/apache2/apache2.conf the line ServerName localhost (as suggested on this forum)
Set the permissions on /var/www to give read write execute access (at the moment to everyone)
Set up the web site on relevant folders make sure permissions are OK.
Set up hosts either in /etc/hosts directly of through networking on the GUI with the names of all the servers that will be accessible from this machine.
set the apache2 default file to act on blank names by uncommenting the Redirtect Match directive in /etc/apache2/sites-available/default - type [http://machinename](http://machinename) in the browser to check to see if default page is displayed in browser.
Add the Virtual hosts files to /etc/apache2/sites-available. 
Set up the symlinks using a2ensite command.
I won't insult anyone on this forum about how I set up the Win2003 DNS server.

That sounds easier than it was in reality. The trick that did the work for me was adding the server name in the NameVirtualHost and <VirtualHost > directives

One of my Virtualhost files reads

NameVirtualHost manorind.co.uk

<VirtualHost manorind.co.uk>
DocumentRoot /var/www/manorind
ServerName manorind.co.uk
ServerAlias [www.manorind.co.uk](www.manorind.co.uk)
DirectoryIndex index.php index.html index.htm
ErrorLog /var/log/apache2/manor-error.log
TransferLog /var/log/apache2/manor-access.log

<Directory /var/www/>
AllowOverride None
Allow from all
</Directory>

<Directory /var/www/manor/>
AllowOverride None
Allow from all
</Directory>
</VirtualHost>

The clue to this final solution came by a rather odd route.
I have the Ubuntu Linux Bible (Wiley 2007) , Ubutnu unleashed (SAMS 2007) and the Linux Bible (Wiley 2006). 
All these books have examples of setting up VIrtual Hosts. One give the example NameVirtualHost *:80. Another gives the example NameVirtualHost 212.85.67.67. The other uses the example NameVirtualHost *
I looked at the documentation for Apache2. Under the Name based Virtual Host section there is the following example

NameVirtualHost *:80

<VirtualHost *:80>
ServerName [www.domain.tld](www.domain.tld)
ServerAlias domain.tld *.domain.tld
DocumentRoot /www/domain
</VirtualHost>

Now I don't know what the * is. It is sometimes used as a wildcard but none of the texts tell me. If I don't know what something does I am very careful to leave it alone (as for example I don't know what ^/$ in the RedirectMatch directive of /etc/apache2/sites-available/default means so I don't go near it.

My final clue to this saga came from investigating Address based Virtual Hosts on the Apache2 documentation where the following example is given 

<VirtualHost www.smallco.com>
ServerAdmin [email]webmaster@mail.smallco.com[/email]
DocumentRoot /groups/smallco/www
ServerName [www.smallco.com](www.smallco.com)
ErrorLog /groups/smallco/logs/error_log
TransferLog /groups/smallco/logs/access_log
</VirtualHost>

So for the first time there is a clue that you can actually put a server name in the NameVirtualHost directive. I put this in for my hosts and "bingo" everything starts to work.

As a final whinge.
The Ubuntu Unleashed book I find has some problems. Mainly it is a edit of the Linux Unleased text. It is supplied with a release of Dapper but in the Apache2 section alone it is using instruction for Apache 1.3. As files are not in the same places this is very misleading. Elsewhere great chunks of test are duplicated from the Linux Unleashed text (Different authors by the way) 
The Linux Bible is all things to all men so I have no comment.
The Ubuntu Bible (a recent acquisition) is tailored for Dapper and seems to be OK. Sad that they ship Edgy on the CD. 

So a final big thanks to all those who tried to help out.
I will return the favour if I can.
Steve

END INSERT
Hope this helps

---

### Post by Oldsoldier2003 on 2008-04-04
> **marcks said:**
> I am new to Linux and am struggling a bit.

I have installed Apache2, PHP and MySQL.  I am attempting to change the Document Root but continually get errors.

The file I am changing is: etc/apache2/apache2.conf

There is no Document Root line so I have added:

DocumentRoot "/home/www/"  I have tried with and without ""

The error I get when I do the config test is:

Syntax error on line 297 of /etc/apache2/apache2.conf:
DocumentRoot must be a directory


Can anyone help please
Karen

on Ubuntu you edit /etc/apache2/sites-available/default not apache2.conf

---

### Post by marcks on 2008-04-05
> **Dr Small said:**
> Why not use /var/www/ ?
Also, as more pertaining to your question, does /home/www exist ?

Dr Small

/home/www does exist but I might just leave it the way it is.  Everything is so complex.

---

### Post by marcks on 2008-04-05
> **Oldsoldier2003 said:**
> on Ubuntu you edit /etc/apache2/sites-available/default not apache2.conf

thank you
Nowhere I looked did I see the file to edit was a different one, not sure if it was me or not.

---

