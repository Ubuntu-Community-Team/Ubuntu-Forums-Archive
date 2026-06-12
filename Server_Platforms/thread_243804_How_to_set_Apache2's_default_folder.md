---
title: "How to set Apache2's default folder?"
date: 2006-08-25
forum: Server Platforms
---

### Post by kenquad on 2006-08-25
Hey all:

Simple question, I guess, just can't figure it out.  Where in apache2.conf (or anywhere else, for that matter) do I go to set the default document folder?  This is a LAN application, not an actual website, and what I want to do is set it up so that when somebody types in the IP address of my computer, they always see a certain document.  Any help would be appreciated.  Thanks.

Ken Quad

---

### Post by chonger on 2006-08-25
You want to set DocumentRoot and DirectoryIndex in combination. The first sets the root directory (aka folder) of the server, the second sets the default file to display in a directory.

---

### Post by kenquad on 2006-08-25
> **chonger said:**
> You want to set DocumentRoot and DirectoryIndex in combination. The first sets the root directory (aka folder) of the server, the second sets the default file to display in a directory.

So are these variables in apache2.conf?  Because I can't find them.

---

### Post by harisund on 2006-08-25
No, they are in /etc/apache2/sites-available/default

---

### Post by kenquad on 2006-08-25
Question answered; thanks both!

---

### Post by kenquad on 2006-08-28
OK, maybe not quite answered :-)  I don't see a DirectoryIndex parameter in the config file, just some <directory> tags which seem intended to set permissions for the root directory.  Am I missing something or will I have to add this parameter?

Thanks,
Kenquad

---

### Post by lamego on 2006-08-28
```
lamego@lamego-desktop:/etc/apache2$ grep -r DirectoryIndex *
apache2.conf:DirectoryIndex index.html index.cgi index.pl index.php index.xhtml
lamego@lamego-desktop:/etc/apache2$

```

---

### Post by lugos on 2006-08-28
I had the same question.  I found DirectoryIndex, and I'd like to keep that the same.  But I couldn't find how to change the default directory.  Here is what I have come across, but I don't know which needs to be changed:

**In my apache2.conf file**
# UserDir is now a module
#UserDir public_html
#UserDir disabled root

#<Directory /home/*/public_html>
[INDENT]#AllowOverride FileInfo AuthConfig Limit[/INDENT]
[INDENT]#Options Indexes SymLinksIfOwnerMatch IncludesNoExec[/INDENT]
#</Directory>

**Or in my default file (/etc/apache2/sites-available)**
DocumentRoot /var/www
<Directory />
[INDENT]    Options FollowSymLinks
    AllowOverride None[/INDENT]
</Directory>
<Directory /var/www/>
[INDENT]    Options Indexes FollowSymLinks MultiViews
    AllowOverride None
    Order allow,deny
    allow from all
    # Uncomment this directive is you want to see apache2's
    # default start page (in /apache2-default) when you go to /
    #RedirectMatch ^/$ /apache2-default/[/INDENT]
</Directory>

**Or in my 000-default file (/etc/apache2/sites-enabled)**
DocumentRoot /var/www
<Directory />
[INDENT]    Options FollowSymLinks
    AllowOverride None[/INDENT]
</Directory>
<Directory /var/www/>
[INDENT]    Options Indexes FollowSymLinks MultiViews
    AllowOverride None
    Order allow,deny
    allow from all
    # Uncomment this directive is you want to see apache2's
    # default start page (in /apache2-default) when you go to /
    #RedirectMatch ^/$ /apache2-default/[/INDENT]
</Directory>

Any help would greatly appreciated.

Thanks,
lugos

---

### Post by harisund on 2006-08-28
First, 000-default is basically just a symbolic link back to default in the sites-available folder. 

Next, wherever you see /var/www/ in the sites-available/default folder, change it to your required folder.

---

### Post by shanbyrt on 2007-10-08
The following posted by lamego:
> 
Code:

lamego@lamego-desktop:/etc/apache2$ grep -r DirectoryIndex *

Found the dir.conf file in the mods-available/ dir for my install of the out-of-the-box LAMP server.  I needed to add *gulp* index.cfm to my DirectoryIndex.

Hope this helps someone.

---

