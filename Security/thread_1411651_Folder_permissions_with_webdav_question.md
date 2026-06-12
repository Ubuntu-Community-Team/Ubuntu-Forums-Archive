---
title: "Folder permissions with webdav question"
date: 2010-02-20
forum: Security
---

### Post by Pirate King on 2010-02-20
Hi there,

(Wasn't sure if this should be in security or server section)

I just installed Ubuntu Server 9.10 on a PC and I'm very new to the whole command line scene. I've set up a web server with webdav using [this guide]("http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-8.10"). 

In addition to the /var/www/web1/**web** folder I made with the aforementioned guide, I have another folder (at location /home/ben/bendav) that I am also using as a webdav share. However, when accessing it from another computer, even with correct credentials I don't get write access! 



My /etc/apache2/sites-available/default file looks like this:

NameVirtualHost *
<VirtualHost *>
       
        DocumentRoot /var/www/web1/web/
        <Directory /var/www/web1/web/>
                Options Indexes MultiViews
                AllowOverride None
                Order allow,deny
                Allow from all
        </directory>

        Alias /webdav /var/www/web1/web

        <Location /webdav>
                DAV on
                Authtype Basic
                AuthName "webdav"
                AuthUserFile /var/www/web1/passwd.dav
                Require valid-user
        </location>

        Alias /bendav /home/ben/bendav

        <Location /bendav>
                DAV on
                Authtype Basic
                Authname "yoooommooooo"
                AuthUserFile /var/www/web1/bendavpasswd.dav
                require user beno
        </location>

</VirtualHost>

I would like to make it so only the user beno (from the bendavpasswd.dav file) can **read** or **write** the bendav folder, but at the moment if I mount the folder in my Ubuntu Desktop computer with user beno I can only get read access. I tried *$ chmod ug+rw bendav * but that didn't do anything.

Hope you guys understand, I'm crap at explaining things.

Thanks in advance!

---

### Post by Pirate King on 2010-02-20
haha, i think I spent a total of 10 hours on this problem. I was  determined to fix it, and it was literally one command I had overlooked! I needed to change the ownership of the /home/ben/bendav folder to the www-data group using *$ chown www-data /home/ben/bendav*. 

I love Ubuntu! =D

---

### Post by andre@home on 2011-10-09
Hi Pirate King
nice that you've got it fixed!

Do you have any suggestions on my problem. thanks....

Now I have a similar problem, at leat I think.... on Debian 6.

My son is a starting photographer and needs more space so:
So now I have:
sda1 as system with the DocumentRoot /var/www/web1/web/
sda2 as swap
sda 3: this partition I want to add
But I want to add also
sdb1
sdc1
sdd1

In total now at least 8 TB for his pop music photos. He already now has 2-3 TB so the system is ready for the coming few years...

My default file now looks like:
```
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/web1/web/
        <Directory /var/www/web1/web/>
                Options Indexes MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        Alias /webdav /var/www/web1/web

        <Location /webdav>
           DAV On
           AuthType Basic
           AuthName "webdav"
           AuthUserFile /var/www/web1/passwd.dav
           Require valid-user
       </Location>

Alias /webdav1 /mnt/webdav1

<Location /webdav1>
DAV on
Authtype Basic
Authname "webdav1"
AuthUserFile /var/www/web1/passwd1.dav
Require valid-user
</location>

</VirtualHost>

```

My rights are Ok I think, but still I got an error, see error.log Appache

#permissions of the directory you are trying to use as the DocumentRoot (were I’ve put some files in it):
root@tom-server-2:/etc/apache2/sites-available# ls -lh /var/www/web1/web
totaal 984K
-rwx------ 1 www-data www-data 0 okt 1 22:32 Nieuw - Bitmapafbeelding.bmp
-rwx------ 1 www-data www-data 75K okt 1 22:35 Nieuw - Bitmapafbeelding.JPG
drwx------ 2 www-data www-data 4,0K okt 1 22:31 testmap
-rw-r--r-- 1 www-data www-data 74K okt 8 14:25 voip-23-07-11.pdf
-rwx------ 1 www-data www-data 814K okt 1 23:05 WebDAV and Autoversioning - Version Control with Subversion - O'Reilly Media.mht

www-data is the owner as you see, which should be as I’ve chown that …
#prompted for your username/password at all?
* yes for [http://ipnr/webdav](http://ipnr/webdav)
* no for [http:///ipnr/webdav1](http:///ipnr/webdav1)
Both after restart of browser.
Apache error.log (the other log no erro as far I could see)
[Sun Oct 09 11:09:56 2011] [crit] [client 127.0.0.1] (13)Permission denied: /mnt/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable
[Sun Oct 09 11:09:56 2011] [error] [client 127.0.0.1] File does not exist: /var/www/web1/web/favicon.ico, referer: [http://127.0.0.1/webdav1](http://127.0.0.1/webdav1)

---

### Post by andre@home on 2011-10-09
Got it solved...
It was another point of view, but still:  thanks for your input! 

solution:
[http://www.notesofasysadmin.com/unixlinux/curing-symbolic-link-not-allowed-apache-20/#comment-567](http://www.notesofasysadmin.com/unixlinux/curing-symbolic-link-not-allowed-apache-20/#comment-567)
The input is waiting for moderation, so will come soon...

---

