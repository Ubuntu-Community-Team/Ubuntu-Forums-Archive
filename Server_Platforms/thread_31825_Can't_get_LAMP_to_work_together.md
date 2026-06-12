---
title: "Can't get LAMP to work together"
date: 2005-05-04
forum: Server Platforms
---

### Post by fiddy_k on 2005-05-04
I've tried multiple times to get Apache2, PHP4 and MySQL to work together with no success. I have all three installed and running, Apache2 and PHP4 are working together, but I can't get PHP to recognize MySQL functions. I've attempted to search all over for a solution and can't seem to get anything to work. Here is my latest code used to install the three:

$ sudo apt-get install apache2 libapache2-mod-php4 libapache2-mod-auth-mysql php4-dev php4-cgi mysql-server

I tried the ubuntu tutorial many times with no success, so I just used apt-cache search to find the above items to install. I uncommented the mysql.so extension line in php.ini as well. Other than that I have made no changes.

If anyone can offer any advise I would greatly appreciate it. This is becoming very, very frustrating but I'm more than willing to do whatever necessary to learn and make it work. Thanks for reading.

---

### Post by Ric_ on 2005-05-06
Can you paste the PHP error that your getting and I'll see if I can help. I have all these working sucessfully. The only difference I did when installing was apt-get install apache2 (prefork or what ever) then installed php4 then installed the modules after. Also a link to a 

<?PHP

php_info();

?>

would be useful.

Just spotted something in your text try an 

apt-get install php4-mysql

---

### Post by LordHunter317 on 2005-05-06
You forgot "php4-mysql" which is why it isn't working.  libapache2-mod-auth-mysql is for doing HTTP authentication off a MySQL database, so you probably don't need/want that.

You shouldn't have to add it, but after installing that package, verify that the line "extension=mysql.so" was added to /etc/php4/apache2/php.ini.  It should be at the very bottom.  If it wasn't, add it.

Then, restart apache and you should be fine.

---

### Post by fiddy_k on 2005-05-08
[QUOTE=LordHunter317]You forgot "php4-mysql" which is why it isn't working.  libapache2-mod-auth-mysql is for doing HTTP authentication off a MySQL database, so you probably don't need/want that.

You shouldn't have to add it, but after installing that package, verify that the line "extension=mysql.so" was added to /etc/php4/apache2/php.ini.  It should be at the very bottom.  If it wasn't, add it.

Then, restart apache and you should be fine.[/QUOTE]


Whenever I try php4-mysql, I get an error:

> sudo apt-get install php4-mysql
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package php4-mysql 

That's the only reason why I didn't use it before. I would assume there's a way to work around this problem, anyone have an idea how? Thanks so much for the feedback so far, each little bit is helping.

---

### Post by LordHunter317 on 2005-05-08
Add the universe repository to your sources.list, run apt-get update and do it again.

---

### Post by fiddy_k on 2005-05-08
[QUOTE=LordHunter317]Add the universe repository to your sources.list, run apt-get update and do it again.[/QUOTE]

Inch by inch... I edited sources.list, uncommented the universe repository lines, ran apt-get update, then tried apt-get install php4-mysql and got this error:

> sudo apt-get install php4-mysql
Reading package lists... Done
Building dependency tree... Done
Package php4-mysql is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package php4-mysql has no installation candidate 

I then used apt-cache search mysql and found a module for php3, but not php4.  ](*,)  So close, yet so far away... 

I don't think installing the php3 module is the right thing to do, but then again I don't know for sure. Did I miss a step somewhere? I used the ubuntu how-to on accessing the universe repository, and I'm using the most recent version of ubuntu.

EDIT: I think i may have got it, not sure yet...

---

### Post by LordHunter317 on 2005-05-08
[QUOTE=fiddy_k]Inch by inch... I edited sources.list, uncommented the universe repository lines, ran apt-get update, then tried apt-get install php4-mysql and got this error:

 

I then used apt-cache search mysql and found a module for php3, but not php4.  ](*,)  So close, yet so far away... 

I don't think installing the php3 module is the right thing to do, but then again I don't know for sure. Did I miss a step somewhere? I used the ubuntu how-to on accessing the universe repository, and I'm using the most recent version of ubuntu.

EDIT: I think i may have got it, not sure yet...[/QUOTE]
 Post your sources.list.  I verified there is a package in universe for php4-mysql, so I know it's there.

---

### Post by fiddy_k on 2005-05-08
OK, I got php4-mysql installed successfully but I'm still getting an error:

Fatal error: Call to undefined function: mysql_connect()

Here is a link to my php.ini file for reference. I uncommented the mysql extension line before, and it didn't do anything, so I re-commented it. Please let me know if I've got something mixed up:

[http://alexkeith.servebeer.com/~rob/phpini.txt](http://alexkeith.servebeer.com/~rob/phpini.txt)

---

### Post by LordHunter317 on 2005-05-08
[QUOTE=fiddy_k]OK, I got php4-mysql installed successfully but I'm still getting an error:

Fatal error: Call to undefined function: mysql_connect()

Here is a link to my php.ini file for reference. I uncommented the mysql extension line before, and it didn't do anything, so I re-commented it. Please let me know if I've got something mixed up:

[http://alexkeith.servebeer.com/~rob/phpini.txt](http://alexkeith.servebeer.com/~rob/phpini.txt)[/QUOTE]
 That line must be uncommented, and you are editing the file /etc/php4/apache2/php.ini, right?   There may be other php.ini files on your system, depending on your configuration, and editing those will not make it work.

Also, after editing php.ini, you must restart (not reload, but restart) apache for anything mysql related to work.

---

### Post by fiddy_k on 2005-05-08
HAHAHAHAHAHAHAAAAA YES, it's working... getting an error but it's a mysql error, so it's working. MAN, you've helped me SO SO much, thank you for everything.

---

### Post by Ric_ on 2005-05-09
If any of you are interested i use the php5 repositries, add these to your apt sources and bingo. I've used their php4 packages in productions, One thing to look out for was that a few times when installing modules such as php4-mysql it failed to update php.ini but that fixable by hand.

deb [http://packages.dotdeb.org](http://packages.dotdeb.org) ./
deb-src [http://sources.dotdeb.org](http://sources.dotdeb.org) .

---

