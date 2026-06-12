---
title: "Able to login via ftp-ssh but unable to upload files"
date: 2009-01-02
forum: Server Platforms
---

### Post by johndoe75 on 2009-01-02
For everyone's info: I'm a newbie!

Yesterday I've decided to try and set up a home server myself and see what it's like to host my own website instead of hosting it somewhere else.

I've been using core-FTP for years to upload files to my online webspace. So Yesterday i've succesfully installed Ubuntu Server edition 8.10 with a lamp server,SSH server,ftp server and webmin.

So tought I could login like I normaly would when making a new connection to a server via ftp or ssh.

Filled in the username that i've set up when installing Ubuntu, gave in the correct password, filled in  my ftp.myhostname.nu
Now I'm able to navigate thru all my directories, but I'm unable to upload anything.

I've been googling around and did a search here too, but couldn't find a solution? 

What did I forget? Anyone knows a good tutorial that I can follow?

---

### Post by my_key on 2009-01-02
Are you sure your user has write permissions to the directory you are trying to upload? What program do you use to upload your files and in what directory are you uploading files? Does the program give you an error message?

---

### Post by johndoe75 on 2009-01-02
My_key,

This is the only account I have since install. It is the account I was ordered to create when installing the Ubuntu server edition.

The ftp app is core FTP @ [www.coreftp.com](www.coreftp.com)
Hmm, I've been using this app for years now and on the same Ubuntu server that my webshoster is running on. 

I'm trying to upload in my webroot var/www/.. etc
Where can I verify that my account has upload privileges.
Actualy it's strange that my 'main account' doesn't have any privileges :S

The error is I believe on the top of my head 'permission denied'.

Thank you for your quick response

---

### Post by my_key on 2009-01-02
All ftp programs I encountered can check permissions, mostly right-click on the folder www in /var and click on properties or permissions,...

You can also log in via ssh and:

```
ls -al /var
```

Then read: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
This will teach you how to interpret the drwxr-xr-x sequence you see next to www.

Note that it's NOT a good idea to make you www directory world writable for security reasons. You will probably need to opload the files here as the user which owns /var/www or as root and than finish by giving the user www-data the permissions to read these file and folders.

Which user do you use to log in over ftp? I hope it's a normal user and not root?

Suppose the user's name is john.

Over ssh while being in /var/www:
```
sudo mkdir website
sudo chown john website

```
This makes john owner of the website dir and you can upload files here.

After uploading you can give ownership to Apache (user www-data):
```

sudo chown www-data -vR /var/www/website
```

And check permissions to see none of the files are world writable, because that's generally a bad thing.

Good luck with your server!

---

### Post by my_key on 2009-01-02
If your installing a specific application like e.g. drupal, there might be a bit more involved. Perhaps you need to tell apache to interpret phpfiles with modphp, perhaps you need to set up a database. Google for "applicationname ubuntu server" to find lots of tutorials.

If you find administering your own server a bit daunting, you can also install webmin. I've never used it, but I've heard good things about it.

Tip: the linuxreality podcast has a nice home server series with one episode dealing with apache. Chess Griffin, the author of that show, always does a great job about explaining difficult things very simply.

---

### Post by Iowan on 2009-01-02
> **my_key said:**
> ... You will probably need to opload the files here as the user which owns /var/www or as root and than finish by giving the user www-data the permissions to read these file and folders.By default, root owns */var/www*.  One option mentioned in [this]("https://help.ubuntu.com/community/ApacheMySQLPHP") help page is to relocate the Document Root.

---

### Post by johndoe75 on 2009-01-02
No I haven't enabled the 'Root' account. I'm using sudo for everything that needs root access.

I have no second account, which means that there is only one account that I assume has all privileges since this is the one that was created in the 'install' procedure of the Ubuntu server OS.

I have access to everything with this 'main' account,well exept for the mysql databases thru Webmin, but that's another story I guess :S

I'm starting to think that I'm missing a configuration step somewhere in the [Ubuntu Server Guide]("https://help.ubuntu.com/8.10/serverguide/C/index.html")..
But I'm stuck at this point because I don't know where to start looking from this point on.

Maybe that link about chmodding comes in handy. I'll have a look at it as soon as I get home from work.

Cheers!

---

### Post by my_key on 2009-01-02
It doesn't matter if you have not enabled the root account (it's not advised to do that anyway). Files/directories are still be owned by root (most of your system's dirs are in fact). When you issue commands as sudo you act as if you were root.
sudo = Super User DO

I can't seem to find anything in that link that Iowan posted that explains relocating the document root, but you could in fact also do that. You can also work with a symbolic link to a directory in the user's home directory or with [per user web dirs]("http://httpd.apache.org/docs/2.2/howto/public_html.html"). If your the only one using your server, there is no harm in using the method I discribed above. Which is the same as the 
```
sudo chown -R $USER:$USER /var/www
``` from the link Iowan posted.

---

### Post by Iowan on 2009-01-02
My bad... When setting up multiple virtual hosts, you'd probably want to put documents in different places.  The help page (under 5.2 Virtual Hosts) mentions how to set up a new virtual host with Document Root and Directory in different places.  You could use this information to move your current website targets, but the data would need to be manually moved.

---

### Post by johndoe75 on 2009-01-02
> **my_key said:**
> All ftp programs I encountered can check permissions, mostly right-click on the folder www in /var and click on properties or permissions,...

You can also log in via ssh and:

```
ls -al /var
```

Then read: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
This will teach you how to interpret the drwxr-xr-x sequence you see next to www.

etc...

Suppose the user's name is john.

Over ssh while being in /var/www:
```
sudo mkdir website
sudo chown john website

```
This makes john owner of the website dir and you can upload files here.

After uploading you can give ownership to Apache (user www-data):
```

sudo chown www-data -vR /var/www/website
```

And check permissions to see none of the files are world writable, because that's generally a bad thing.

Good luck with your server!

This is absolutely **working**! Cheers guys:popcorn:
Pff.. this saves a lot of research, coffee and headaches.

---

