---
title: "Setting up virtual host on apache"
date: 2008-02-24
forum: Server Platforms
---

### Post by seattle vic on 2008-02-24
So I'm new at this.  I got a domain name and am reading up on how to set up for virtual hosts.  I'm running apache 2.2.4 under ubuntu server.  I've gotten it to work, except that the browser takes you to an index, not to the html file.  I cannot see in the reading I've been doing how to direct the server to go right to the html file.

Here's my config files that I have under /etc/apache2/sites-availabe, (as well as a link in sites-enabled):

<VirtualHost *:80>
ServerName victorycat.com
ServerAlias [www.victorycat.com](www.victorycat.com)
ServerAdmin [email]victorino@isomedia.com[/email]
DocumentRoot /var/www/victorycat.com/
</VirtualHost>

My html file is in the /var/www/victorycat.com directory.  How do I tell apache to go there?

---

### Post by denver on 2008-02-24
You need to set the DirectoryIndex to what ever file will be your default page. This is usualy set in /etc/apache2/apache2.conf. The directive can also be set in your virtual host or .htaccess file. Just add

```
DirecoryIndex index.php index.html
```

right after DocumentRoot.

---

### Post by seattle vic on 2008-02-25
Denver,

it worked.  Thanks a lot.  Now on to the next problem :)

BTW, do you have a recommendation for apache docs?  What I found is not very complete for newbies, including the apache site.

Vic

---

