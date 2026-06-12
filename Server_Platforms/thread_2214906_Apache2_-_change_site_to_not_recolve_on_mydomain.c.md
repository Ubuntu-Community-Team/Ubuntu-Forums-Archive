---
title: "Apache2 - change site to not recolve on mydomain.com/owncloud"
date: 2014-04-03
forum: Server Platforms
---

### Post by llewellynpienaar on 2014-04-03
[COLOR=#333333][FONT=Lucida Grande]Good day ubuntu community.[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I have a small but very annoying issue with owncloud, or apache. And I am sure I did something wrong with the installation or that I am not to sure how apache works just yet. [/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I have a sub domain name called cloud.mydomain.com that I have forwarded to my server. However I would like to set it up that I can only access owncloud on cloud.mydomain.com instead of mydomain.com/owncloud? At this moment I can access owncloud on both cloud.mydomain.com and mydomain.com/owncloud. How do I disable connection to mydomain.com/owncloud.[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Any suggestion on how I can get that done?.

Thanks[/FONT][/COLOR]

---

### Post by dudumomo on 2014-04-03
Hi,

It's a normal behaviour, you didn't do anything wrong.

Not sure you should disable mydomain.com/owncloud....if people used to visit this page, it might be frustrating for them not to find it anymore. 
I would suggest to do a redirection instead mydomain.com/owncloud to cloud.mydomain.com
Like that it will educate users.
You can do with the option redirect like:
```
        Redirect /owncloud http://cloud.mydomain.com/
```
to add to your mydomain.com virtualhost, after the <VirtualHost *:80>

But if you do want to forbid access, you could modify your mydomain.com virtualhost to add the following section:

```
        <Directory /var/www/myfolderowncloud>
                Order allow,deny
                deny from all
        </Directory>
```
(If you have one? it should not be set in your cloud.mydomain.com virtualhost)

Hope it helps!

---

