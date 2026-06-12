---
title: "Apache &amp; FTP: mod_ftp"
date: 2008-12-23
forum: Tutorials
---

### Post by coolaj86 on 2008-12-23
The ftp module for Apache hasn't been released yet as a stable module so you won't find it in the repositories, but you can build it pretty easily and the configuration isn't too much of a hassle.

[http://httpd.apache.org/mod_ftp/](http://httpd.apache.org/mod_ftp/)
[http://www.apache.org/dist/httpd/mod_ftp/](http://www.apache.org/dist/httpd/mod_ftp/)

The downside is that it's not in widespread use and it's not as easy to find howtos for.

Unfortunately, I'll just be covering the basics here. By default this will allow anonymous connections. Many of the other directives are explained in the example ftpd.conf provided (and many of them didn't work for me).

Prerequisites:
If you're not very familiar with apache take a look at another post of mine. It will either make you more or less confused so read at your own risk: 
[http://ubuntuforums.org/showthread.php?t=1019301](http://ubuntuforums.org/showthread.php?t=1019301)
You need to be able to compile from source code and you need the Apache's special APXS
```
apt-get install --yes --quiet build-essential subversion apache2-threaded-dev
mkdir ~/Code
```

Churn source into binary like milk into butter:
Here's where you'll do the actual compiling.
Either download from the tar.gz archives or get it via subversion.
```
cd ~/Code
wget http://www.apache.org/dist/httpd/mod_ftp/mod_ftp-0.9.2-beta.tar.gz
tar --extract --file mod_ftp-0.9.2-beta.tar.gz
####
# Or you can use svn 
# svn checkout http://svn.apache.org/repos/asf/httpd/mod_ftp/trunk/ mod_ftp
####
cd mod_ftp*
APXS=/usr/bin/apxs2 ./configure.apxs
make
sudo make install
```
I didn't have any problems here. Easy as pie.

Ubuntu-ify the configuration:
First open Ubuntu's default config file for apache and remove the lines that were added automatically
```

sudo su -
cd /etc/apache2
nano apache2.conf
####
#### Place a comment in front of or remove these 3 lines
#LoadModule ftp_module usr/lib/apache2/modules/mod_ftp.so
#
# Example mod_ftp configuration
#Include etc/apache2/extra/ftpd.conf
```
Next let's create necessary load file and move the provided config to the more appropriate location
```
echo "LoadModule ftp_module /usr/lib/apache2/modules/mod_ftp.so" > /etc/apache2/mods-available/ftpd.load
mv ./extra/ftpd.conf ./mods-available/
rmdir ./extra
a2enmod ftpd
```



Before you can reload apache you should either comment out the ftpd log section or create a file with the right permissions
```
cd /etc/apache2
nano ./mods-available/ftpd.conf
#### Bug Fix: Comment this line out for now
#ErrorLog     "var/log/apache2/ftp_error_log"

```

Then configure and customize as needed
```
cd /etc/apache2
nano ./mods-available/ftpd.conf
####
#### I make this change to use the directory I just created
# DocumentRoot "/var/ftp"
mkdir /var/ftp
touch /var/ftp/ftp-test.txt
chown www-data:www-data -R /var/ftp
```

Finally, restart or reload apache and visit [ftp://localhost/](ftp://localhost/) to see if all went as planned.
```
/etc/init.d/apache2 restart
```

---

### Post by blaer on 2009-01-02
Thanks!

The section with the vim httpd.conf puzzled me a bit. 
If you would have added a line like:

```
echo "LoadModule ftp_module /usr/lib/apache2/modules/mod_ftp.so" > /etc/apache2/mods-available/ftpd.load
```

It would have saved me some time. ;)

I'm not very familiar with apache, so i had to look how other modules did it.
I'm om ubuntu 8.04 Server.

---

### Post by coolaj86 on 2009-01-02
Agreed, your way makes more sense.

You might like to look at this too:
[http://ubuntuforums.org/showthread.php?t=1019301](http://ubuntuforums.org/showthread.php?t=1019301)
That's where I wrote up how to do some other common things with apache.

---

### Post by jobsworth on 2012-08-27
thank you cooaj86 for attempting to write this at all.
it did not go as easily for me as for you.
first time i tried it i got some horrible error messages.

in file included from ftp_internal.h:30,
                 from mod_ftp.c:24:
ftp_config.h:4:9: error: macro names must be identifiers
ftp_config.h:7:9: error: macro names must be identifiers
ftp_config.h:10:9: error: macro names must be identifiers
ftp_config.h:13:9: error: macro names must be identifiers
ftp_config.h:19:9: error: macro names must be identifiers
ftp_config.h:22:9: error: macro names must be identifiers
make[1]: *** [mod_ftp.slo] Error 1
make[1]: Leaving directory `/root/mod_ftp-0.9.6/modules/ftp'
make: *** [all-recursive] Error 1

so i just removed the include statement from ftp_internal,h
and tried again. this time it ran thru to the end without any error messages. incidentally i run debian squeeze and not ubuntu
and the latest version of mod_ftp was 9.6 and not 9.2
not that it should make a difference apart from altering 9.2 to 9.6,
i did not lose my apache web server and a2enmod ftpd worked,
i don't have a ftpd.conf file anywhere and would not know what to put in it if i had so while my apache2 has a clean restart and continues to work i don't really know how to use ftp.
i also have ftp on my web host provider and i don't know how to use that either. it should be something like [ftp://ftp.mywebsite.com](ftp://ftp.mywebsite.com)
for my web host provider but that does not do much.
i will persevere and get there in the end.
once again thank you for providing such a helpful post.

---

