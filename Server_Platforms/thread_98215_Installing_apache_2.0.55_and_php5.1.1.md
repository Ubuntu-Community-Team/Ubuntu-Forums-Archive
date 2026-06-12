---
title: "Installing apache 2.0.55 and php5.1.1"
date: 2005-12-02
forum: Server Platforms
---

### Post by akurashy on 2005-12-02
Installing apache 2.0.55 and php5.1.1
 
**(Special Thanks to J.C. Denton)**

 This How-to is to get the latest apache and php, I would like to say this is my first time I write one, sorry if you don't understand, but I will be happy to help you through this :)  
 

  First let get rid of the old apache and php
 

 For apache2
 ```
$ sudo apt-get remove apache2
```  

 or apache1
 

 ```
$sudo apt-get remove apache
```  

 Remove php old versions
 

 ```
$ sudo apt-get remove php5
```  

 if php4
 
```
$ sudo apt-get remove php4
```  

 Now let get to start downloading the sources!
 

 Apache 2.0.55
 
```
 $ wget -c [http://apache.mirrors.versehost.com/httpd/httpd-2.0.55.tar.gz]("http://apache.mirrors.versehost.com/httpd/httpd-2.0.55.tar.gz")
  $ tar -xvvzf [httpd-2.0.55.tar.gz]("http://apache.mirrors.versehost.com/httpd/httpd-2.0.55.tar.gz") 

  $ cd httpd-2.0.55

```  

 Now we are going to configure 

 

 ```
$ ./configure --enable-so 
``` 
 

 After you configure it
 
```
$ make
```  

 Now some people might going to do sudo make install, but lets do [URL="http://apache.mirrors.versehost.com/httpd/httpd-2.0.55.tar.gz"]
[/URL]
 (Be sure to have checkinstall installed)


 ```
$ sudo checkinstall
``` 
From there you can just follow what checkinstall tells you.

after that, hurray we have apache 2.0.55 installed! :D 




Now we go to php 5.1.1

Lets get it first of course

```
 $ wget -c [http://us3.php.net/get/php-5.1.1.tar.gz/from/us2.php.net/mirror]("http://us3.php.net/get/php-5.1.1.tar.gz/from/us2.php.net/mirror")
``` 
Untar it and cd to it


```
$ tar -xvvzf php-5.1.1.tar.gz
$ cd php-5.1.1

``` 
We are going to configure it now, beware you might run into some packages needed, just check in the synaptic to get them :)


```
$ ./configure --prefix=/usr/local/apache2/php --with-config-file-path=/usr/local/apache2/php --with-apxs2=/usr/local/apache2/bin/apxs --with-mysql --enable-gd --with-gd --with-xsl --enable-xslt --with-xslt-sablot --with-xml --with-zlib --enable-calendar --enable-sysvsem --enable-sysvshm --enable-sysvmsg --enable-track-vars --enable-trans-sid --enable-bcmath --with-bz2 --enable-ctype --with-db4 --with-regex=php

``` 
After that longgggg configure (which shouldn't take long) it's time to compile it

```
$ make
``` 
After it compiles we do checkinstall

```
$ sudo checkinstall
``` 
Fill what it tells you and well enjoy your .deb :)

Now let's see

Lets stop apache
```

$ sudo /usr/local/apache2/bin/apachectl stop
then start it
$ sudo /usr/local/apache2/bin/apachectl start

``` 


How to know your file is running? well save a index.php with the content inside 



```
open index.php
<?php
phpinfo();
?>
close index.php

``` 


Normally the htdocs is in /usr/local/apache2/htdocs so save it there
well i moved mine to /var/www :) you can change it in the config




Well that's is all
If the index.php is sucessful to open in localhost/index.php then you have installed this neat webserver!



Hope this help you! :)

---

### Post by goneskiing on 2005-12-03
The php install does not work for me:
Apache installed okay.
I tested apache by going to [http://localhost](http://localhost) - works okay

PhP 5.1.1 installed okay (I left off mysql and db4, added pgsql)

I changed /usr/local/apache2/conf/httpd.conf:
changed listen 80 to listen 127.0.0.1:80
changed document root (in both places) to /var/www

stopped and restarted Apache server
[http://localhost](http://localhost) now shows the contents of /var/www - so Apache okay
BUT: testphp comes up as text 

Maybe DirectoryIndex needs to be specified in the modules file but I cannot find the modules-available directory ?  Any ideas?

---

### Post by akurashy on 2005-12-03
can you paste your conf? httpd conf

---

### Post by curtis on 2005-12-03
```
AddType application/x-httpd-php .php
```
Add that below
```

LoadModule php5_module        modules/libphp5.so

```

---

### Post by goneskiing on 2005-12-03
Thanks to everyone here who helped - FINALLY success!  Compiling from source was the key.  Meanwhile I discovered an excellent book - Professional PHP4 (Appress Press).

---

### Post by akurashy on 2005-12-04
Glad you got it running :), enjoy!, what's that book about?

---

### Post by cloneofsnake on 2005-12-08
Failed here:

>  Now we are going to configure

Code:

$ ./configure --enable-so


and then I looked in the home\httpd-2.0.55 folder and found INSTALL - software installation instructions, it says:

> 
     $ ./configure --prefix=PREFIX
     $ make
     $ make install
     $ PREFIX/bin/apachectl start


Tried the first ./configure line, got "configure: error: no acceptable C compiler found in $PATH"

(I just installed ubuntu last night, without any of the upgrades that it told to about first thing.  I think I need to get some of the basic stuff installed first before messing with LAMP, yah?  Can someone please point me to some good sources on how to get my ubuntu set up properly?  Preferably with explaination on the commands too?  From what I done here so far, I figured "sudo" is ubuntu's application install / uninstall manager; wget is "web get"?; tar is unzip; cd is confirm directory; ./configure is err... stating the install path?)

---

### Post by phatmatt on 2005-12-18
"We are going to configure it now, beware you might run into some packages needed, just check in the synaptic to get them "

What packages are needed to ./configure php-5.1.1?  I'm running shell and synaptic is only for gui, right?

---

### Post by x__dark on 2005-12-23
I ran into some problems installing php 5.1.1, but the apache install went well.

You should add a section stating the required packages for PHP 5.1.1 to make life easier and also, anyone using this guide should note you need to install build-essential & checkinstall before attempting to install apache.

> sudo apt-get install build-essential
> sudo apt-get install checkinstall

Will this version of apache work with the version of PHP5 included in the apt repos?

---

### Post by now-new on 2007-11-15
now you can easily install apache2 and php5 by just writting sudo apt-get install apache2/php5. it work fine with me. the thing is that I cant stop and/or restart apache.

---

### Post by DvX on 2007-11-15
Hi
please help me

I installed Apache but after configure 

> ./configure --enable-so

i try do 

> sudo make

and

> sudo make install

but it's gave me this message:

> make: *** No targets specified and no makefile found.  Stop.

i sure from password :(
what is problem?!! :confused:

i use Ubuntu for the first time :)

---

### Post by tmth on 2008-05-21
In apache 2.2.x

```
sudo checkinstall
```

is not working:

```
chmod 644 /usr/lib/libapr-1.a
chmod: changing permissions of `/usr/lib/libapr-1.a': No such file or directory
```
And then checkinstall fails

---

