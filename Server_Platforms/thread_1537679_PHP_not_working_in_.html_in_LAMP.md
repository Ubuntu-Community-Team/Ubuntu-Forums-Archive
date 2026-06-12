---
title: "PHP not working in *.html in LAMP"
date: 2010-07-23
forum: Server Platforms
---

### Post by ridgeland on 2010-07-23
PHP in *.php files works in LAMP.
PHP script within an *.html file is not executed.  Does not display anything but view->source_code shows the <?php ... ?>

localhost/phpinfo.php is
<?php  phpinfo();  ?>
works fine, lots of info

localhost/phpinfo.html is
<html> <head> <title>PHP Info</title> </head> <body>
<?php  phpinfo();  ?>
</body> </html>
Doesn't display anything except the page title is there.  View page source --- shows <?php phpinfo() ?> not the phpinfo() output.

Both files are in /var/www/ with 644 permissions.

$ sudo a2enmod php5
Module php5 already enabled
$ sudo /etc/init.d/apache2 restart
doesn't matter

Cleared Firefox cache - auto clear everything each time Firefox closes - no effect.

php5-cli - php works from command line.

I can upload the phpinfo.html to my web hosting site and it works fine there.

While writing this I thought of new sources and solved the problem.

From the php site - debian notes:
[http://www.php.net/manual/en/install.unix.debian.php]("http://www.php.net/manual/en/install.unix.debian.php")
> If the PHP scripts are not parsing via the web server, then it's likely that PHP was not added to the web server's configuration file, which on Debian may be /etc/apache2/apache2.conf  or similar.

By default php for html is OFF! why?
My fix though was to add
```
    <FilesMatch "\.html$">
	SetHandler application/x-httpd-php
    </FilesMatch>

```
to /etc/apache2/mods-enabled/php5.conf
and restart apache

$ sudo gedit /etc/apache2/mods-enabled/php5.conf
$ sudo /etc/init.d/apache2 restart

---

### Post by bigboy_pdb on 2010-07-23
This thread is marked as solved, but there's no reply so I'm guessing that you've solved it on your own.

I'm going to reply anyway, in case someone else needs help with this and finds this thread. HTML files are processed differently from PHP files. Your PHP code was showing up in the HTML file because PHP isn't part of the HTML specification. Any time that there's PHP code in a file you should use the ".php" extension.

**EDIT:** I reread your post (I hadn't read it thoroughly the first time) and noticed that you wanted to process HTML files using PHP. I'm assuming that it's off by default because an HTML file would be delivered as is whereas a PHP file would need to be processed. There's no point in processing an HTML file as PHP when it doesn't need to be because doing so would waste resources. With the different file extensions you can differentiate between which files are processed by the PHP module, but if you use the same extension then they all must be processed.

---

### Post by ridgeland on 2010-07-23
bigboy_pdb,
I wish I had known that earlier!
[From w3schools:]("http://www.w3schools.com/php/php_intro.asp")
> What is a PHP File?
    * PHP files can contain text, HTML tags and scripts
    * PHP files are returned to the browser as plain HTML 
    * PHP files have a file extension of ".php", ".php3", or ".phtml"

I have simple html files that have very simple <?php which is wrong.  I should rename those files phtml.  A quick test with my problem files shows they open fine as *.phtml.

---

### Post by Vegan on 2010-07-24
for a static document I use .html

for pages with PHP in them I use .php

for java pages I use .java

use the proper extension so that the proper parsers can be used.

---

### Post by klaypigeon on 2010-11-16
Wow, nice catch, I was starting to get pretty frustrated. I cannot believe this is disabled as of version 10.10 on stock Ubuntu server LAMP installs. My troubleshooting was identical, but in seeking a solution I found your post. 
+1

---

### Post by satish_j on 2010-12-10
I came across this thread on searching for the similar issue iam facing.
What i cannot understand is the php code(in html files)is getting parsed properly in Windows environment,whereas it is not working in Ubuntu.
How is it working in **W**AMP??And what setting change can make it work under Ubuntu??
I have already tried creating htaccess file in /var/www and entering the 'AddType' declaration inside it,but that didn't helped..

---

### Post by ridgeland on 2010-12-10
satish_j,

My initial confusion was that my html files ran php fine on my hosting site but not my computer.  The hosting site (bluehost.com) had(/has?) steps required to turn on php inside html.  This is the wrong choice (even if MS does it).  Why?  Because now every html file the server sees must be run through a php processor.  Do it right with a php file ending in php and the server only has to run the php files through a php processor, not every file.  Why waste the server's time running html files that have no php code through a php processor that does nothing with the file?

---

### Post by satish_j on 2010-12-10
> **ridgeland said:**
> satish_j,

My initial confusion was that my html files ran php fine on my hosting site but not my computer.  The hosting site (bluehost.com) had(/has?) steps required to turn on php inside html.  This is the wrong choice (even if MS does it).  Why?  Because now every html file the server sees must be run through a php processor.  Do it right with a php file ending in php and the server only has to run the php files through a php processor, not every file.  Why waste the server's time running html files that have no php code through a php processor that does nothing with the file?
I totally agree with you,but then again,i need to know the reason for this.The very fact that it is working fine in one machine and not in other(both using same server/client softwares)means that there has to be some other setting for enabling it.
I mean,just out of curiosity,i need to know how to enable php in html files..:KS

---

### Post by ridgeland on 2010-12-10
satish_j,
That's what the initial post did.  It explains how I got php to process in html.  Semms like Bluehost did something with .htmaccess or such.  Search their knowledgebase for php, you don't need an account.
[http://helpdesk.bluehost.com/index.php/kb](http://helpdesk.bluehost.com/index.php/kb)

---

### Post by SeijiSensei on 2010-12-10
Go reread the OP's post.  The "problem," if you can call it that, is resolved by adding the SetHandler directive to tell Apache to use the PHP module when sending .html files.  I'm surprised to hear that using the PHP handler for .html files appears to be the default setting in Windows Apache.  It's never been the default in Apache for *nix for as long as I can remember.  It's also not the default on my 10.04 Server installation, so I doubt anything changed with 10.10.

---

### Post by satish_j on 2010-12-13
> **SeijiSensei said:**
> Go reread the OP's post.  The "problem," if you can call it that, is resolved by adding the SetHandler directive to tell Apache to use the PHP module when sending .html files. 

> **ridgeland said:**
> satish_j,
That's what the initial post did.  It explains how I got php to process in html.  Semms like Bluehost did something with .htmaccess or such.  Search their knowledgebase for php, you don't need an account.

> **satish_j said:**
> 
**I have already tried creating htaccess file in /var/www and entering the 'AddType' declaration inside it,but that didn't helped..**

As mentioned in Post6,i have already tried that method w/o success..

---

### Post by SeijiSensei on 2010-12-13
> **satish_j said:**
> As mentioned in Post6,i have already tried that method w/o success..

You need either "**SetHandler**" or "**AddHandler**" depending on where you deploy it in the Apache configuration.  **AddType** won't solve the problem.

---

### Post by satish_j on 2010-12-16
> **SeijiSensei said:**
> You need either "**SetHandler**" or "**AddHandler**" depending on where you deploy it in the Apache configuration.  **AddType** won't solve the problem.

This is also not working..Got any other ideas??

---

### Post by satish_j on 2010-12-24
Solved it..
Added the 'AddType' handler in /etc/apache2.conf and bingo,prob is resolved..:p

---

### Post by ivikas on 2011-05-11
Hi,
    PHP file is not being executed,it is offered as a download.I installed LAMP as  

apt-get install apache2
apt-get install php5
apt-get install mysql-server

I have tried everything like 
sudo a2enmod php5
Module php5 already enabled

even re-installing  libapache2-mod-php5

                     sudo apt-get purge libapache2-mod-php5

                     sudo apt-get install libapache2-mod-php5

I am using public_html directory and it is working fine.MySQL is working perfect and i can access it from the Terminal.

Note:
My computer Hard disk is faulty and i had sent it for a repair.I am using Ubuntu 10.10 as Live CD and installing lamp on it and intent to save the source php files on an external hard-disk.

I have tried the ApachePHPMySQL ubuntu documentation and whole lot of online resource.Nothing works.Any Idea will be appreciated.

Thanks in Advance

---

### Post by trinetra on 2011-09-15
> **ivikas said:**
> Hi,
    PHP file is not being executed,it is offered as a download.I installed LAMP as  

apt-get install apache2
apt-get install php5
apt-get install mysql-server

I have tried everything like 
sudo a2enmod php5
Module php5 already enabled

even re-installing  libapache2-mod-php5

                     sudo apt-get purge libapache2-mod-php5

                     sudo apt-get install libapache2-mod-php5

I am using public_html directory and it is working fine.MySQL is working perfect and i can access it from the Terminal.


Suffering with the same problem. I tried to add "AddType application/x-httpd-php .php .htm .html" or "AddHandler" in .htaccess. None worked. 
Does anybody solved the problem if so please help us. Thanks.


My test html file with simple PHP snippet 
--------------------------------------------------
<html>
<head></head>
<body>
  <h1>
  <?php echo "I LOVE PHP!"; ?>
  </h1>
</body>
</html>

---

### Post by ridgeland on 2011-09-15
Hi trinetra
I don't use LAMP a lot but I tested this for you.
I copied your script and saved it as /Data/Temp/trinetra.html
Then I booted to the LAMP partition (different OS installation)
I opened it with Firefox as file:///Data/Temp/trinetra.html:
nothing.
I copied it to /Data/html/LAMP/trinetra.html and opened it with Firefox as file:///Data/html/LAMP/trinetra.html :
nothing.
I copied it to /Data/html/LAMP/trinetra.php and opened it as 
[http://localhost/trinetra.php](http://localhost/trinetra.php)
and got:
I LOVE PHP!
in big bold letters.

The moral of the story:
You need to save the file as *.php not *.html
You need to have the file in the path of [http://localhost](http://localhost)
You need to open it as localhost not as a file.

If you got those three things right and it still doesn't work then let's work on [http://localhost](http://localhost) and where it points.

---

### Post by trinetra on 2011-09-16
@**Ridgeland**: Thanks a lot for responding and helping me with my problem.....

Few observations that I found after your suggestion......

1. You are correct that I used to open the test.html (trinetra.html) as a file in Firefox and nothing is displayed.
2. But after your direction to open the file with* [http://localhost/test.html](http://localhost/test.html)*
                  I had placed the file in */home/test/public_html/* directory as *index.html*
                  and changed the entries in */etc/apache2/sites-available/default *to point to my new location than */var/www/*
                  and restared the Apache server. But I went into permission/ access problem.
3. Later I tried with default location i.e. I placed the test.html in */var/www *as index.html and restarted the Apache server....
                  Boom that's it, I got "I love PHP" in big letters.

     Though I didn't changed the extension as php, still as html I could  able to open the file in browser. But the catch is instead of opening  the file with absolute path (i.e. the path in your machine), I tried to  open as helped by *Ridgeland* like *[http://localhost/](http://localhost/)* or *[http://localhost/test.html](http://localhost/test.html).*  In both the cases the php snippet got executed without any problem even  if the file extension is html (I wonder why it didn't worked for  "Ridgeland").

     Ridgeland you saved my day ........

---

### Post by ridgeland on 2011-09-16
Have fun...

But... when the server sees a request for a *.php the server sends the *.php through an extra step to process any php code and display the result.  

You can set up the server so *.html is treated like *.php.  In that case every html page even those that do not have php code in them still has to go through a wasted process of checking for php code but not finding any then displaying the result.

My first efforts with *.html failed because the server was set up correctly and did not search *.html for php code.  My hack of processing all *.html for php code wastes server resources.  For my home server that is trivial.  For a large corporation it would matter.

---

