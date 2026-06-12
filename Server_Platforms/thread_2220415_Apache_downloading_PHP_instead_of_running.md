---
title: "Apache downloading PHP instead of running"
date: 2014-04-27
forum: Server Platforms
---

### Post by JohnDillinger43 on 2014-04-27
I've seen this topic posted a number of places, but I though it might be worth posting my own thread since my situation seems different from ones others have posted (and none of the posted solutions have worked).  I installed Apache, MySQL, and PHP on my Ubuntu 14.04 system to do some testing, and had everything working beautifully for a few days.  Then suddenly PHP files started downloading instead of running.  I don't think I changed or updated anything when the problem began, but obviously something's different since I wasn't having this problem before.  I tried reinstalling PHP, making sure .load and .conf were in mods-enabled, etc.  Cleared may cache at every step.  Looking at the conf files everything seems like it should work, but I'm not having any luck getting it to execute the PHP scripts.  Am I overlooking something obvious?  Otherwise I can post apache2.conf if it would be worthwhile.

---

### Post by aysiu on 2014-04-27
Maybe one of these two links might help?
[http://ubuntuforums.org/showthread.php?t=1361019&p=8543964&viewfull=1#post8543964](http://ubuntuforums.org/showthread.php?t=1361019&p=8543964&viewfull=1#post8543964)
[http://stackoverflow.com/questions/18422140/apache-is-downloading-php-files-instead-of-displaying-them](http://stackoverflow.com/questions/18422140/apache-is-downloading-php-files-instead-of-displaying-them)

---

### Post by JohnDillinger43 on 2014-04-28
I did try reinstalling libapache2-mod-php5, and still no luck.  I've done less with the .conf files because I'm not quite sure what I'm doing there.  In fact, I can't even find httpd.conf -- has this been replaced by apache2.conf?  If not, then I might not have everything installed properly.  php.ini is where it should be, but I can't figure out what section of the file to add the relevant lines to (and I'm still unclear as to exactly what they do).

---

### Post by Habitual on 2014-04-29
```
DirectoryIndex index.html index.php
```and bounce?

See [http://httpd.apache.org/docs/current/mod/mod_dir.html#directoryindex](http://httpd.apache.org/docs/current/mod/mod_dir.html#directoryindex)

---

### Post by JohnDillinger43 on 2014-05-04
Thanks -- but I'm still not clear on what these commands are.  Maybe this is a case of RTFM and I just haven't familiarized myself with Apache enough yet, but are these lines in a config file, or shell commands?  If the former, what file, and where is it stored?

---

### Post by JohnDillinger43 on 2014-05-05
I did a little more playing around and found that I CAN get the files to parse if I type the address (e.g., "localhost/test.php") into the browser.  They just won't open if I try to open the files from Nautilus.  Not sure if this is a default program issue or just a fact about how Apache runs things.

---

### Post by kosmokramer314 on 2014-05-06
did you modify the permissions to be executable?  ls -ltrh and check to make sure the .php script is marked at least r-x for the www-data user

example of my settings for a Twitter API php script that is called in the footer of my site.  footer.php is a dynamic element that executes the TwitterAPIExchange.php script..soooooo the Twitter script needs to be executable in my case,  but not the footer.php because it's just being read from and not actually doing anything outside of exposing it's contents.

```
-r-x------  1 www-data www-data 7.7K Oct  3  2013 TwitterAPIExchange.php
drwxrwx---  2 www-data www-data 4.0K Nov  7 21:49 data
drwxrwxrwx  2 www-data www-data 4.0K Jan 18 13:45 config
drwxrwxr-x  5 www-data www-data 4.0K Jan 19 16:57 Scrape
drwxr-xr-x  8 www-data www-data 4.0K Jan 21 11:12 settings
drwxrwxrwx 33 www-data www-data 4.0K Mar 27 15:20 apps
drwxr-xr-x 18 www-data www-data 4.0K Mar 27 16:09 lib
-rw-r--r--  1 www-data www-data 1.4K May  1 17:06 footer.php

```

---

### Post by SeijiSensei on 2014-05-06
> **JohnDillinger43 said:**
> I did a little more playing around and found that I CAN get the files to parse if I type the address (e.g., "localhost/test.php") into the browser.  They just won't open if I try to open the files from Nautilus.  Not sure if this is a default program issue or just a fact about how Apache runs things.

When you open the file with Nautilus, no program is invoked to parse the PHP code.  You see the code itself perhaps in an editor.  To see the result after the code is parsed requires that you view the PHP file with a browser.  Then Apache gets the request and uses the files in libapache2-mod-php5 to identify the code as a PHP script and hand it on to the PHP Apache module for parsing.

---

### Post by JohnDillinger43 on 2014-05-08
Proper execute permissions are set.  So even if I select "Open in Google Chrome", what's happening is that Chrome is being used to open it, but the actual PHP5 mod isn't parsing the code before Chrome tries to open it?  I suppose that makes sense, though it would still be nice to be able to double-click instead of typing in the address every time.

---

### Post by aysiu on 2014-05-08
What appears in the address bar when you open it with Chrome?

Is it something like ```
file:///var/www/nameoffile.php
``` or is it more like ```
http://localhost/nameoffile.php
```?

---

### Post by JohnDillinger43 on 2014-05-10
The former (file://) downloads the PHP file, while the latter ([http://localhost](http://localhost)), which is what I have been using successfully, parses and executes the PHP correctly.

---

### Post by aysiu on 2014-05-10
That's normal behavior.

---

### Post by CharlesA on 2014-05-10
> **aysiu said:**
> That's normal behavior.

Just to expand on that. PHP is a server side language, which means the web server (Apache/Nginx/IIS, whatever) executes it and spits back the output to the browser.

If you are opening the php file as a file and not through the web server, it will show the contests of the file itself and not parse it.

---

### Post by ShadowMerlin on 2014-05-12
I'm having a similar problem with .pl (or .cgi) files.  They are in the ScriptAlias directory, permissions are 755 for both the directory and the file.



Here's the relevant part of the .vhost file:

       <Directory /var/www/clients/client3/web12/cgi-bin/>
               Order allow,deny
               Allow from all
       </Directory>
       ScriptAlias  /cgi-bin/  /var/www/clients/client3/web12/cgi-bin/
       AddHandler cgi-script .cgi
       AddHandler cgi-script .pl




The file runs correctly from the command line, but when I access it via the web, instead of executing, it tries to download.  

I've spent the better part of the last two days trying to figure this out.  Any help will be GREATLY appreciated.

---

### Post by SeijiSensei on 2014-05-13
Have you considered adding [mod_perl]("http://perl.apache.org/") to Apache and using that for .pl files?
```
sudo apt-get install libapache2-mod-perl2 libapache2-mod-perl2-doc
```

What are the .cgi file written in?  Are they binaries or scripts?

---

### Post by JohnDillinger43 on 2014-05-19
Thanks for all the helpful information and advice.  I'm marking this as solved.

---

