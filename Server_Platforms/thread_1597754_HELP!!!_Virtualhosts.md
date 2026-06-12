---
title: "********HELP!!! Virtualhosts*******"
date: 2010-10-15
forum: Server Platforms
---

### Post by Manifest on 2010-10-15
I added a subdomain(subdomain.mydomain.com) heres the contents
```
<VirtualHost ****************:80>
ServerName subdomain.mydomain.com
DocumentRoot /var/www/stuff/
</VirtualHost>
```But when i go to subdomain.mydomain.com it is the same page as 127.0.0.1

---

### Post by Manifest on 2010-10-15
I added a subdomain(subdomain.mydomain.com) heres the contents
```
<VirtualHost ****************:80>
ServerName subdomain.mydomain.com
DocumentRoot /var/www/stuff/
</VirtualHost>
```But when i go to subdomain.mydomain.com it is the same page as 127.0.0.1

---

### Post by Manifest on 2010-10-15
No answer????

---

### Post by lisati on 2010-10-15
*Thread moved to **Server Platforms**.*
Please be patient. The usual rule of thumb for these forums is to wait 24 hours before bumping your thread

---

### Post by junapp on 2010-10-15
did you restart the apache service?

sudo /etc/init.d/apache2 restart

---

### Post by Manifest on 2010-10-16
please anyone?

---

### Post by koenn on 2010-10-16
you can't just throw random stuff in a text file and expect it to work.

Here are some howtos that'll tell you how to set up apache virtual hosts:
[http://ubuntuforums.org/showthread.php?t=194807](http://ubuntuforums.org/showthread.php?t=194807)
[http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/](http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/)

You might want to reed up on apache to have a general idea about what your doing:
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html)

---

### Post by Manifest on 2010-10-16
I **do **know what i am doing
The domain works but the subdomain goes to /var/www

---

### Post by koenn on 2010-10-16
> **Manifest said:**
> I **do **know what i am doing

OK then.

---

### Post by CharlesA on 2010-10-16
> **Manifest said:**
> I **do **know what i am doing
The domain works but the subdomain goes to /var/www

With that attitude, I doubt you'll get much help.

I tested virtualhosts on my machine and it worked perfectly. You need to edit httpd.conf.

```
<VirtualHost *:80>
ServerName www.mars.com
ServerAlias www.mars.com
DocumentRoot /var/www/mars
</VirtualHost>
<VirtualHost *:80>
ServerName dc.mars.com
ServerAlias dc.mars.com
DocumentRoot /var/www/mars/www
</VirtualHost>

```

Also make sure name resolution is working correctly. I added dc.mars.com and mars.com to my /etc/hosts file.

---

### Post by SeijiSensei on 2010-10-16
Make sure you have "NameVirtualHost *:80" directive before the <VirtualHost></VirtualHost> containers as well.

---

### Post by basd82 on 2010-10-17
> **Manifest said:**
> I added a subdomain(subdomain.mydomain.com) heres the contents
```
<VirtualHost ****************:80>
ServerName subdomain.mydomain.com
DocumentRoot /var/www/stuff/
</VirtualHost>
```But when i go to subdomain.mydomain.com it is the same page as 127.0.0.1

Can you post the virt host config of mydomain.com also.

If there is catch all alias in that one you need make sure that subdomain.mydomain.com is loaded first


Bas

---

### Post by basd82 on 2010-10-17
> **basd82 said:**
> Can you post the virt host config of mydomain.com also.

If there is catch all alias in that one you need make sure that subdomain.mydomain.com is loaded first


Bas

Here is example is how do this  notice order of virtual host due to the catch all its importend

```

<VirtualHost *:80>
        ServerName      www.hccfotovideocreatief.nl
        ServerAdmin     webmaster@hccfotovideocreatief.nl
        DocumentRoot    /disk/site/hcc.nl/fotovideo/www
        Errorlog        /disk/site/hcc.nl/fotovideo/log/error.log
        TransferLog     /disk/site/hcc.nl/fotovideo/log/access.log
</VirtualHost>

<VirtualHost *:80>
        ServerName      redirect.hccfotovideocreatief.nl
        ServerAlias     hccfoto.nl                      *.hccfoto.nl \
                        hccvideo.nl                     *.hccvideo.nl\
                        hccfvc.nl                       *.hccfvc.nl \
                        hccfotovideocreatief.nl         *.hccfotovideocreatief.nl \
                        hcccreative.nl                  *.hcccreative.nl \
                        hcccreatief.nl                  *.hcccreatief.nl
        ServerAdmin     webmaster@hccfotovideocreatief.nl
        Redirect permanent / http://www.hccfotovideocreatief.nl/
</VirtualHost>

```

hope this helps

---

### Post by Manifest on 2010-10-17
I dont have anything in my httpd.conf if that helps:)

---

### Post by CharlesA on 2010-10-17
> **SeijiSensei said:**
> Make sure you have "NameVirtual Hosts *:80" directive before the <VirtualHost></VirtualHost> containers as well.

Does that really matter? I've added that before and apache throws out an error when restarted. Remove it and the error goes away.

> **Manifest said:**
> I dont have anything in my httpd.conf if that helps:)

Where were you defining the virtualhosts?

---

### Post by Manifest on 2010-10-17
Fixed thanks:KS

---

### Post by SeijiSensei on 2010-10-18
> **CharlesA said:**
> Does that really matter? I've added that before and apache throws out an error when restarted. Remove it and the error goes away.

Before HTTP/1.1 the only way to have a virtual host was to use multiple IP addresses assigned using multiple virtual interfaces like eth0:0, eth0:1, etc.  HTTP/1.1 added the "Host" parameter to the protocol exchange so that all the virtual hosts could share a single address and be differentiated by hostnames.

At this point (around Apache 1.1 if I recall correctly), Apache added the NameVirtualHost directive.  This is a global directive that's not included in any <VirtualHost></VirtualHost> containers but stands before all of them.

In my default apache2 installation, the directive is contained in ports.conf.

---

### Post by CharlesA on 2010-10-18
Thanks Seiji. That would explain why apache spit back errors when I added it to httpd.conf.

Didn't even check ports.conf.

---

### Post by koenn on 2010-10-18
> **CharlesA said:**
> Thanks Seiji. That would explain why apache spit back errors when I added it to httpd.conf.

Didn't even check ports.conf.

it shouldn't really matter in what config file you add it, Aren't those files just arbitrary spin-offs that get included in the main config file again  -- just a way to keep things organised ?

you can verify this with something like```

kdunix:/etc/apache2# grep -B1 ^Include /etc/apache2/apache2.conf 

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf
--
# Include all the user configurations:
Include /etc/apache2/httpd.conf
--
# Include ports listing
Include /etc/apache2/ports.conf
--
# Include generic snippets of statements
Include /etc/apache2/conf.d/
--
# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
```


What errors do you get ?

---

### Post by CharlesA on 2010-10-18
> **koenn said:**
> it shouldn't really matter in what config file you add it, Aren't those files just arbitrary spin-offs that get included in the main config file again  -- just a way to keep things organised ?

you can verify this with something like```

kdunix:/etc/apache2# grep -B1 ^Include /etc/apache2/apache2.conf 

Thanks, didn't know that. :)


> What errors do you get ?

This is what it spits back:

[code]root@mars:/etc/apache2# service apache2 restart
 * Restarting web server apache2  
[Mon Oct 18 10:58:25 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting [Mon Oct 18 10:58:26 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
                                                                                     [ OK ]


```

httpd.conf:

```
NameVirtualHost *:80
<VirtualHost *:80>
ServerName www.mars.com
ServerAlias www.mars.com
DocumentRoot /var/www/mars
</VirtualHost>
<VirtualHost *:80>
ServerName dc.mars.com
ServerAlias dc.mars.com
DocumentRoot /var/www/mars/www
</VirtualHost>

```

removing NameVirtualHost *:80 gets rid of the warning.

---

### Post by koenn on 2010-10-18
that probably means you already have a line 'NameVirtualHost *:80' in one of the config files (which, together, just add up to 1 giant conf file).

Adding a second one typically gives a warning like the one you get (triggered by the 2nd time apache reads it and tries to process it)

grep will probably show where you have them :
```
kdunix:/etc/apache2# grep -rl NameVirtu /etc/apache2/ 
/etc/apache2/ports.conf
```

after adding one in httpd.conf
```
kdunix:/etc/apache2# grep -rl NameVirtu /etc/apache2/ 
/etc/apache2/httpd.conf
/etc/apache2/ports.conf
```

---

### Post by CharlesA on 2010-10-18
Yep. That's why.

Thanks. :)

---

### Post by koenn on 2010-10-18
welcome

---

