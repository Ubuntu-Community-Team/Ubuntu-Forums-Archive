---
title: "[PHP5] - Install XDEBUG from dotdeb repository.. how?"
date: 2006-09-24
forum: Server Platforms
---

### Post by moreweb on 2006-09-24
Hi all,
someone have installed xdebug exstension from dotdeb packages?
I don't found php5-xdebug in repository.. that's strange.. or not?? :oops: 

How install it?

Thanks! :-s

---

### Post by moreweb on 2006-10-09
Hi all,
today I've tried to install xdebug with pecl.
I've installed php5-dev (and deps) but after ```
marco@box:~$ sudo pecl install xdebug-beta
downloading xdebug-2.0.0RC1.tgz ...
Starting to download xdebug-2.0.0RC1.tgz (252,286 bytes)
.....................................................done: 252,286 bytes
64 source files, building
running: phpize
Configuring for:
PHP Api Version:         20041225
Zend Module Api No:      20050922
Zend Extension Api No:   220051025
ERROR: `phpize' failed
``` I've got a generic phpize error. ](*,) 

Can someone help me?
Thanks

---

### Post by nielsh on 2006-10-22
Hi,

I just installed everything by hand and that seems to work fine:

[LIST=1]
[*]Download the source code [here]("http://www.xdebug.org/link.php?url=xdebug200rc1") and save it to ~/tmp.
[*]Go to ~/tmp, unpack the archive and go to the newly created directory:
```

cd ~/tmp
tar xvzf xdebug-2.0.0RC1.tgz
cd xdebug-2.0.0RC1
```
[*] Build and install the Xdebug library:
```

phpize
./configure --enable-xdebug
make
cp modules/xdebug.so /usr/lib/php5/20051025/
```
[*] Make the library known:
```

sudo gedit /etc/php5/apache2/php.ini
```
And add the following line:
```

zend_extension="/usr/lib/php5/20051025/xdebug.so"
```
[*] Restart Apache:
```

sudo /etc/init.d/apache2 restart
```
[/LIST]

That should be all. Xdebug should now show up if you run phpinfo().


Kind regards,

Niels

---

### Post by moreweb on 2006-11-06
Thanks **nielsh**!
I have lost your reply.. Now it works very well also with PHP 5.2.0. :D

---

