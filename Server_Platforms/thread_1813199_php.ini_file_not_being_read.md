---
title: "php.ini file not being read"
date: 2011-07-27
forum: Server Platforms
---

### Post by bloggermouth on 2011-07-27
I've restarted Apache after making changes to the php.ini file (/etc/php5/apache2) and no changes are reflected in phpinfo() which indicates that I am editing the correct file. I'm quite familiar with the process as I've done it many times before with no issues. 

It is just the weirdest darned thing :confused:

Any help will be greatly appreciated.

---

### Post by sneakyimp on 2011-07-27
You probably already know this, but the PHP.ini file loaded via command line is not the same php.ini loaded when you run a script from the command line. That's one thing to be aware of.

In either case, phpinfo() will report which ini file is being loaded next to the phrase "Loaded configuration file".  On my dev box, this is /etc/php5/apache2/php.ini.

Note also that it says "Scan this dir for additional .ini files " and the dir to be scanned is /etc/php5/apache2/conf.d.  It may be that an INI file in that folder is overriding your default php.ini.

Beyond that, I'm not sure what else to tell you except maybe to force refresh in your browser.  Maybe the result is being cached.

---

### Post by bloggermouth on 2011-07-27
> **sneakyimp said:**
> You probably already know this, but the PHP.ini file loaded via command line is not the same php.ini loaded when you run a script from the command line. That's one thing to be aware of.

In either case, phpinfo() will report which ini file is being loaded next to the phrase "Loaded configuration file".  On my dev box, this is /etc/php5/apache2/php.ini.

Note also that it says "Scan this dir for additional .ini files " and the dir to be scanned is /etc/php5/apache2/conf.d.  It may be that an INI file in that folder is overriding your default php.ini.

Beyond that, I'm not sure what else to tell you except maybe to force refresh in your browser.  Maybe the result is being cached.

Thanks for the reply.

I looked in the other INI files and there are no directives related to what I am changing in the php.ini file. Specifically the max_upload... directive.

I understand that php will run without the php.ini file using the default settings. I also edited the cli ini file to be the same as the /etc/php5/apache2/php.ini file. 

This is my dev machine so I don't allow FF to cache pages on it.

---

### Post by sneakyimp on 2011-07-27
for upload_max_filesize, the issue could be somewhere else.  First, make sure you are entering the correct parameter name. AFAIK, there are no actual PHP parameters starting with "max_upload"

All of these are related to uploads and the docs have some informative notes:
[http://www.php.net/manual/en/ini.core.php#ini.post-max-size](http://www.php.net/manual/en/ini.core.php#ini.post-max-size)
[http://www.php.net/manual/en/ini.core.php#ini.upload-max-filesize](http://www.php.net/manual/en/ini.core.php#ini.upload-max-filesize)
[http://www.php.net/manual/en/ini.core.php#ini.memory-limit](http://www.php.net/manual/en/ini.core.php#ini.memory-limit)

There are others too.

---

### Post by bloggermouth on 2011-07-27
> **sneakyimp said:**
> for upload_max_filesize, the issue could be somewhere else.  First, make sure you are entering the correct parameter name. AFAIK, there are no actual PHP parameters starting with "max_upload"

All of these are related to uploads and the docs have some informative notes:
[http://www.php.net/manual/en/ini.core.php#ini.post-max-size](http://www.php.net/manual/en/ini.core.php#ini.post-max-size)
[http://www.php.net/manual/en/ini.core.php#ini.upload-max-filesize](http://www.php.net/manual/en/ini.core.php#ini.upload-max-filesize)
[http://www.php.net/manual/en/ini.core.php#ini.memory-limit](http://www.php.net/manual/en/ini.core.php#ini.memory-limit)

There are others too.

Apologies for not quoting the proper directive. I used the proper ones and hastily typed in the incorrect one.

---

### Post by sneakyimp on 2011-07-27
If you haven't read those links, you should.  Especially post-max-size.

So what's "not working" ?  Are you checking your phpinfo values and see that your newly specified parameters in php.ini are not taking effect?  Are you actually uploading files and *that* is not working? What are the actual values you have entered?   What's showing up in phpinfo?

Obviously, if you are still having a problem, we need more specific detail, starting with the exact details of your php.ini edits:
* which ini file? (the entire path)
* how are you entering it?  nano?  vi?  gedit?
* do you have permission to edit this file?  AFAIK you need root access to edit php.ini so you should at least be using the sudo command on a linux box or you won't have write permission.
* what is the exact setting you are entering?
* how did you restart apache?
* what is the exact "Loaded Configuration File" reported by phpinfo when you view it in apache?
* can you change *other* settings in the php.ini file or do all changes to the ini file fail to have an effect?
* are you working with Eclipse or some other debugger or are you just opening a browser to localhost?

---

### Post by sirgogo on 2011-07-27
Check your httpd.conf file. Make sure it has the proper directives for PHP support. If your install didn't go 100% smoothly, chances are this is what it screwed up.

---

### Post by bloggermouth on 2011-07-27
> **sneakyimp said:**
> If you haven't read those links, you should.  Especially post-max-size.

So what's "not working" ?  Are you checking your phpinfo values and see that your newly specified parameters in php.ini are not taking effect?  Are you actually uploading files and *that* is not working? What are the actual values you have entered?   What's showing up in phpinfo?

Obviously, if you are still having a problem, we need more specific detail, starting with the exact details of your php.ini edits:
* which ini file? (the entire path)
* how are you entering it?  nano?  vi?  gedit?
* do you have permission to edit this file?  AFAIK you need root access to edit php.ini so you should at least be using the sudo command on a linux box or you won't have write permission.
* what is the exact setting you are entering?
* how did you restart apache?
* what is the exact "Loaded Configuration File" reported by phpinfo when you view it in apache?
* can you change *other* settings in the php.ini file or do all changes to the ini file fail to have an effect?
* are you working with Eclipse or some other debugger or are you just opening a browser to localhost?

I use the terminal command sudo gedit /etc/php5/apache2/php.ini

The settings I've changed are;
upload_max_filesize = 32M
post_max_size = 64M
session.gc_maxlifetime = 3600

I open the files in the browser. PHP is working perfectly except it isn't responding to the changes in the ini file.

phpinfo(); shows /etc/php5/apache2/php.ini as the file being used.
I restart  apache with the following command;
sudo /etc/init.d/apache2 restart

I'm quite sure that I am doing the correct methods. I have even restarted the machine in case something odd is happening with restarting apache. Both Apache and PHP permissions are the same.

---

### Post by bloggermouth on 2011-07-27
> **sirgogo said:**
> Check your httpd.conf file. Make sure it has the proper directives for PHP support. If your install didn't go 100% smoothly, chances are this is what it screwed up.

The httpd.conf file is empty.  I am using the 000-default file in /etc/apache2/sites-enabled directory.

---

### Post by sneakyimp on 2011-07-27
Are you able to make changes to any of the other php.ini settings, for example [memory_limit](http://www.php.net/manual/en/ini.core.php#ini.memory-limit)?

why are you setting post_max_size twice?

Did you install php using the apt-get command?

Also, you didn't answer my other questions.  Are you opening a browser and visiting [http://localhost](http://localhost) or are you typing in some other url?

---

### Post by bloggermouth on 2011-07-27
> **sneakyimp said:**
> Are you able to make changes to any of the other php.ini settings, for example [memory_limit]("http://www.php.net/manual/en/ini.core.php#ini.memory-limit")?

why are you setting post_max_size twice?

Did you install php using the apt-get command?

Also, you didn't answer my other questions.  Are you opening a browser and visiting [http://localhost](http://localhost) or are you typing in some other url?

That was an posting oversight. It is not in there twice. Distractions around here, lol.

I don't recall how I installed the software except to say it was all installed with one command line in terminal. 

I typically use a domain for my machine but I just tested localhost and came up with the same result.

---

### Post by sneakyimp on 2011-07-27
[quote=sneakyimp]* what is the exact "Loaded Configuration File" reported by phpinfo when you view it in apache?
* can you change *other* settings in the php.ini file or do all changes to the ini file fail to have an effect?
* are you working with Eclipse or some other debugger or are you just opening a browser to localhost?[/quote]

I'm not sure if I can help you because this sounds weird, but please give exact answers to the questions.

Also, maybe try **sudo nano /etc/php5/apache2/php.ini** instead.  It'll give you a message if you have any trouble saving the file.

Also, when you open up the php.ini file to make sure your changes were saved, are these changes the previous incorrect values or do your changes get saved properly?

I just did this:
```

sudo nano /etc/php5/apache2/php.ini

```
change upload_max_filesize to this:
```

upload_max_filesize = 8M

```
then restart
```

sudo /etc/init.d/apache2 restart

```

When I look at my phpinfo file at [http://localhost/phpinfo.php](http://localhost/phpinfo.php), the change has taken place immediately.

Also worth noting on my machine is that the directory /etc/php5/apache2/conf.d is FULL of ini files:
```

user@host:~$ cd  /etc/php5/apache2/conf.d 
user@host:/etc/php5/apache2/conf.d$ ls -l 
total 88
-rw-r--r-- 1 root root  54 2011-05-02 16:09 curl.ini
-rw-r--r-- 1 root root  50 2011-05-02 16:09 gd.ini
-rw-r--r-- 1 root root  17 2010-06-03 00:47 idn.ini
-rw-r--r-- 1 root root  60 2010-07-23 23:06 imagick.ini
-rw-r--r-- 1 root root  54 2011-02-22 09:28 imap.ini
-rw-r--r-- 1 root root  58 2011-02-22 09:18 mcrypt.ini
-rw-r--r-- 1 root root 229 2010-12-13 10:48 memcache.ini
-rw-r--r-- 1 root root  55 2011-06-29 19:09 ming.ini
-rw-r--r-- 1 root root  57 2011-05-02 16:09 mysqli.ini
-rw-r--r-- 1 root root  56 2011-05-02 16:09 mysql.ini
-rw-r--r-- 1 root root  52 2011-05-02 16:09 pdo.ini
-rw-r--r-- 1 root root  60 2011-05-02 16:09 pdo_mysql.ini
-rw-r--r-- 1 root root  62 2011-05-02 16:09 pdo_sqlite.ini
-rw-r--r-- 1 root root  58 2011-05-02 16:09 pspell.ini
-rw-r--r-- 1 root root  58 2011-05-02 16:09 recode.ini
-rw-r--r-- 1 root root  54 2011-05-02 16:09 snmp.ini
-rw-r--r-- 1 root root  60 2011-05-02 16:09 sqlite3.ini
-rw-r--r-- 1 root root  58 2011-05-02 16:09 sqlite.ini
-rw-r--r-- 1 root root  54 2011-05-02 16:09 tidy.ini
-rw-r--r-- 1 root root 477 2011-06-29 21:23 xdebug.ini
-rw-r--r-- 1 root root  59 2011-05-02 16:09 xmlrpc.ini
-rw-r--r-- 1 root root  52 2011-05-02 16:09 xsl.ini

```

Any one of these ini files could have a conflicting value. Fortunately, on my system it does not.

---

### Post by bloggermouth on 2011-07-27
I did what you suggested and no change. 

I looked through the other ini files in the conf.d directory and there are no anomalies. I don't have as many as you do. Just the basics with GD, cURL etc.

I really appreciate your help despite the result.

---

### Post by sneakyimp on 2011-07-27
Did the changes you made in the file stick, or do they disappear the moment you close the file?  I'm trying to determine if you are somehow failing to actually save the changes to the file.

If you make the changes to the file and save them successfully, then one of those other INI files could well be overriding your change.  There's also the possibility that you have set values for these parameters *in two different places in your php.ini file* and the second one is overriding your first change.  

Beyond that, I'm not sure what to say.  Good luck.

---

### Post by bloggermouth on 2011-07-27
> **sneakyimp said:**
> Did the changes you made in the file stick, or do they disappear the moment you close the file?  I'm trying to determine if you are somehow failing to actually save the changes to the file.

If you make the changes to the file and save them successfully, then one of those other INI files could well be overriding your change.  There's also the possibility that you have set values for these parameters *in two different places in your php.ini file* and the second one is overriding your first change.  

Beyond that, I'm not sure what to say.  Good luck.

The changes are sticking, always have. That is why I am so perplexed. It seems that PHP is ignoring the ini file altogether.

---

### Post by sneakyimp on 2011-07-27
Have you tried renaming the ini file to see if php/apache complains? If you rename php.ini to php.ini.BAK and restart apache, then do things look different in your apache phpinfo ?  If not, then something is weird:  either you are accessing a domain that is mapped to some other machine or apache is lying to you about which php.ini it is loading.

If things go look different in php.ini then you know that you have the right file. Change its name back to php.ini and restart apache again.  In that case, you might be entering your change in php.ini and the same settings are re-set later by another directive.  You have to make sure that each directive is set once and only once -- and this includes all those ini files in conf.d too.  Did you try searching them?

---

### Post by paulernest on 2011-07-31
I've got an identical problem using Lucid with php 5.3.2, and a workaround which works but is a bad solution.

phpinfo() is reporting Loaded Configuration File /etc/php5/apache2/php.ini

When I rename /etc/php5/apache2/php.ini to /etc/php5/apache2/php.ini.old  and then restart apache (using: sudo service apache2 restart),  phpinfo() still runs, but this time gives a blank against Loaded  Configuration File, so I must have the right file.

The only other differences between the output of phpinfo() are the following:

With php.ini named properly

[LIST]
[*]Loaded Configuration File /etc/php5/apache2/php.in
[/LIST]
 With php.ini named as php.ini.old

[LIST]
[*]Loaded Configuration File (none)
[/LIST]
 The execution time and remote port also changed, but I think these  changes every time the script is run so they shouldn't matter.

It appears as though every within /etc/php5/apache2/php.ini is being completely ignored and complied in defaults are being used.

I've found that by creating the new file /etc/php5/conf.d/test.ini and  putting the directive I require in it (upload_max_filesize), then the  directive is honoured after an apache restart.

I'd really like to get to the bottom of why directives in the php.ini  file area being ignored. Any advice would be gratefully received.

---

### Post by paulernest on 2011-07-31
Just done a test and might have a little more information for someone else to go on.

If I rename /etc/php5/apache2/php.ini as /etc/php5/apache2/php.ini.bac
then create a new /etc/php5/apache2/php.ini, which contains nothing apart from the directive I want to set, then when I restart apache the directive is honoured.

---

### Post by paulernest on 2011-07-31
Ok, I've found out what the problem was (at least in my case). At some point I had introduced a syntax error in the php.ini file right at the beginning, and this was preventing any further directives from being read. Once the error was fixed, my upload_max_filesize directive was good to go.

I figured this out by realising that if I placed the directive I wanted to at the beginning of the file then it was honoured, so I gradually moved it down the file until it stopped working and that led me to spot the error.

I'm not going to admit what the syntax error was, cause that's just too embarrassing!

I hope this is of use to someone.

---

### Post by sneakyimp on 2011-07-31
Nice detective work. Adding your directives at the very beginning of the file is probably not the best idea since these directives may already exist in the file further down.  If you set a directive to one value on the very first line of your file and a different value at line 500, then the line 500 value will probably be what gets used.  I suspect this could be bloggermouth's problem -- Or perhaps these ini settings get set in one of the other myriad INI files he has.

The right approach to setting values is to find out if they are already being set somewhere and changing the value there.

---

### Post by paulernest on 2011-08-01
I guess a more systematic way to try and pin this problem would be:

[LIST=1]
[*]In /etc/php5/apache2 rename both php.ini file and conf.d link to php.ini.old and conf.d link.old
[*]Make sure there are no php directives being set in any of the apache configuration files; main file, conf.d files, and virtual host conf files.
[*]Make sure that there are no .htaccess files setting php directives
[*]create your own /etc/php5/apache2php.ini file with nothing but the directive you want to change.
[*]Restart apache
[/LIST]
If phpinfo() now reports your directive as being set correctly, then gradually bring back in all the other configuration files until you find out where either a) the directive is being overridden, or b) where you have a syntax error.

It seems that a syntax error at a point in a file will prevent all directives below that point being read. Directives lower in a file will overrule the same directive above them. Therefore, if you add the directive at the top of the file and it fixes you problem, then it's likely to be a syntax error, but if you add the directive at the bottom of the file and it fixes your problem, then it's likely that that directive is already being set above.

---

### Post by sneakyimp on 2011-08-01
That sounds like a pretty good approach.

---

### Post by bloggermouth on 2011-08-03
As it turns out, the issue was syntax related. #-o

Thanks for the help guys!!

---

### Post by josefnpat on 2012-11-01
I recently had this very same issue, and wanted to document an easy way to check the syntax of a php.ini file;

Basically, php uses the parse_ini_file() command to parse the php.ini, but doesn't actually spit errors out when you do a service apache2 restart.

So, open up an interactive session in php (`php -a`) and use `parse_ini_file()` on the `/etc/php5/apache2/php.ini` file (or wherever you've got your php.ini file) to get a better idea of what happened.

```
x@x:/etc/php5/apache2$ php -a
Interactive shell

php > parse_ini_file("php.ini");
PHP Warning:  syntax error, unexpected '|' in php.ini on line 111
 in php shell code on line 1

```

What I noticed here is I un-commented a line thinking it would change standard error reporting, and not realizing it was just a comment, as opposed to valid syntax.

---

