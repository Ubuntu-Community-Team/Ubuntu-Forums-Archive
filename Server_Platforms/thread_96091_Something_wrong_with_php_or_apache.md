---
title: "Something wrong with php or apache"
date: 2005-11-28
forum: Server Platforms
---

### Post by Insane on 2005-11-28
I cannot seem to view a php fiel in my browsr when i go to localhost....

I can view HTML files and I have php5 installed....and every module or whatever you want to call it that is availible installed....
When I try to access a file, it asks me whether I want to download it. So, I am stuck.....
Pleasse help...

---

### Post by Insane on 2005-11-28
Oh..I also have apache 2 installed.

---

### Post by Insane on 2005-11-28
Ok, now, after I restarted my PC, I now can access the php file, but it only tells me about the wonderful internal server error..

Please can someone help.

---

### Post by Insane on 2005-11-28
Right, I re installed everyhting that has to do with apache, including apache2 itself, and I am back to the thign where the browser wants to download the php file instead of opening it. 

This is the phpinfo.php file...

---

### Post by goneskiing on 2005-11-28
Yeah, join the crowd - we've lost days on this.  Something is really wrong.  I'm installing RH4 now to see if that works - waiting for Dapper to see if that works does not cut it.

---

### Post by az on 2005-11-28
[QUOTE=goneskiing]Yeah, join the crowd - we've lost days on this.  Something is really wrong.  I'm installing RH4 now to see if that works - waiting for Dapper to see if that works does not cut it.[/QUOTE]


Let me save you a few more days work:

[https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)


Also, make sure that you configure your php5.load

DirectoryIndex index.php
AddType application/x-httpd-php .php .php5
AddType application/x-httpd-php-source .phps

[https://wiki.ubuntu.com/PHP5Installation](https://wiki.ubuntu.com/PHP5Installation)

---

### Post by Insane on 2005-11-28
ok, it still does nto work. I unstalled everything php, mysql and apache related, and followed the guide completely....

I am getting this error when trying to set the mysql root pass:

Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

and I checked, and there is NOTHING in the mysqld folder... :'(

---

### Post by goneskiing on 2005-11-28
Thanks for the wiki pages - this is finally progress (though things are still not working)

1) yes, these wiki pages need to be consolidated to just one page (and then do get rid of the others - too damn confusing)  Can someone volunteer to take the lead here ?  

2) Should add postgresql to the page along with MySql 

3) re Securing Apache
Need to address firewall issue here - if I'm running default firestarter will I have a problem with localhost ?  (Doesn't seem to since when I try "firefox localhost" I get the /var/www directory 

4) re php5.load (/etc/apache2/mods-available/php5.load)
what about mods-enabled (I don't see any php load file link here - it would seem there should be one ?)  If so, how ?

5) Meanwhile my phpinfo test file now gives error - something about not able to run)

6) I'm also having big trouble with Postgresql with connecting - just won't accept my user and password (I'll try more on this to pin it down).

---

### Post by Efrain Valles on 2005-12-05
I have the same Problem.... 
My firefox keeps trying to download the php... have you guys made any progress... ?? I´ll try to keep reading and post anything I discover:???:

---

### Post by nemik on 2005-12-05
same here for some reason it tries to download info.php but works for other things. go into your var directory and just make a test45.php in there put some random echo statement. make sure the permissions for your new php45.php are set to 755. then try to load it. should work fine.

---

### Post by goneskiing on 2005-12-05
I couldn't get any breezy packages to work - Follow the tutorial on installing apache and php5.1 - it will install using configure and make - this works (plus you getting the newer php).

---

### Post by svyatogor on 2006-02-01
have exactly the same problem. was working fine until I decided to install php5+apache2 from dapper branch on my breazy.

---

### Post by MJN on 2006-02-01
Try adding **AddType application/x-httpd-php .php** and **AddType application/x-httpd-php-source .phps **to mods-available/php5.conf (_not_ inside the <Files *.php> container) and comment out **SetOutputFilter PHP **and **SetInputFilter PH** (these _are_ inside <Files *.php>), then restart Apache.
 
Any joy?
 
If so, it's all to do with Apache telling the client what the MIME type of the file is.... without the above directives Apache doesn't know it's a PHP script and hence just sends it as whatever the default is (text/plain I seem to recall) thus the client follows this and displays the code on screen...
 
Mathew

---

### Post by jeffdavis on 2006-02-08
MJN wrote: "Try adding AddType application/x-httpd-php .php and AddType application/x-httpd-php-source .phps to mods-available/php5.conf (not inside the <Files *.php> container) and comment out SetOutputFilter PHP and SetInputFilter PH (these are inside <Files *.php>), then restart Apache."

For the record, something very similar worked on Hoary Hedgehog with php4 and apache2.  I went to /etc/apache2/mods-available/php4.conf and uncommented the following lines (removed the # signs at the start of the lines):

  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps

Restarted apache, and now it works fine.  Thanks, MJN!

---

### Post by deadgoon on 2006-02-08
I've found another possible solution, at least it seemed to work for me.

I went through all of the suggestions in this thread and many others.  I installed, de-installed, etc, etc, until I was blue in the face.  I was still have the same issue.. download dialog on my index.php file.  I tried it in Konquerer and Firefox both, same thing.

THEN I finally remembered the #1 rule of Unix... check your file permissions.  None of the files were set to execute.  I did a quick chmod 755 * in my public_html directory and it worked in Konquerer.  It still didn't work in Firefox.  I cleared the cache and tried again.  It worked!!!

Hope this helpes someone out there and I hope it keeps working for me.  I'm tempted to do a reboot to make sure.

---

### Post by schmidty on 2006-02-19
With the Postgresql problem try using the connection string of:

pg_connect("dbname=database user=user");

without the localhost or port switches...this worked for me.

Schmidty

---

