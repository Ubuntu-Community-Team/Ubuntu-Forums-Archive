---
title: "Webserver permissions"
date: 2007-09-26
forum: Server Platforms
---

### Post by Ramthebuffs on 2007-09-26
I have lamp setup on one of my other computers but I don't think its very secure.  I can't remember how I set the permissions.  Now on this computer I have a new install of ubuntu and lamp and I'd like to make it work.  As of now I'm forbidden to access any files inside the /var/www other than the page that says apache is setup and phpmyadmin.  My main concern right now is being able to get into my pages.  After I  get that sorted I'd like it to be secure enough that I can forward my router once a month or so when I'm out of town and be able to access my pages without worrying somebody is crawling all over my computer.

I'm sure this has been addressed before, but the search feature @ ubuntuforums is very tedious and after looking around forever I've decided to post the question.  I'm no 'nix guru but I can get around ok.  I really don't know anything about creating permissions by 775 or 777 or whatever.  If theres already a link on how to do something like this, that would be great.

---

### Post by obrient on 2007-09-26
Not quite sure if this is what you are looking for, but to change permissions on folders you need to use chown. Below is my little cheat sheet that I have set up on a wiki here at home.

Basically I believe that most of your folders on a web server should have a read permission for all but not write or execute. Not totally sure on this myself. I have most of my folders and pages set to 0775 on in /var/www. Hope this helps. One last thing is if you want the webserver to be able to do things to files you will want to make the file part of the www-data group. 

    *  chown to 0777 = (rwxrwxrwx)
    * chown to 0776 = (rwxrwxrw-)
    * chown to 0775 = (rwxrwxr-x)
    * chown to 0774 = (rwxrwxr--)
    * chown to 0773 = (rwxrwx-wx)
    * chown to 0772 = (rwxrwx-w-)
    * chown to 0771 = (rwxrwx--x)
    * chown to 0770 = (rwxrwx---) 

First set of rwx = Owner
Second set of rwx = Group
Thrid set of rwx = All Others.

No a *Nix pro by any stretch :)

---

### Post by Ramthebuffs on 2007-09-27
Thanks for the help, I think I'm sorta starting to get it.  On my old computer with a working lamp the folders are set to drwxr-xr-x and the files are -rw-r--r--

On this computer that I've been trying to get sorted the folders are this drwx-w---- and the files are -rwx-w----

To me this doesn't mean a whole lot I guess.  I'm still getting 403 Forbidden on anything that isn't directly in /var/www.  So /var/www/other gets the error.

---

### Post by fatbastard spice on 2007-09-27
Are you also looking at the securing apache side of the equation? For me it's far more important than the privileges side of the equation.

Sorry if this is a bit patronising, but every now and again i get boring and give more detail than necessary. Anyway on the privileges side of the equation what you're protecting against is someone getting control of the www-data account via an apache vulnerabilty and wrecking your sites. So you don't want to give the www-data account write access to anything more than is necessary.

What i generally do is give ownership to my own user account and then give group ownership to the same sites to the www-data account. Then turn off write access for the www-data user, though there's always a few directories that apache needs write access. Places where you've got uploads, or where your web application is writing logs or other temp/data type stuff. Generally though it shouldn't need write access to individual files, just the odd directory.

So something like this
```
sudo chown fbs -R /var/www
sudo chgrp www-data -R /var/www
sudo chmod 0751 -R /var/www
```

and then
```
sudo chmod 0771 /var/www/***
```
to the odd directory where apache needs write access

Fiddle around with it to meet whatever you want (saycontrolling www-data access by setting the appropriate access to the all others group), but basically you're trying to limit the damage a compromised www-data account can do. Also to be truely paranoid check that the www-data account hasn't been given extra access by being added to other groups (groups www-data).

---

