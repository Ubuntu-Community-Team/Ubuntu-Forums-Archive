---
title: "What's the ubuntu server edition?"
date: 2007-11-16
forum: Server Platforms
---

### Post by enchance on 2007-11-16
Noob thinking out loud: I'm using ubuntu 7.10 desktop and it's great! But can't seem to get LAMP right. Can I instead install 7.10 server? I mean, can I also run compiz-fusion and all the other stuff every desktop user has on the desktop version of ubuntu?

I just can't get LAMP to work right like in my previous [post]("http://ubuntuforums.org/showthread.php?p=3783125#post3783125"). All I really want is to get my LAMP setup properly in my gutsy desktop so I can test my php files.

Another thing, is it safe to say that the difference between the desktop and the server version of ubuntu is that the server edition let's you install LAMP?

---

### Post by HermanAB on 2007-11-16
There is nothing magical about the server edition.  If anything the server edition has less magic than the desktop editions...

The server version doesn't have X and the GUI schtuff, since in a data cetre, there are not screens and keyboards attached to the machines.  So if you have a desktop machine with a screen and keyboard attached, then you need the desktop version of Ubuntu.

---

### Post by enchance on 2007-11-16
> **HermanAB said:**
> There is nothing magical about the server edition...The server version doesn't have X and the GUI schtuff

So my only alternative is to get LAMP to work in my desktop environment... I hope someone finds an answer to my problem so I can start makin some sites.

Since LAMP defaults to "/var/www/" is it possible to change it to something like "~/www/" instead? I'm currently experiencing some Permissions [problems]("http://ubuntuforums.org/showthread.php?p=3783269#post3783269") in my current (and 1st try) of installing LAMP in my ubuntu desktop.

---

### Post by milton1 on 2007-11-16
> **enchance said:**
> So my only alternative is to get LAMP to work in my desktop environment... I hope someone finds an answer to my problem so I can start makin some sites.

Since LAMP defaults to "/var/www/" is it possible to change it to something like "~/www/" instead? I'm currently experiencing some Permissions [problems]("http://ubuntuforums.org/showthread.php?p=3783269#post3783269") in my current (and 1st try) of installing LAMP in my ubuntu desktop.

LAMP works very well in the desktop environment. There is a how-to for installing it in the ubuntu wiki.

changing your default folder is easy. In /etc/apache2/sites-available/default find this line:

```
DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
```
Change the document root to the folder you want to use.

---

### Post by wolfear on 2007-11-16
Or..another option which I used in the past (for local development only )was to install the server then install the desktop on top of it via apt.
Advantage there is your LAMP is preconfigured to your machine.
Disadvantage is you have be willing to use a command line for a bit and sometimes weird things can happen.

If you already have apache2, php and mysql installed but are just having permission problems, you might find life much easier if you make sure you (by this, I mean the username you use during your development work) are part of the www-data group.

As long as you are part of the www-data group, adding group permissions to the /var/www directory (sudo chmod -R g+rw www-data /var/www) should solve your problem.

---

### Post by enchance on 2007-11-16
> **milton1 said:**
> 

```
DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
```
Change the document root to the folder you want to use.

I can't believe even this didn't work! I guess my only chance is to uninstall then install again, right? :( To uninstall do I simply run "sudo apt-get remove..." am I right?

---

