---
title: "Set www directory under home Apache2"
date: 2015-12-21
forum: Server Platforms
---

### Post by mycomputertips on 2015-12-21
I couldn't find a forum for Servers so I hope my question is allowed here. It's been sometime since I set up a development server locally. I know I ran in to some problems last time as regards how you set up Apache2 to serve pages from a different directory.

Could someone point in the right direction so that after I have installed Apache2 I can set up www under my home directory instead of the default directory.

---

### Post by SlidingHorn on 2015-12-21
From what I'm reading, you'll have to make 2 edits:

*/etc/apache2/sites-available/000-default.conf*
Find "DocumentRoot" and change to the following:
```
DocumentRoot /path/to/new/root
```

*/etc/apache2/apache2.conf*
Find:
```
<Directory /var/www/html/>
Options Indexes FollowSymLinks
AllowOverride None
Require all granted
</Directory>
```

And change the "/var/www/html" to the absolute path of your desired home directory.

Source:  [http://stackoverflow.com/questions/34046055/apache-2-default-document-root-wont-change-ubuntu](http://stackoverflow.com/questions/34046055/apache-2-default-document-root-wont-change-ubuntu)

Note:  You may have to make a change to the virtual server settings in the 000-default.conf file.  See the comments under the answer on the linked page.

---

### Post by SeijiSensei on 2015-12-21
Make sure the directory has read and execute permissions, and the files it contains have read permissions, for the www-data user. The simplest solution is to grant these permissions to all users.

---

### Post by mycomputertips on 2015-12-21
Thank you very much for this. I do remember before the changes it was so simple, but after that I got in to a real mess.

---

### Post by efflandt on 2015-12-22
Something they do at sdf.org (alias freeshell.org) is simply put a symlink in our home directory to our webspace in docroot:```
efflandt@XPS-8100-1404:~$ ssh freeshell
$ ls -l
total 64
-rwxr-xr-x  1 efflandt  arpa  273 Nov 12  2001 cryptme*
-rwxr-xr-x  1 efflandt  arpa  940 Aug 27  2003 crypttest*
lrwx------  1 efflandt  arpa   18 Sep 10 18:43 html@ -> /www/af/e/efflandt
-rwxr-xr-x  1 efflandt  arpa   56 Mar 15  2003 inc-paths*
drwx------  2 efflandt  arpa  512 Apr 29  2014 mail/
-rw-------  1 efflandt  arpa  252 Aug 15  2001 mynewsinfo.txt
-rwx------  1 efflandt  arpa   99 Dec  3  2003 mytest*
-rwxr-xr-x  1 efflandt  arpa  268 Aug 27  2003 pwtest*
-rw-r--r--  1 efflandt  arpa  965 Jul 22  2002 tmp.txt
```Then unless you have your own domain there, the URL for your web dir is: username.freeshell.org/

Or another way it is typically done for user directories is to have a **public_html** directory in their home directory and that URL is typically accessed with a tilde in front of their username like: domain.name/~username/

---

### Post by mycomputertips on 2015-12-23
> **SlidingHorn said:**
> From what I'm reading, you'll have to make 2 edits:

*/etc/apache2/sites-available/000-default.conf*
Find "DocumentRoot" and change to the following:
```
DocumentRoot /path/to/new/root
```

*/etc/apache2/apache2.conf*
Find:
```
<Directory /var/www/html/>
Options Indexes FollowSymLinks
AllowOverride None
Require all granted
</Directory>
```

And change the "/var/www/html" to the absolute path of your desired home directory.

Source:  [http://stackoverflow.com/questions/34046055/apache-2-default-document-root-wont-change-ubuntu](http://stackoverflow.com/questions/34046055/apache-2-default-document-root-wont-change-ubuntu)

Note:  You may have to make a change to the virtual server settings in the 000-default.conf file.  See the comments under the answer on the linked page.

This worked for me, I was able to set up WWW directory under home after changing the .conf files, so thank you for the link, and thanks to everyone else for your advice.

---

