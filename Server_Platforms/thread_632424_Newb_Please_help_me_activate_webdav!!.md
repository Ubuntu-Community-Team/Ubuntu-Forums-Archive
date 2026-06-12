---
title: "Newb: Please help me activate webdav!!"
date: 2007-12-05
forum: Server Platforms
---

### Post by Smartin on 2007-12-05
Hi,

I'm running Dapper server 6.0.LTS with the Ubuntu desktop.

I had this running just fine in Feisty but the move to Dapper Server has broken something...

This is what I have done:

To enable the apache modules:
```

sudo a2enmod

dav

sudo a2enmod

dav_fs

```

Then make sure the lock file exists:
```

$ cd /var/lock/apache2
$ sudo touch DAVLock
$ sudo chown www-data:www-data DAVLock

```

To create user folder:
```

sudo mkdir /var/www/simon
sudo chgrp www-data /var/www/simon
sudo chmod 775 /var/www/simon

```

To create the user password:
```

sudo htpasswd -c /var/www/simon/.DAVlogin simon 

```

Then create restrictions to folder:
```

sudo nano /etc/apache2/mods-enabled/dav_fs.conf

```

Paste in:
```

DAVLockDB /var/lock/apache2/DAVLock
#DAVMinTimeout 600

<Location /dav/simon/>
        Dav On

        AuthType Basic
        AuthName simon
        AuthUserFile /var/www/dav/simon/.DAVlogin

        <LimitExcept OPTIONS>
                Require user simon
        </LimitExcept>
</Location>

```

Restart apache:
```

sudo /etc/init.d/apache2 restart

```

When I then try to access the folder [http://myserver/simon](http://myserver/simon) using the finder of my OSX box I get an error to the effect that the server cannot be found.

When I try a browser, I can see the folder /simon and can get inside it without a password.

What the heck have I done wrong? :-)

Simon

---

### Post by Smartin on 2007-12-06
Hi,

I don't know if it's relevant but if I open my DAVLock file in gEdit, there's nothing in it.

I was expecting something to be in that file...

?

Simon

---

