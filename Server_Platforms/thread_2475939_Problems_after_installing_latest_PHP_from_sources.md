---
title: "Problems after installing latest PHP from sources"
date: 2022-06-12
forum: Server Platforms
---

### Post by cookiepot on 2022-06-12
I removed my php 7.2 package that I installed from the official repositories and installed latest PHP from sources on github. I entered the directory and did so :
```

./configure --with-apxs2=/usr/bin/apxs --with-pdo-mysql
make -j4
sudo make install

```

(I followed the instructions from the github readme and here : [https://www.php.net/manual/en/install.unix.apache2.php](https://www.php.net/manual/en/install.unix.apache2.php))

So running php -version gives me PHP 8.2.0-dev, but when I open phpmyadmin I have these errors :
```

Deprecated: Using ${var} in strings is deprecated, use {$var} instead in /usr/share/php/php-php-gettext/gettext.inc on line 91

Deprecated: Using ${var} in strings is deprecated, use {$var} instead in /usr/share/php/php-php-gettext/gettext.inc on line 92

Deprecated: Using ${var} in strings is deprecated, use {$var} instead in /usr/share/php/php-php-gettext/gettext.inc on line 94

Deprecated: Using ${var} in strings is deprecated, use {$var} instead in /usr/share/php/php-php-gettext/gettext.inc on line 99

Deprecated: Using ${var} in strings is deprecated, use {$var} instead in /usr/share/php/php-php-gettext/gettext.inc on line 100

Deprecated: Using ${var} in strings is deprecated, use {$var} instead in /usr/share/php/php-php-gettext/gettext.inc on line 102

Fatal error: Array and string offset access syntax with curly braces is no longer supported in /usr/share/phpmyadmin/libraries/Util.php on line 2087

```

So what did I do wrong ?

---

### Post by TheFu on 2022-06-12
If you plan to install any other applications from the official repos that use PHP, then those all expect the older version and you've broken that.  Those errors appear to be due to running a different version of php than the web-pages expect.  Php 8 is different from php 7.

The correct method, for all scripting languages, to have a newer version is to use a virtual-environment-manager which let's you pick which version of php is used on the system for specific needs.
Php, Ruby, Perl, Python all have solutions for this or you can manually set it up using different directories - that's what /usr/local/ is for or you can do the virtual environments under your HOME.

For example, I use perlbrew with perl.
There are 4 different perl versions installed, 3 are controlled by perlbrew and 1 is the default system-perl.
```
$ perlbrew list
  perl-5.36.0                               
* perl-5.35.11                              
  perl-5.29.7         
```

The system perl is:
```
$ which perl
/usr/bin/perl
$ perl -v
This is perl 5, version 30, subversion 0 (v5.30.0)
```
I can change between them at will withing 1 shell. All the others use whatever the default perl is ... which is 5.25.11 currently.  I'm playing with 5.36.0 which has some new features.

Hopefully, this makes sense and you can from the php version manager tool, install it and learn the 5 commands to make it do what you need.

---

### Post by cookiepot on 2022-06-12
Thanks, it makes more sense now. So i've read a bit about multiversionning PHP and found this to switch to php 8 :
```

sudo update-alternatives --set php /usr/bin/php8.0
sudo update-alternatives --set phar /usr/bin/phar8.0
sudo update-alternatives --set phar.phar /usr/bin/phar.phar8.0

```

Ok, but in /usr/bin, there is only "php7.2" (from the php I removed improperly) and a file php, which is a link to "/etc/alternatives/php", which is also a link to "/usr/bin/php7.2".

php8 seems to be installed in /usr/local/bin, here is the return when I installed php8 :
```

Installing shared extensions:     /usr/local/lib/php/extensions/no-debug-non-zts-20210903/
Installing PHP CLI binary:        /usr/local/bin/
Installing PHP CLI man page:      /usr/local/php/man/man1/
Installing phpdbg binary:         /usr/local/bin/
Installing phpdbg man page:       /usr/local/php/man/man1/
Installing PHP CGI binary:        /usr/local/bin/
Installing PHP CGI man page:      /usr/local/php/man/man1/
Installing build environment:     /usr/local/lib/php/build/
Installing header files:          /usr/local/include/php/
Installing helper programs:       /usr/local/bin/
  program: phpize
  program: php-config
Installing man pages:             /usr/local/php/man/man1/
  page: phpize.1
  page: php-config.1
/home/axel/Téléchargements/php-src-master/build/shtool install -c ext/phar/phar.phar /usr/local/bin/phar.phar
ln -s -f phar.phar /usr/local/bin/phar
Installing PDO headers:           /usr/local/include/php/ext/pdo/

```

So, what should I do now ? Maybe I have to reinstall php7.2, then run the 3 update-alternatives commands and link them to the files in /usr/local/bin

---

### Post by cookiepot on 2022-06-13
I reinstalled "default" Ubuntu php, then I rebuild the latest php 8 package with the following options :
```

./buildconf
./configure --enable-cli --enable-fpm --enable-intl --enable-mbstring --enable-opcache --enable-sockets --enable-soap --with-curl --with-freetype --with-jpeg --with-mysql-sock --with-mysqli --with-openssl --with-pdo-mysql --with-pgsql --with-xsl --with-zlib --with-apxs2=/usr/bin/apxs2 
make -j4
sudo make install 
sudo cp php.ini-development /usr/local/lib/php.ini

```

Then I added some lines in apache2.conf following the instructions on this page : [https://www.php.net/manual/en/install.unix.apache2.php](https://www.php.net/manual/en/install.unix.apache2.php)
```

LoadModule php_module modules/libphp.so
<FilesMatch \.php$>
    SetHandler application/x-httpd-php
</FilesMatch>
```

Now, it seems that Apache doesn't recognize php. When I open a php page, the source code in the web browser displays and underlines in red the php stuff

---

### Post by TheFu on 2022-06-13
Whenever you install manually build software, you have to set the PREFIX to somewhere else.  Don't let it point at /usr.  Try /usr/local instead.  This has been how we've done locally installed (i.e. non-packaged) software since the mid-1990s - perhaps longer.

The PREFIX is controlled by the ./configure script and should be reflected in the resulting Makefile.


Why did you ignore the strong suggesting to use a php virtual environment tool?  Really, you should use that instead.

---

### Post by cookiepot on 2022-06-19
I didn't know that we have to do that since the mid-1990s, but php 8 seems to be already installed in /usr/local, as I showed earlier
I tried to read the configure script but it's too long and I don't understand...
I don't have much time but I read (and learned) a ton of things, but I'm still unable to make the link between apache and php 8. I didn't ignore the suggesting to install phpbrew, I just don't understand why apache doesn't recognize my php 8, and if I don't understand that, I won't be able to understand phpbrew either and I'd have other problems

---

### Post by TheFu on 2022-06-19
I don't use php or apache much (we use nginx and ruby/perl here), so someone else will need to provide specific answers. 

Maybe general answers will help?  Apache needs to be told to use the php program and modules you want.  When installing apache + php through the LAMP meta-package on Ubuntu, those connections are setup for us and assume the default locations that each pre-packaged version uses.  There is a php.ini file that would be used to tell apache these locations.  

For self-compiled stuff (anything in /usr/local/), we have to tell apache to use the different php.ini file which is configured for the specific version of php and the modules for that version.  There are many php.ini files on most systems, so you'll need to use/find a specific one.  phpbrew seems very similar to perlbrew, except it is written in php.  I've seldom seen php used as an admin scripting language. It is 99% of the time uses for webapps, not admin scripts.  Regardless, phpbrew would manage environment variables to ensure the desired version of php is used along with the specific modules just for that php version, keeping each of the php versions separate from each other.  This is very, very, important.  I would hope that phpbrew has code to swap the php version used by apache.  [https://github.com/phpbrew/phpbrew/issues/708](https://github.com/phpbrew/phpbrew/issues/708) well, crap. Seems modifying apache is on their feature list, but not yet implemented.

Someone wrote a little script to handle it: [https://stackoverflow.com/questions/20584156/tell-apache-to-use-a-specific-php-version-installed-using-phpbrew/34686059#34686059](https://stackoverflow.com/questions/20584156/tell-apache-to-use-a-specific-php-version-installed-using-phpbrew/34686059#34686059)

Of course, knowing how to manually do it would be important before trusting any script that has to run as root (which this would). Anyway, those scripts have the code for switching php versions, so it shouldn't be too hard to figure out what they do.

Hope this is helpful. If not, just ignore me until someone else with more php-apache skills provides answers.

---

### Post by cookiepot on 2022-06-19
Thank you ! I finally figured out how to do the task.

---

### Post by TheFu on 2022-06-19
> **cookiepot said:**
> Thank you ! I finally figured out how to do the task.

You could help the community by saying which files had to be modified and what those modification where .... so the next person, like you, might find the answer?
While you are at it, using the "Thread Tools" button to mark this thread as SOLVED really helps both people looking for answers and people looking to be helpful.  Save time for other people, please.

---

### Post by cookiepot on 2022-06-21
I forgot to mention I installed phpbrew. I'm sorry for not trying harder in the other way, but I've lost too much time for something that should have been quick. I still dont close the topic, because now phpmyadmin needs php 7 and not 8. I report the solution as soon as I find it.

---

