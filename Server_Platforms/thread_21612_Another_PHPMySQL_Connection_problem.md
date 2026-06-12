---
title: "Another PHP/MySQL Connection problem"
date: 2005-03-23
forum: Server Platforms
---

### Post by idude on 2005-03-23
This may be a simple fix... 

I have PHP4 and Apache2 installed directly from Synaptic and am having an enormous amount of difficulty getting DB connectivity through a PHP file.

The error I am receiving is:
Fatal error: Call to undefined function: mysql_connect() in /home/idude/www/test.php on line 6

Line #6:
mysql_connect(localhost,$username,$password);

The script is a generic PHP DB testing script to pull info.

To make sure it wasn't the script, I tried to install WordPress blog software which I've used on various other linux builds and when I try to run that it says:
"Your PHP installation appears to be missing the MySQL which is required for WordPress."

Sooo.. I think PHP is just not getting to MySQL at all...

I am fairly new to setting up Linux servers, but I have setup PHP,MySQL & Apache on another server without any problems like this.

TIA...

-iDude

---

### Post by jdonnell on 2005-03-23
did you do this?
```
sudo apt-get install php4-mysql
```

---

### Post by idude on 2005-03-24
Yep and it says 
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package php4-mysql

---

### Post by idude on 2005-03-24
Nevermind tho, I went back to Warty (I was on Hoary), and I installed MySQL, then PHP4, then apache and did some configuration to get the PHP4 to work on Apache...  

But, I did use your command again after going into Synaptic and adding the extra two  "Universe" repositories which were not checked by default.  After checking them, it found the php4-mysql package fine.

Sooo.... Overall, I'm sure everything would've worked fine under Hoary, but I wanted to use Warty since it's a completed build.  I may upgrade to Hoary when it comes out full in April.  

My site is now up, moved over from Linspire 5.0, at [http://www.idude.org](http://www.idude.org)

Thanks for the help.

---

### Post by dataw0lf on 2005-03-24
Looking good, and congratulations on moving from LinSpire.

---

### Post by BloGTK on 2005-03-25
[QUOTE=idude]Yep and it says 
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package php4-mysql[/QUOTE]

For Hoary, php4-mysql is in universe, so you need to add a universe repository into your sources.list in order to install php4-mysql.

---

### Post by idude on 2005-04-04
[QUOTE=dataw0lf]Looking good, and congratulations on moving from LinSpire.[/QUOTE]

Still like Linspire for Desktop for standard consumers... very friendly and is easy to install and use... I personally think the people I've tested Linspire on would be clueless trying to install Ubuntu, those people have no OS knowledge.   Linspire has done a lot of nice things...

But for those of us who are familiar with Linux already, I think Ubuntu is a godsend.  It's a very clean, powerful build on 1 CD.  I love it.  Sometimes I forget I'm even on my server when using Ubuntu.

So basically, Linspire for Newbies, Ubuntu for the rest. :-)

---

