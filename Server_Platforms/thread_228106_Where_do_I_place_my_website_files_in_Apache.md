---
title: "Where do I place my website files in Apache"
date: 2006-08-02
forum: Server Platforms
---

### Post by cocotu on 2006-08-02
Hi guys, in my LAMP server I'm trying to place a little site at /var/www. The thing is I'm not sure if this is the right place to put the index.html. Someone told me that I needed to create an /html folder and place the index.html there. I did that but I get:

Index of /
 Name                    Last modified      Size  Description-------------------------------------------------------------------------------- 
 Joomla1-0/              01-Aug-2006 18:05    -   
 apache2-default/        01-Aug-2006 12:42    -   
 html/                   01-Aug-2006 12:42    -   
 public_html/            01-Aug-2006 16:38    -   

I wish I can get the index.html by just entering my hosts address. Lets say I click on the html/ I see the index.html or if I click on the apache2-default/ I also get the index.html that I placed there as well. Also I can do that in the public_html/. But, as you can read I'm a total newbie doing this! Where is the correct place to put my website? /var/www?
How about if I want to create directories like those hosting companies such as:

/public_html
/cgi_bin
/private
I have been reading around but I don't see to get a straight answer.  Thanks!!

---

### Post by bmonkey on 2006-08-02
place your files anywhere in /var/www/  - but to display the index.html must be in the "root" directory i.e the www folder and not any subfolders.. then just check it by visiting [http://localhost](http://localhost) or what ever ur server ip is

---

### Post by cocotu on 2006-08-03
Thanks bmonkey. But is there a way that I can organize things, for example I have a hosting company that has:

/public_html
/cgi_bin
/private

Can I do this also? How can this be possible?

Thanks again.

---

### Post by bernied on 2006-08-03
have a look in /etc/apache2
httpd.conf is the main configuration file
there are also files in 
/etc/apache2/vhosts.d

It is all configurable and the answer has to be read the manuals. Apache's website is excellent with lengthy and easy-to-read documentation:
[http://httpd.apache.org/](http://httpd.apache.org/)

---

### Post by az on 2006-08-03
Just uncomment the redirect-match directive in the default site to point to your index.html, wherever it is.

---

### Post by alecjw on 2006-08-03
> **cocotu said:**
> Thanks bmonkey. But is there a way that I can organize things, for example I have a hosting company that has:

/public_html
/cgi_bin
/private

Can I do this also? How can this be possible?

Thanks again.

To make those folders, run this command:
sudo mkdir /var/www/public_html/ /var/www/cgi_bin/ /var/www/private/

You will probably want to delete the sample folder. do this by:
sudo rmdir /var/www/apache2-default/

---

### Post by harisund on 2006-08-03
> **bernied said:**
> have a look in /etc/apache2
httpd.conf is the main configuration file
there are also files in 
/etc/apache2/vhosts.d

It is all configurable and the answer has to be read the manuals. Apache's website is excellent with lengthy and easy-to-read documentation:
[http://httpd.apache.org/](http://httpd.apache.org/)

Hmm..just in case anyone is reading this, the /etc/apache2/httpd.conf is *not* the main configuration file. 

In Debian/Ubuntu it is /etc/apache2/apache2.conf and site related details are in /etc/apache2/sites-available/default

---

### Post by cocotu on 2006-08-03
I guess I will just place everything under the /var/www. We are planning to have this server for our Intranet and we are thinking about setting up a CMS or any free bullentin board.

---

### Post by harisund on 2006-08-03
2 minor things you might wish to know. 

First, the 'owner' of /var/www is root. Which means if you are planning on running a CMS or something that has to write to the hard disk, you will need write permissions for the www-data user/group (since that is what Apache2 runs by default as). 

If you want to do some testing, you could always do ```
 sudo a2enmod userdir
```. The advantage of this is you could place your files in ~/public_html. Meaning create a directory called public_html in your home. Assuming your username is cocotu all files in public_html can be accessed using [http://localhost/~cocotu](http://localhost/~cocotu). So before you place anything directly in /var/www (which is accessible through [http://localhost](http://localhost)) you can test them out first.

---

### Post by bernied on 2006-08-04
I apologise for my earlier mistake with the locations of configuration files - I assumed that the configuration would be the same across linuxes (my apache2 server is on a gentoo system).

At the moment, if I want the webserver to be able to write files, I manually use the chown command (chown apache /wherever/file), but this has to be done as root. Ideally I'd like to be able to select a menu item that opens an editor (and also one for a file manager) with my default group set to www-data, and with permissions for r/w for user and group. That way both my user and anyone else in that group (including apache) can write to any file (or directory) that I create with the editor (or file manager). And I'd only use those menu items for working on the webserver.

So how do I tell Ubuntu (Kubuntu for me) to do that? Are there options for user:group and mask when you create links to executables on the desktop? (I can't look myself right now - at work - but wanted to write this brainstorm down before I forgot)

---

### Post by bernied on 2006-08-04
If anyone cares
```
chmod g+s wwwstuff
```
where wwwstuff is a folder, sets a bit which makes every file created in that folder have the same group as the folder. But what about the mask - can that be set on a folder-to-folder basis?

---

### Post by cocotu on 2006-08-07
So if I use a CMS, is it OK to install it under root? Or should I make another user? Thanks..

---

