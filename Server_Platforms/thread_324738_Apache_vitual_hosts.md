---
title: "Apache vitual hosts"
date: 2006-12-24
forum: Server Platforms
---

### Post by involutaryhaxor on 2006-12-24
Alright, so I have no clue what I'm doing with this here. I would need step by step instructions for how to do this. 

I already have a website on my ubuntu server, perpetualapocalypse.com

If I could, I would want to leave that alone and add another virtual site, stewartcolbertcon.com

Thanks in advance.

---

### Post by d.j.schroeder on 2006-12-24
Is this Apache 2.0?  I am assuming the answer is yes, if not disregard the rest of my post.  Also, backup any files before you change them, just in case.

Look in /etc/apache2/sites-enabled there should be 000-defualt.  Open it up and take a look.  I am no expert here, but I made mine do what you want to do, I can't remember what my default looked like exactly, and I didn't follow my own "make a backup advice".  You want it to start with NameVirtualHost *.  Then copy from <VirtualHost *> all the way to </VirtualHost> and paste it at the end.  You are setting up to run two name based virtual hosts here.

Then at the beginning of one container you will have > ServerName perpetualapacolypse.com and for the other [HTML]ServerName stewartcolbertcon.com[/HTML].  Then in each container you need to specify where to find the files:  > DocumentRoot /var/www/whateverfolderyouputthemin

If I'm remembering right that's all you should have to do to get it to work.  Obviously, there are a bunch of other things in there you can configure, but you shouldn't need to to make it work.

Good luck, hope it helps.

---

### Post by chrisfay on 2006-12-24
For name based virtual hosting, you need to make sure you convert your first domain into a virtual host as well. I would create two files within the folder sites-available, one for your current domain and another for your new one. Copy the following info into each file, replacing your own information obviously. After you have created the two files, you use the command a2ensite to symlink them into sites-enabled. They will not be active until linked. So:

```
sudo vi /etc/apache2/sites-available/perpetualapocalypse.com
```
This will open up a new file called perpetualapocalypse.com for editing. Input the following into the new file:

```
NameVirtualHost *

<VirtualHost *>
DocumentRoot "/var/www/yoursitefolder"
ServerName perpetualapocalypse.com 
ServerAlias www.perpetualapocalypse.com
<Directory "/var/www/yoursitefolder/">
Allow from all
Options -Indexes
</Directory>
ServerAdmin youremail@domain.com
LogLevel emerg
</VirtualHost>
```

Type:
```
:wq
```
...to save the file

Then do the same with your second domain, create the file, input the same info as above, but with your domains specific info. When that's done, issue the following command:

```
sudo a2ensite perpetualapocalypse.com
``` 
...as stated before, this will symlink your virtual host to sites-enabled, and name based virtual hosting would then be functional. Do the command for the second file as well.Remember to restart Apache2 before continuing.

```
sudo apache2ctl restart
```

.....assuming Apache2 for these directions.

---

