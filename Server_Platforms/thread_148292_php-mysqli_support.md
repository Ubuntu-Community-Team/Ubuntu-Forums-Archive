---
title: "php-mysqli support"
date: 2006-03-21
forum: Server Platforms
---

### Post by gmclachl on 2006-03-21
I really needed mysqli support in PHP so I built a package that enables the php-mysqli module on Dapper. In case anyone is in the same boat I thought I would share.

   [http://www.untitledproject.co.uk/packages](http://www.untitledproject.co.uk/packages)  

 After installing you will need to restart apache. 
  sudo /etc/init.d/apache2 force-reload 

  I also have a Breezy package, if anyone is interested i can post that as well, but it needs to be tidied up a bit first. 

 This is my first package, and hasn't really been tested, thoroughly   it works for me on a couple of machines and thats about all the testing i have done. So you have been warned.

 George

---

### Post by dudus on 2006-03-22
I haven't tried dapper yet but I was hopping it comes with mysqli. If it isn't true then your pack is very apreciated. Until now the only way to have mysqli in Ubuntu that I know is compilling using the mysqli flag as I described here:

[https://wiki.ubuntu.com/PHP5FromSource](https://wiki.ubuntu.com/PHP5FromSource)

I think it is very iportant that dapper comes with php-mysqli package.

I'll post this in he dapper forum.

---

### Post by tejo on 2006-04-03
it works on dapper, i've tried it


many many many thanks gmclachl

---

### Post by dudus on 2006-04-06
running dapper now but it doesn't has mysqli.
there is a bug for it:
[https://launchpad.net/distros/ubuntu/+source/php5/+bug/27904](https://launchpad.net/distros/ubuntu/+source/php5/+bug/27904)

---

### Post by Limber on 2006-04-07
Gives me an Error: Dependency is not satisfiable: php5-common

Obvioulsy I have php5-common installed...

---

### Post by gmclachl on 2006-04-07
Hmm, thats weird. Are you running Dapper?

 George

---

### Post by Limber on 2006-04-07
I sure am...

I really don't get it, php + mysql works and everything, plus I've run apt-get update-dist
My punbb forums really need mysqli... do I have to reinstall php5 and edit configure to make this work? Sooo annoying.

Good stuff that you made the package though :)

---

### Post by gmclachl on 2006-04-07
Ah, it appears that the version has changed in Ubuntu I have a dependency of php5-common-5.1.2-1ubuntu1 and it is now php5-common-5.1.2-1ubuntu2.

 I will need to roll the package again. 

 George

---

### Post by gmclachl on 2006-04-07
I needed to roll the package again to allow for the fact php5-common has been upgraded. 

 [http://www.untitledproject.co.uk/packages/php5-mysqli-1untitledproject2.deb](http://www.untitledproject.co.uk/packages/php5-mysqli-1untitledproject2.deb)

  That should work for you now.

  George

---

### Post by gmclachl on 2006-04-07
Bah duplicate post.

---

### Post by Limber on 2006-04-07
You da man, George. *hugs*
=)

---

### Post by dudus on 2006-04-10
It seems that libmysql15 has changed to libmysql15off. As it seems temporary you should set both

libmysqlclient15off |  libmysqlclient15

---

### Post by dudus on 2006-04-10
[quote=dudus]It seems that libmysql15 has changed to libmysql15off. As it seems temporary you should set both

libmysqlclient15off |  libmysqlclient15[/quote]

I changed the package you did and added this corrections. But I'm very new to this and not sure if it was right. Then it installed ok but apache could not load the extenssion.

I then removed the package and tried to install with my bare hands. The same error. 

```

[Mon Apr 10 18:13:08 2006] [notice] caught SIGTERM, shutting down
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20051025/mysqli.so' - /usr/lib/libmysqlclient.so.15: version `MYSQL_5.0' not found (required by /usr/lib/php5/20051025/mysqli.so) in Unknown on line 0
[Mon Apr 10 18:13:10 2006] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2-1ubuntu2 configured -- resuming normal operations
```

This is the output apache writes to his error.log. Then apache starts fine but with no mysqli.
I checked that lib (/usr/lib/libmysqlclient.so.15) was there. And I'm clueless 

What could be the problem?

---

### Post by gmclachl on 2006-04-10
[QUOTE=dudus]I changed the package you did and added this corrections. But I'm very new to this and not sure if it was right. Then it installed ok but apache could not load the extenssion.

I then removed the package and tried to install with my bare hands. The same error. 

```

[Mon Apr 10 18:13:08 2006] [notice] caught SIGTERM, shutting down
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20051025/mysqli.so' - /usr/lib/libmysqlclient.so.15: version `MYSQL_5.0' not found (required by /usr/lib/php5/20051025/mysqli.so) in Unknown on line 0
[Mon Apr 10 18:13:10 2006] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2-1ubuntu2 configured -- resuming normal operations
```

This is the output apache writes to his error.log. Then apache starts fine but with no mysqli.
I checked that lib (/usr/lib/libmysqlclient.so.15) was there. And I'm clueless 

What could be the problem?[/QUOTE]

 Hmmm,  I just had a look at the repositories and it appears that MySQL has been updated from 5.0.18 to 5.0.19 ( this accounts for the new libmysqlclientoff )

 As you need to build the extension against mysql_config I assume the upgrade means that using either libmysqlclient15off or the updated MySQL is causing the failure. I will need to look into it, and will need to build it again for 5.0.19 

Um..you are using MySQL 5 aren't you?
 George

---

### Post by dudus on 2006-04-10
Yes it's right I update my mysql to 5.0.19.
Didn't know that mysqli.so was so dependent on mysql version. Will I have to update it for every new release (mysql 5.0.20 is alredy out and may be in the repos any time!)

Anyway,
Thanks for the efforts George, I'm looking forward this.
And studing this package thing. By the way, I learned some from your package :)

---

### Post by dudus on 2006-04-12
George save me!!!! ](*,)

It is driving me crazy. Can't get this to work!

I have this libraries installed:

```
 
libmysqlclient15-dev_5.0.19-3_i386.deb
libmysqlclient15off_5.0.19-3_i386.deb

``` 
I found that mysql_config only existis if you install libmysqlclient15-dev. Even with this I get the same error.

Notice that as your package depends on  libmysqlclient15, I had to repack depending on  libmysqlclient15off. 

I installed mysql-admin to test my mysql configuration. Everything seems to work well, so I suppose my client and server are ok.:-k


Still apache won't load mysqli
tail /var/log/apache2/error.log
```
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20051025/mysqli.so' - /usr/lib/libmysqlclient.so.15: version `MYSQL_5.0' not found (required by /usr/lib/php5/20051025/mysqli.so) in Unknown on line 0
[Wed Apr 12 17:28:45 2006] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2-1ubuntu2 configured -- resuming normal operations

``` 
Tried googling this error, but I got nothing.:-k

I checked that I have the file mysqli.so in folder /usr/lib/php5/20051025/. And that php.ini tries to load the file.

:confused:  Is there any other file needed for this to work (ie. any mysql extension)?

I suppose the problem is the mysqli.so file I extracted from your deb. I tried getting a fresh one but there's nowhere to download this.
Maybe I should try to compile a new php5 and get just this file!?

If I can't find a way till tomorrow I'll remove everything related to php5 from dapper and compile a whole new verssion.

Tomorrow is beta-freeze and I thin php5-mysqli won't make into the repos. Such a pitty.:(

Mysql version: MySQL 5.0.19-Debian_3-log
php version: PHP 5.1.2-1ubuntu2


Thanks for everything.

---

### Post by gmclachl on 2006-04-12
I haven't had the chance to build the package yet. I just updated  MySQL etc on my x86 machine and I am now running 5.0.19 anyway I built the mysqli lib, I thought rather than pack it you could try it first. 

   [http://www.untitledproject.co.uk/packages/mysqli.so](http://www.untitledproject.co.uk/packages/mysqli.so) 

 Download it and put it in /usr/lib/php5/20051025/

 and add extension=mysqli.so in your /etc/php5/apache2/php.ini

 restart apache, and that should be you. I tried it locally, and it works here. 

 George

---

### Post by gmclachl on 2006-04-12
I  have built the package anyway, tested in locally and it seems to be working, I am running 5.0.19  still need to tidy the package up a touch, I have one warning I need to get rid of when I am packaging it. However this won't affect how it works on your system. 

 [http://www.untitledproject.co.uk/packages/php5-mysqli-1untitledproject2.deb](http://www.untitledproject.co.uk/packages/php5-mysqli-1untitledproject2.deb)
 
 George

---

### Post by dudus on 2006-04-13
George, I have to agree with Limber. Your the man!
using mysqli.so works perfectly for me. 
I'll try your package.

If you give me permission I'll try to find some MOTU that is intersted in pushing this package into the repos.

---

### Post by dudus on 2006-04-13
[QUOTE=gmclachl]I  have built the package anyway, tested in locally and it seems to be working, I am running 5.0.19  still need to tidy the package up a touch, I have one warning I need to get rid of when I am packaging it. However this won't affect how it works on your system. 

 [http://www.untitledproject.co.uk/packages/php5-mysqli-1untitledproject2.deb](http://www.untitledproject.co.uk/packages/php5-mysqli-1untitledproject2.deb)
 
 George[/QUOTE]
I tried this package and it works perfect for me either.
But I'm somewhat confused.
This package installs mysqli.so file with size 97K.
And the mysqli.so file you gave me before has 369K.
Both work. But why there is this difference.
And where are you getting these files from? Are these from the debian package?

Many thanks again

---

### Post by gmclachl on 2006-04-13
Thats because a .deb file is compressed. Glad it worked though.

 George

---

### Post by gmclachl on 2006-04-13
I built mysqli as a shared library, it's fairly simple to do. You need to make sure you have build-essential and I think you need another couple of build packages, whose names escape me just now.  

 You also need libmysqlclientxx-dev 

 
   Download the PHP source that matches the PHP installed on your machine and unpack it. 
   cd to the unpacked directory
    cd path/to/php/source/ext/mysqli 

    type 
    phpize 
    
    type 
     ./configure --with-mysqli=shared,/usr/bin/mysql_config
  
    type 
    make 

    type
    sudo make install 

   You will now have mysqli.so in your /usr/lib/php/2005..../ directory 

     
   
 George

---

### Post by dudus on 2006-04-13
Nice. I tried it just for fun. Worked perfectly. 
Thanks again :)

---

### Post by bbzbryce on 2006-04-15
Thanks George, that solved my problem.  One thing I had to figure out was how to get phpize, which is in the package php5-dev, so if anyone is wondering.

---

### Post by LordNikon9x on 2006-04-21
Is there plans to get php-mysqli to package repository?

Just my 2c.

---

### Post by darkrad on 2006-04-26
hello, i have same problem with ](*,) :

```
[12:24] couldn't load file "/usr/local/lib/mysqltcl-3.01/libmysqltcl3.01.so": /usr/lib/libmysqlclient.so.15: version `MYSQL_5.0' not found (required by /usr/local/lib/mysqltcl-3.01/libmysqltcl3.01.so)
    while executing
"load /usr/local/lib/mysqltcl-3.01/libmysqltcl3.01.so"
```

can somebody say me what i need to do to fix that? thanks

---

### Post by darkrad on 2006-04-27
i can't use it anymore?

---

### Post by gmclachl on 2006-04-27
I would assume php5 has been updated in the repositories, so I will need to build the extension against the new version. Which I will do tonight. 

Actually, reading your post again, thats probably not the problem.  I will look into it when I get home from the office. 

 George

---

### Post by darkrad on 2006-04-27
thanks, let me know please

---

### Post by dudus on 2006-04-27
[QUOTE=darkrad]thanks, let me know please[/QUOTE]
Are you using dapper?
I'm using dapper fully updated here and it works like a charm

---

### Post by darkrad on 2006-04-27
i fixed updating mysqltcl ([http://www.xdobry.de/mysqltcl/mysqltcl-3.02.tar.gz](http://www.xdobry.de/mysqltcl/mysqltcl-3.02.tar.gz))

thanks

---

### Post by charlie. on 2006-04-27
As far as I know, the following must be installed for PHP5's source code to build:

build-essential
flex
bison
libxml2-dev
libmysqlclient15-dev

The last name includes the "15" version number. I found this version by looking at the name of "libmysqlclient..." under "Installed Packages" in aptitude.

Once you have the dependencies, you SHOULD be able to build PHP5, with mysqli, and the dig through the output for mysqli.so, which you could manually copy to your PHP extension DIR. (mysqli.so should be in the 'ext/mysqli' subdir in the build output after "make" is complete.) Unless you "make install", simply building the source will not interfere with any installed PHP modules that APT installed. You will have to rebuild if you update either PHP or mysql-client with APT.

I installed everything above, and built my PHP source code with...

make clean
./configure --enable-mysqli
make

... and observed no build errors. I did not, however, get a mysqli.so file in my output. Instead, I got mysqli.lo, which is not a shared object file. I expect that the configure line should have been...

./configure --with-mysqli=shared,/usr/bin/mysql_config

... as gmclachl suggested. Tomorrow, I will try this. If it works, you will know. (BTW: Does anyone know the significance of the path, "/usr/bin/mysql_config," in the above line?)

---

### Post by charlie. on 2006-04-28
Changing the ./configure line to...

./configure --with-mysqli=shared,/usr/bin/mysql_config

... made all the difference. I tried it with and without the "shared," section. Without the 'shared' keyword, mysqli.so is not generated.

After running "make", mysqli.so may be located within the "modules" subdirectory. It should be copied to your PHP module directory...

sudo cp mysqli.so /usr/lib/php5/20051025/

.. and then owned by root. Take note, this extension_dir is not set explicitly in php.ini - it is the default and can be seen in a phpinfo() output.

Now all you need to do is add the line...

extension=mysqli.so

.. to your php.ini (/etc/php5/apache2/php.ini) and restart your apache server. (That is done quite frequently, so an alias for it is a good idea - mine is 'restart-apache')

A phpinfo() page should now show "mysqli" as a loaded extension. The extensions are listed in alphabetical order, so it should not be too difficult to locate. At this point in time, the PHP source tree and build output can be axed. You should only have to rebuild this extension when you update PHP. When that happens, you will need the new source anyway.

---

### Post by dudus on 2006-04-28
This works for me... but if it is really that easy there isn't a package for it?
When I get this packaging thing I will do a package and try to add it to the repos.

---

### Post by dudus on 2006-05-10
The package George did brakes with a full updated dapper install. This is due to the upgrade of mysql from verssion 5.0.19 to 5.0.21.

I made an updated package.
Enjoy.
[I]
Maybe you'll have to uninstall the old one before installing this one[/I]

---

### Post by charlie. on 2006-05-11
dudus, you have just validated my decision to stick to building the extension manually - I don't have to wait for someone, however quick they may be, to provide an updated package. I only have to...

./configure
make
... copy mysqli.so

---

### Post by dudus on 2006-05-11
This may be worth for you. 
But build tools aren't default, and one don't need them just to have php5-mysqli.

Besides the build tools you also needs php5 development files and libs.

And you also loose the beauty of apt

---

### Post by Gtaylor on 2006-05-11
This is a really serious issue! I hope to see it included soon, I'm wanting to move some servers over to Dapper once it leaves beta but won't until this is resolved, I don't have the time or will to compile and distribute modules every time there are updates. 

To the devs out there: please grace us with a response to the Launchpad tracker entry at least, this really needs to be addressed!

---

### Post by gmclachl on 2006-05-12
FWIW it seems as if there is an offiicial package on the way. So if anyone needs mysqli support have a scout round the repos. 

George

---

