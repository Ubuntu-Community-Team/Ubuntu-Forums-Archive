---
title: "[SOLVED] Installing PHP 6 and MySQL 5 (with mysqli)"
date: 2008-04-18
forum: Server Platforms
---

### Post by dmick on 2008-04-18
I would like to install the combination of:
-Apache
-PHP6
-MySql5 
The main problem is to enable MySQL (and particularly mysqli) with PHP6.

I succeeded in installing the first two (Apache/PHP6) without (mostly) any problem by following the following guide  [http://www.bencornwell.com/2007/11/18/php-6-installation-guide-for-ubuntu-710-gutsy-gibbon/]("http://www.bencornwell.com/2007/11/18/php-6-installation-guide-for-ubuntu-710-gutsy-gibbon/")

PHP6 and the typical of phpinfo.php worked so it was great. 

I installed MySQL5 with synaptic manager. When I entered the command
```

/usr/local/php6/bin/php --version

```
I get a message telling me that mysql.so could not be found. After some research I installed "php5-mysql" and the related dependencies (being aware of the compatibility problem it could cause but I did not find any other solution) and make PHP6 with the link to MySQL header files:
 ```

sudo ./configure --prefix=/usr/local/php6 --enable-bcmath --enable-calendar --enable-dba --enable-exif --enable-ftp --enable-gd-native-ttf --enable-soap --enable-sqlite-utf8 --enable-wddx --with-apxs2=/usr/bin/apxs2 --with-gettext --with-iconv --with-openssl --with-pcre-regex --with-pdo-sqlite --with-sqlite --with-zlib --enable-zip --with-icu-dir=/usr/local/icu --with-mysql=/usr/bin

```
Then I added in my php.ini a link "extensions=" to all the .so files I found in /usr/lib/php5/20060613+lfs/ . After that I think mysql can work as indicated by the related section on the PHPInfo page:
 ```

mysql
MySQL Support enabled
Active Persistent Links 0
Active Links 0
Client API version 5.0.45
MYSQL_MODULE_TYPE external
MYSQL_SOCKET /var/run/mysqld/mysqld.sock
MYSQL_INCLUDE -I/usr/include/mysql
MYSQL_LIBS -L/usr/lib -lmysqlclient

Directive Local Value Master Value
mysql.allow_local_infile On On
mysql.allow_persistent On On
mysql.connect_timeout 60 60
mysql.default_host no value no value
mysql.default_password no value no value
mysql.default_port no value no value
mysql.default_socket no value no value
mysql.default_user no value no value
mysql.max_links Unlimited Unlimited
mysql.max_persistent Unlimited Unlimited
mysql.trace_mode Off Off

```
 
However a second test of PHP and a call to mysqli failed, and I get the following message when I use the PHP --version command:
```

PHP Warning: PHP Startup: mysqli: Unable to initialize module
Module compiled with module API=20060613, debug=0, thread-safety=0
PHP compiled with module API=20070729, debug=0, thread-safety=0
These options need to match
in Unknown on line 0
PHP Warning: PHP Startup: mysql: Unable to initialize module
Module compiled with module API=20060613, debug=0, thread-safety=0
PHP compiled with module API=20070729, debug=0, thread-safety=0
These options need to match
in Unknown on line 0
PHP Warning: PHP Startup: pdo_mysql: Unable to initialize module
Module compiled with module API=20060613, debug=0, thread-safety=0
PHP compiled with module API=20070729, debug=0, thread-safety=0
These options need to match
in Unknown on line 0
PHP Warning: PHP Startup: PDO: Unable to initialize module
Module compiled with module API=20060613, debug=0, thread-safety=0
PHP compiled with module API=20070729, debug=0, thread-safety=0
These options need to match
in Unknown on line 0
PHP 6.0.0-dev (cli) (built: Apr 17 2008 21:06:00)
Copyright (c) 1997-2008 The PHP Group
Zend Engine v3.0.0-dev, Copyright (c) 1998-2008 Zend Technologies

```

I spent many hours trying to work that out and I am not saavy neither in Linux neither in Apache/PHP/MySQL. I will sincerely welcome any help for this issue.

Many thanks in advance.

Michael

---

### Post by hyper_ch on 2008-04-18
why do you want to use php6?

---

### Post by dmick on 2008-04-18
Well, it's true I am new to PHP but since it's available I was thinking why not start to learn with the newest version (which offers internationalization in which I will be interested for a website).

Ok this post may just be a reason not to use it but the "only" problem seems to be a link to mysqli. If anyone could help me solve this problem it would really be great to be able to start with PHP6. Otherwise I guess I will just give up the idea of starting with PHP6 (not very motivating though!).

I think many people in this forum try hard to solve their problem and avoid going backward to something that works for sure but which is not really what they wanted first. I am one of them and I will greatly appreciate any help!

---

### Post by hyper_ch on 2008-04-18
PHP6 is still in development I tend to think.

> 
Stable Releases

   1. Current PHP 5 Stable: 5.2.5
   2. Historical PHP 4 Stable: 4.4.8

Release Candidates

   1. Current PHP 5 RC: 5.2.6RC5


---

### Post by dmick on 2008-04-18
The guide I mentioned in my post telling how to install PHP6 shows that I am not the only one looking at installing it.

This post was not really about "should I choose to use PHP6?" but more like "I would like to use PHP6, would someone will be willing to help me using it with mysli?"

You don't appear to be in this category and it's not a problem. It's true I am using something maybe I should not be using (at least according to you).

Could you tell me then what are the steps (if any) to clean all what I did so far (mainly typing "make" and "make install" for PHP6, and installing MySQL with Ubuntu repositories)? Thanks for your help.

I would of course much more welcome any solution to install PHP6/MySQL5/mysqli together if someone would be kind enough to help me go through this.

---

### Post by hyper_ch on 2008-04-18
Try this to install mysql:
```

apt-get install mysql-server mysql-client libmysqlclient15-dev

```

But it seems to me that you are not that experienced on linux and specifically not on lamp servers. So I find it a bit irritating that you want to go beyond the boundaries of the package management without actually knowing what to do... that's why I'd say to stick to php5...

---

### Post by dmick on 2008-04-18
Thanks for your help. I already installed those packages and my guess is that MySQL is actually working (and it's marked as enabled in the PhP Info section I quoted) but not mysqli. 

After creating a basic database, a simple mysqli request such as:
```

mysqli_connect('localhost', 'username', 'password', 'example');

```
will return the error
```

Fatal error: Call to undefined function mysqli_connect() in /var/www/mysqli_test.php on line 2;

```

However replacing the "mysqli" request by a "mysql" request as:
```

mysql_connect('localhost', 'username', 'password', 'example');

```
seems to work (display a blank screen)

So the problem really seems to be in enabling mysqli (why do you I want to use mysqli? I just need a friendly people to help me doing it).

PS: the spirit of Ubuntu appears to be to share the power and joy of Linux (together with the tricky and hacking parts of it) with anyone, even the non initiated. It's totally different from the computing intelligentsia you seem to favour   and it gives rise to this fantastic forum where the most savvy help totally newbies (who hardly ever used a text editor) to edit such thing as their xorg.conf file without telling them off with a condescending "what do you want to use a text editor if you never used one?". Thanks for your help anyway.

---

### Post by hyper_ch on 2008-04-18
> **dmick said:**
> PS: the spirit of Ubuntu appears to be to share the power and joy of Linux (together with the tricky and hacking parts of it) with anyone, even the non initiated. It's totally different from the computing intelligentsia you seem to favour   and it gives rise to this fantastic forum where the most savvy help totally newbies (who hardly ever used a text editor) to edit such thing as their xorg.conf file without telling them off with a condescending "what do you want to use a text editor if you never used one?". Thanks for your help anyway.

well, you could also ask a caveman to become a quantum physicist in one day... it's not as drastic here but still same applies... you want to explore challenging stuff without even knowing the basics first... that only leads to troubles.

---

### Post by dmick on 2008-04-18
Sorry I don't want to argue with you. I did not realize me installing PHP6 and MySL5 was equivalent to teach quantum physics to a caveman.

I think we get further away from the initial question. Maybe someone who could trust I may understand some (apparently very sophisticated) Linux commands could help me setup mysqli with PHP6?

P.S.: I guess the previous not so useful posts will deter some people from answering but I am still looking for help to solve this problem

---

### Post by rawb on 2008-04-19
Putting aside the fact that you most definitely shouldn't be using PHP 6 right now, your MySQLi problem is most likely because you didn't configure PHP with the "--with-mysqli=/path/to/mysql_config" option.

---

### Post by dmick on 2008-04-20
Thanks for the help but I already found the solution after not expecting any help from people like hyper_ch. It was simply by adding:
```

--with-mysqli=mysql_config_path
--without-mysql

```
And indicating in the php.ini the link to mysqli.so

Conclusion:
1) It has nothing that challenging to enable mysqli with PHP6
--> Don't have to listen to anyone telling you what is too hard for you
2) The number of people telling what other should do is definitely not as low as one can expect in this forum (2 out of 2 for this thread!)

---

### Post by rawb on 2008-04-20
> **dmick said:**
> Thanks for the help but I already found the solution after not expecting any help from people like hyper_ch. It was simply by adding:
```

--with-mysqli=mysql_config_path
--without-mysql

```

You don't need the --without-mysql bit. mysql and mysqli are two different extensions; both can be used together.

---

### Post by dmick on 2008-04-20
Ok. I'd like to add that your post would have given me the solution if I hadn't found it before so many thanks for your help.

---

