---
title: "Http symbolic links don't work."
date: 2014-09-05
forum: Server Platforms
---

### Post by Raymond Day on 2014-09-05
I have this OS:

root@odroid-XU3:~# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"
root@odroid-XU3:~#

It's on a Odroid-XU3 install on a eMMC 64GB card. But I have two 3TB hard rives on it's USB 3.0.

I had this before running on a Odroid-U2 and the links worked on it. But I think it was Ubuntu 13 or 12.

Did this command:

```
chown www-data:www-data /var/www -R
```

This command too:

```
chown www-data:www-data /var/www -R
```

My /etc/apache2/sites-enabled/000-default.conf looks like this:

```
<VirtualHost *:80>
   # The ServerName directive sets the request scheme, hostname and port that
   # the server uses to identify itself. This is used when creating
   # redirection URLs. In the context of virtual hosts, the ServerName
   # specifies what hostname must appear in the request's Host: header to
   # match this virtual host. For the default virtual host (this file) this
   # value is not decisive as it is used as a last resort host regardless.
   # However, you must set it for any further virtual host explicitly.
   #ServerName www.example.com

DocumentRoot /var/www
    <Directory />
            Options FollowSymLinks Indexes
            AllowOverride None
    </Directory>
    <Directory /var/www/>
            Options Indexes FollowSymLinks MultiViews
            AllowOverride None
            Order allow,deny
            allow from all
    </Directory>

   ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
   <Directory "/usr/lib/cgi-bin">
      AllowOverride None
      Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
      Order allow,deny
      Allow from all
   </Directory>

   # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
   # error, crit, alert, emerg.
   # It is also possible to configure the loglevel for particular
   # modules, e.g.
   #LogLevel info ssl:warn

   ErrorLog ${APACHE_LOG_DIR}/error.log
   CustomLog ${APACHE_LOG_DIR}/access.log combined

   # For most configuration files from conf-available/, which are
   # enabled or disabled at a global level, it is possible to
   # include a line for only one particular virtual host. For example the
   # following line enables the CGI configuration for this host only
   # after it has been globally disabled with "a2disconf".
   #Include conf-available/serve-cgi-bin.conf
</VirtualHost>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
```

It says "FollowSymLinks" I just don't get what is wrong.

Here is the end of the apache2 error line.

```
[Fri Sep 05 11:27:46.042075 2014] [core:error] [pid 3946] [client *.*.*.*:50242] AH00037: Symbolic link not allowed or link target not accessible: /var/www/Donalds_house
``` put * in my IP number.

That link looks like this:

```
root@odroid-XU3:~# ls -l /var/www/Donalds_house
lrwxrwxrwx 1 www-data www-data 138 Feb  6  2009 /var/www/Donalds_house -> ../../home/part2/was-partition2/was_on_smallwinserver/Shared/From_netgearhd/ray (netgearhd)/Back Up My Documents/My Pictures/Donalds_house
root@odroid-XU3:~#
```

The webpage just says this:

```
Forbidden

You don't have permission to access /Donalds_house/ on this server.

Apache/2.4.7 (Ubuntu) Server at 192.168.2.109 Port 80
```

Got samba linked to it and I can go to that link in samba at \\ODROID-XU3\USBdisk2-3TB\var\www\Donalds_house and it works.

Have my old server sort of a copy of this one at 192.168.2.110 and I can go to the same link only change 109 to 110 and it shows up on that server.

It's OS is:

```
root@odroid-u2:~# cat /etc/lsb-release
DISTRIB_ID=Linaro
DISTRIB_RELEASE=13.09
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Linaro 13.09"
root@odroid-u2:~#
```

Any one know what could be wrong. I have worked on this for hours in the past 3 days. So thought I would give up and post here and hope some one will know what's wrong.

-Raymond Day

---

### Post by TheFu on 2014-09-05
First - **chown** can only be run with **sudo**.

Second - if there is any part of the permissions that don't allow the webserver access from 
/home/part2/was-partition2/was_on_smallwinserver/Shared/From_netgearhd/ray (netgearhd)/Back Up My Documents/My Pictures/Donalds_house  **anywhere** in that entire path, it won't work.

Third - I'm not positive, but I don't think chown follows symlinks. Check the manpage to see if that is true or not.

---

### Post by Raymond Day on 2014-09-06
It don't matter. It just don't work when I have 777 Rights and every file is Owner by www-data and it still says 403 Forbidden.

So I guess it is some place else. I can copy the links right to the SD card and that is were the OS is and it will work on there. Just seems like it will not work with any link.

-Raymond Day

Looks like I just got it working. The 2 hard drives are mounted at /media/root because I was log in to the desktop as root and that's were it auto mounted them. So it would not let me link to root. So I chown it to www-data and now the links work now.

Wow took a long time to find out what was wrong. Just because it was mounted in /media/root

-Raymond Day

---

### Post by lisati on 2014-09-06
*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2014-09-06
automatic mounts are a bitch - to be avoided on any server. If you want storage mounted, mount it somewhere else and leave it.

For any lurkers - my next piece of advise was to avoid non-Linux file systems for this stuff. Avoid NTFS, fat32/vfat/xfat/ - the file and directory permissions don't work under Linux properly.  This especially applies for software developers working in compiled languages like Java or C/C++ - do that development on Linux file systems, not Windows.

Having 777 permissions means something is broke.  In another thread we've been discussing just that - nobody can think of a good reason for 777 permissions on any machine.  Even /tmp/ which appears to have 777 doesn't. The +t bit is set there.  If you think 777 permissions is the solution, time to get a better understanding of users/groups and permissions.

Oh - and don't run GUI programs as root.  There can be strange things that you don't want as unknown outcomes. 

Anyway, glad you have it solved.

---

