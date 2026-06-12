---
title: "Encountered problem on enabling WebDAV with Apache2"
date: 2008-01-06
forum: Server Platforms
---

### Post by satimis on 2008-01-06
Hi folks,


Ubuntu 7.04 server amd64
apache2 - 2.2.3
php5 - 5.2.1
libapache2-mod-php5 - 5.2.1


I was following;
Enable WebDAV with Apache 2.x on Ubuntu Linux
[http://www.digital-arcanist.com/sanctum/article.php?story=20070427101250622](http://www.digital-arcanist.com/sanctum/article.php?story=20070427101250622)

Already enabled "dav_fs" module with running "a2enmod"


Performed following steps;

$ su
password
# cd /etc/apache2/mods-enabled/

# ln -s ../mods-available/dav* .```

ln: creating symbolic link `./dav_fs.conf' to `../mods-available/dav_fs.conf': File exists
ln: creating symbolic link `./dav_fs.load' to `../mods-available/dav_fs.load': File exists
ln: creating symbolic link `./dav.load' to `../mods-available/dav.load': File exists
ln: creating symbolic link `./dav_lock.load' to `../mods-available/dav_lock.load': Permission denied
ln: creating symbolic link `./dav_svn.conf' to `../mods-available/dav_svn.conf': File exists
ln: creating symbolic link `./dav_svn.load' to `../mods-available/dav_svn.load': File exists

```


# mkdir /usr/share/apache2/var
# touch /usr/share/apache2/var/DAVlock
# chown -R -c www-data:www-data /usr/share/apache2/var```

changed ownership of `/usr/share/apache2/var/DAVlock' to www-data:www-data
changed ownership of `/usr/share/apache2/var' to www-data:www-data

```

# htpasswd -m -c /etc/apache2/.htpasswd```

Usage:
        htpasswd [-cmdpsD] passwordfile username
        htpasswd -b[cmdpsD] passwordfile username password

        htpasswd -n[mdps] username
        htpasswd -nb[mdps] username password
 -c  Create a new file.
 -n  Don't update file; display results on stdout.
 -m  Force MD5 encryption of the password.
 -d  Force CRYPT encryption of the password (default).
 -p  Do not encrypt the password (plaintext).
 -s  Force SHA encryption of the password.
 -b  Use the password from the command line rather than prompting for it.
 -D  Delete the specified user.
On Windows, NetWare and TPF systems the '-m' flag is used by default.
On all other systems, the '-p' flag will probably not work.

```


I was stuck here.  According to "man htpasswd", there are 3 suggestions;

 htpasswd /usr/local/etc/apache/.htpasswd-users jsmith

 htpasswd -c /home/doe/public_html/.htpasswd jane

 htpasswd -mb /usr/web/.htpasswd-all jones Pwd4Steve


Which of them I should follow?  None of the above path exists.  Please advise.  TIA


B.R.
satimis

---

### Post by Miademora on 2008-01-06
You only need -c the first time or as long as the file doesnt exist yet.

You should put it outside the webroot where the webserver can still access it. Maybe around /etc/apache2/ or /etc/httpd/. Depending on what its called in ubuntu.

so for the first user like
htpasswd -mc /etc/apache2/.htpasswd username1

for additional users it should be
htpasswd -m /etc/apache2/.htpasswd username2

---

