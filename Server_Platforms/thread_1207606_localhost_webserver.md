---
title: "localhost webserver"
date: 2009-07-08
forum: Server Platforms
---

### Post by timbim on 2009-07-08
I'm using an ubuntu laptop, and I'd like to be able to install a lamp server platform locally so that I can show php/mysql driven sites to clients if I need to visit them without relying on their internet connection to access a server etc.  Could someone please point me in the direction of a guide on how to do this?

Thanks.

---

### Post by TwiceOver on 2009-07-08
Drop to a command line

sudo apt-get update
sudo tasksel

Select the LAMP installation.  This will install Apache, MySQL, PHP for you.

---

### Post by masux594 on 2009-07-08
Read [this post]("http://ubuntuforums.org/showpost.php?p=7520121&postcount=3").. This is a quick install of a lamp server[that i use too =)]!

Sysc, A

---

### Post by Cheesemill on 2009-07-08
> **TwiceOver said:**
> Drop to a command line

sudo apt-get update
sudo tasksel

Select the LAMP installation.  This will install Apache, MySQL, PHP for you.

Or
```
apt-get install lamp-server^
```

---

### Post by timbim on 2009-07-08
Thanks, from there how do I go about setting up the sites, for example one of them needs to run Joomla!, how shoud I configure that?

---

### Post by TwiceOver on 2009-07-08
> **Cheesemill said:**
> Or
```
apt-get install lamp-server^
```

Just reference for those that find this, if you don't do the apt-get update before tasksel, it may fail.

Just an FYI

---

### Post by wojox on 2009-07-08
When you download joomla read the docs here

[http://docs.joomla.org/Beginners#Complete_the_Joomla.21_v_1.5_Quick_Start_Guide](http://docs.joomla.org/Beginners#Complete_the_Joomla.21_v_1.5_Quick_Start_Guide)

---

### Post by timbim on 2009-07-08
Could someone please direct me to the folder into which the localhost system is installed?

Many thanks
Tim

---

### Post by wojox on 2009-07-08
If you mean DocumentRoot it's in /var/www/

---

### Post by timbim on 2009-07-08
So the www folder is the equivalent of the htdocs folder in the guide to joomla!?

I've copied the joomla folder into what I assume is the right place, and navigating to it via localhost/joomla15 gives positive signs, but a phtml file that firefox is powerless to do anything with.  What do I do?

In fact, it seems to be doing this for any page with php in.  How do I fix that?

---

### Post by timbim on 2009-07-19
Thanks for all the previous help, new issue now.  I want to test some AJAX content.  I'm assuming that to do this I'd need to install tomcat or the like?  Is this correct, and how would I go about it?

---

### Post by georgerobbo on 2009-07-19
I find it easier to do by the command line. If your not using Ubuntu server then you will need to replace aptitude to apt-get. 

sudo aptitude install apache2 php5-mysql libapache2-mod-php5 mysql-server phpmyadmin

---

### Post by timbim on 2009-07-19
I've already got a fully functioning LAMP with Apache, PHP, MySQL and PHPmyAdmin.  If I want to test AJAX code on this, will I need tomcat, and if so, how should I do it.

---

