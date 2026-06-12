---
title: "Webserver?"
date: 2006-09-05
forum: Server Platforms
---

### Post by emptycs on 2006-09-05
How do I install the whole webserver package?

Apache, PHP, MySQL, phpMyAdmin... ?

---

### Post by Titus A Duxass on 2006-09-05
There are many ways!

Use the alternative CD and do a basic install then add your packages.

On some CDs there is a LAMP option, that's the one for you.

You have to search around and find the right CD.

---

### Post by emptycs on 2006-09-05
How do I install these thing manually?

---

### Post by Titus A Duxass on 2006-09-05
Manually you will first have enable the repositories in your sources.list file.  Do this by removing the # from the lines that look like URLs.

Then do:

sudo aptitude update
sudo aptitude upgrade

That will get you an upto date system.

Now install your packages with:

sudo aptitude install packagename

Try to get into the habit of using aptitude and not apt-get, aptitude is a little bit smarter than apt-get.

---

### Post by emptycs on 2006-09-05
> **Titus A Duxass said:**
> Manually you will first have enable the repositories in your sources.list file.  Do this by removing the # from the lines that look like URLs.

Then do:

sudo aptitude update
sudo aptitude upgrade

That will get you an upto date system.

Now install your packages with:

sudo aptitude install packagename

Try to get into the habit of using aptitude and not apt-get, aptitude is a little bit smarter than apt-get.

OK? How would this help me manaully install my webserver? Next time give the full edit command to edit sources.list

---

### Post by Titus A Duxass on 2006-09-05
"OK? How would this help me manaully install my webserver? Next time give the full edit command to edit sources.list" - If you do not follow this and cannot edit your sources.list without guidance then maybe you are not ready for a server install.

Do a search for sources.list and you will find lots of threads.
Do some reading.
Then do a search for aptitude, do some more reading.
Then do a search for server install, again do some more reading.

I will ignore your rather rude demand for more information just in case your mother tongue is not English.

---

### Post by emptycs on 2006-09-05
I already know how to edit my sources.list the only reason I am asking how to install webserver is because I seem to failed to install apache on ubuntu.

---

### Post by Titus A Duxass on 2006-09-05
What fails exactly?

Have you thought about doing a LAMP installation?  That has exactly what you require for your server.

---

### Post by emptycs on 2006-09-05
> **Titus A Duxass said:**
> What fails exactly?

Have you thought about doing a LAMP installation?  That has exactly what you require for your server.

I'm trying to install the webserver and stuff with gui. If I fail at this I'll just install the lamp then install ubuntu-desktop

---

### Post by emptycs on 2006-09-05
Sorry for the double post but how do I put my files in my parent directory?

[http://75.7.21.48](http://75.7.21.48)

---

### Post by Titus A Duxass on 2006-09-05
What do you mean, put the files in the parent directory?

---

### Post by emptycs on 2006-09-05
I would like to add a index.html but I don't know how to.

---

### Post by Crayoneater on 2006-09-05
you have to put the index.html file in /var/www/

or wherever you have set up as your root directory

---

### Post by emptycs on 2006-09-05
I don't have write permission?

---

### Post by hagen00 on 2006-09-05
[http://www.catb.org/~esr/faqs/smart-questions.html]("http://www.catb.org/~esr/faqs/smart-questions.html")

---

### Post by sysops on 2006-09-05
If you have your sources.list with the right entries, then you can search for packages among the many repositories using aptitude.

$ sudo aptitude update

$ aptitude search apache

or alltogether 

$ aptitude search "apache|php|mysql"

Then choose from the list of results the packages you would like to install.

$ aptitude install apache2 php5 mysql-server-5.0 mysql-client-5.0

etc. Any dependancies needed will be automatically queued for install and you will be notified before you are allowed to continue.

---

### Post by alecjw on 2006-09-05
Root has write access to /var/www/, log on as root or use sudo.

---

