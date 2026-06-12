---
title: "Setting up Apache2 to enable Firefox to open PHP files ?"
date: 2008-10-12
forum: Server Platforms
---

### Post by Browser_ice on 2008-10-12
From a [thread]("http://ubuntuforums.org/showthread.php?t=820956") I had done a while ago, someone told me the reason why my Firefox cannot open an PHP file (it asks me to open it with an HTML editor instead), is that my apache2 is not configured for it.

I had installed apache2 indirectly because I needed MySql for a project. I never used apache2. I had installed the apache2-doc but its no where to be found and I ignore the command to summon up the apache2 doc.

As this is turning into something rather long, I am getting tired of searching for the answer. 

Can someone tell me :
1) Do I really have to configure Apache2 to enable Firefox to display PHP files ?

2) If not, what do I have to do ?

3) If so, what do I have to do ?

---

### Post by R.Bucky on 2008-10-12
I had a similar problem with phpmyadmin. Firefox would not open the front page of phpmyadmin because it was a .phtml file. Here is what I did:

Add these two lines to your apache2.conf located in /etc/apache2 directory
[HTML]AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps[/HTML]

Restart apache with *sudo /etc/init.d/apache2 restart*

I believe that should do it.

---

### Post by Browser_ice on 2008-10-12
> **R.Bucky said:**
> I had a similar problem with phpmyadmin. Firefox would not open the front page of phpmyadmin because it was a .phtml file. Here is what I did:

Add these two lines to your apache2.conf located in /etc/apache2 directory
[HTML]AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps[/HTML]

Restart apache with *sudo /etc/init.d/apache2 restart*

I believe that should do it.


Added the lines and restarted apache2. Firefox still asks me to open php files into an html editor (currently bluefish).

---

### Post by cariboo on 2008-10-12
This may be a dumb question, do you have php5 installed, just because you installed mysql and apache, doesn't mean that you have php support.

Jim

---

### Post by Browser_ice on 2008-10-12
> **cariboo907 said:**
> This may be a dumb question, do you have php5 installed, just because you installed mysql and apache, doesn't mean that you have php support.

Jim

Then do you know how to fix this ?

---

### Post by trailortrash on 2008-10-12
> **Browser_ice said:**
> Then do you know how to fix this ?

```
$ sudo apt-get install libapache2-mod-php5
$ sudo apt-get install php5
```

---

### Post by Browser_ice on 2008-10-22
> **trailortrash said:**
> ```
$ sudo apt-get install libapache2-mod-php5
$ sudo apt-get install php5
```

Both of these were already install.

Can't believe something like this brings so much troubles to enable it.

Anyone know the answer (please read the whole thread before replying) ?

---

### Post by MJN on 2008-10-23
You haven't mentioned if you've actually enabled the PHP module...
 
If not, enable it with **sudo a2enmod php5 **(if the module's not called that leave it off and it'll prompt you)
 
Mathew

---

### Post by bcalder01 on 2008-10-23
Hi MJN,
I tried the a2enmod trick, and although I have php5 installed, I get a "module doesn't exist!" error, and when I leave it off, I don't see anything PHP-related in the module list.

---

### Post by lykwydchykyn on 2008-10-23
First off, this *shouldn't* be this much trouble.  I have setup Apache2 and php dozens of times, and on ubuntu it generally works out of the box withouth any intervention as long as you install apache2, php5, and libapache2-mod-php.  It should be ready to go.

But to answer your questions:

1. Yes.  Firefox, or any other browser, has no clue what to do with a PHP file.  PHP is a server-side scripting language, which means you need a server interpreting the file.  The browser only ever sees the output, which is usually simple HTML/Javascript/CSS. 

2. See 1.

3. From the other thread, sounds like you've got apache2 installed as well as php and the other requirements.  So my question is, are you directly opening the php file in Firefox, or are you connecting to Apache at localhost?  In other words does the URL in the location bar read:
```

file:///home/someuser/somefolder/blah/file.php

```
or does it look more like:
```

http://localhost/somefolder/blah/file.php

```
Sorry if that's a simplistic question, but when something typically straightforward is so much trouble I have to wonder if there isn't a fundamental misunderstanding going on.

---

### Post by Browser_ice on 2008-10-24
> **MJN said:**
> You haven't mentioned if you've actually enabled the PHP module...
 
If not, enable it with **sudo a2enmod php5 **(if the module's not called that leave it off and it'll prompt you)
 
Mathew

I did

---

### Post by Browser_ice on 2008-10-24
Somehow, as soon as I installed phpadmin, it started working ok.

---

### Post by bruski on 2008-10-27
Hmm,

I am having the same problem, have done everything suggested in this thread.

I will continue to fix this and post my solution here.

Bruski.

---

