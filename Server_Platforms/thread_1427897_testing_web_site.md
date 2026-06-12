---
title: "testing web site"
date: 2010-03-12
forum: Server Platforms
---

### Post by cliftonbazaar on 2010-03-12
I have just set up my web server for the first time in Linux (used to be Windows 2003).

I have a web site [www.cliftonbazaar.com]("http://www.cliftonbazaar.com"), could someone with experience please check this web site to see if the PHP files are hidden (and therefor my PHP code can't be seen).

If they can be seen then how do I hide the PHP files?

James

---

### Post by sprouty on 2010-03-12
hi,

if you click login, with a invalid user account you get tones of errors, you should try santaze the output. (probably best to do a screen you are not logged in?)

---

### Post by cliftonbazaar on 2010-03-12
Sorry about the errors but it's because that the Mysql database isn't set up (doing it now).

I have asked the wrong question then (and I do apologies), it should of been - can anyone see the directory of my website?
I don't wish public access to my directory as I don't wish for people to see my PHP coded pages.

James

---

### Post by cliftonbazaar on 2010-03-13
Going on form what I asked before -
How do I hide the directory so a visitor can't see all the files?

---

### Post by zander1013 on 2010-03-13
> **cliftonbazaar said:**
> Going on form what I asked before -
How do I hide the directory so a visitor can't see all the files?

i think you just put a period in front of it...

.<dirname>

:)

---

### Post by penguin_patrick on 2010-03-13
> **cliftonbazaar said:**
> Going on form what I asked before -
How do I hide the directory so a visitor can't see all the files?

One thing I've done in the past, is to put an index.html file in every directory.  Then put a redirect to point to the home page.  I think there's a meta tag that will redirect to another url.

* edit * found it: 
```
<meta http-equiv="refresh" content="2;url=http://webdesign.about.com">
```

Set the time to 0 instead of 2, and put in your web root, and it should shoot right to it.
But I think the config file change I mentioned below is a better solution.
* end edit *

Also, there's .htaccess file you can use, that will deny user's ability to view contents of directories.  

I think there's another way, but I can't remember right off hand.

Found a bit that's related:  

```
<Directory "/var/www">
Options -Indexes
</Directory>
```

Research along these lines, to remove indexing capabilities for directories.

If you can't edit the apache2 config files, then you can add the above to the .htaccess and place that in web root, I think.  This will disable dir listing for all directories.

And yes, I can see the dir listing of the images directory, so you'll want to do something to shut that down.

---

### Post by rudy.b on 2010-03-13
> **cliftonbazaar said:**
> Going on form what I asked before -
How do I hide the directory so a visitor can't see all the files?

To keep Apache from showing a file listing of a directory, you can disable the autoindex module by entering the following command:
```
sudo a2dismod autoindex
```Remember to restart your Apache server afterwards.

n.b. to re-enable the module, enter:
```
sudo a2enmod autoindex
```

---

