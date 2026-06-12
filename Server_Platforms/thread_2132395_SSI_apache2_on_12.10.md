---
title: "SSI apache2 on 12.10"
date: 2013-04-04
forum: Server Platforms
---

### Post by blwegrzyn on 2013-04-04
i followed this guide:
[https://help.ubuntu.com/community/ServerSideIncludes](https://help.ubuntu.com/community/ServerSideIncludes)

ssi works but i cannot get main page automatically through index.shtml

the page starts and tries to start the download instead of open the page
application type is: application/x-trash (160 bytes)

any ideas?

---

### Post by Doug S on 2013-04-04
I worked through every step of the reference link you gave, last year during the 12.04 release cycle. Actually, it was me that made the last several edits to that web page.
I do not have a 12.10 server to test with, but the only thing I see as obviously wrong is the restart apache part which should now be:```
sudo service apache2 restart

```instead of what was shown (I have now changed it).
Did you try the simple example page as on the reference page?
I do not understand what you mean by> application type is: application/x-trash (160 bytes)
or what x-trash means as an application type. I'm not sure what to suggest.

---

### Post by blwegrzyn on 2013-04-04
I followed all steps and simple shtml works if I point the browser to shtml directly , if I go to just the page like domain.com it opens a download prompt and tries to download a page of type I described above

---

### Post by Doug S on 2013-04-04
Hmmm... I seem to have an extra line in one of my files that is not described in the reference wiki. Try it:```
doug@s15:/etc/apache2/sites-available$ [COLOR=#ff0000]diff -u default.original default.doug[/COLOR]
--- default.original    2012-03-16 23:43:16.519423937 -0700
+++ default.doug        2012-03-18 11:41:06.158822552 -0700
@@ -7,10 +7,11 @@
                AllowOverride None
        </Directory>
        <Directory /var/www/>
-               Options Indexes FollowSymLinks MultiViews
+               Options Indexes FollowSymLinks MultiViews Includes
                AllowOverride None
                Order allow,deny
                allow from all
+               DirectoryIndex index.shtml
        </Directory>
        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
```I did my tests in my user directory, but will try some stuff in /var/www if you continue to have troubles. Of course, the operational file name is "default", my diff above was on my various backup copies.

---

### Post by blwegrzyn on 2013-04-04
> **Doug S said:**
> Hmmm... I seem to have an extra line in one of my files that is not described in the reference wiki. Try it:```
doug@s15:/etc/apache2/sites-available$ [COLOR=#ff0000]diff -u default.original default.doug[/COLOR]
--- default.original    2012-03-16 23:43:16.519423937 -0700
+++ default.doug        2012-03-18 11:41:06.158822552 -0700
@@ -7,10 +7,11 @@
                AllowOverride None
        </Directory>
        <Directory /var/www/>
-               Options Indexes FollowSymLinks MultiViews
+               Options Indexes FollowSymLinks MultiViews Includes
                AllowOverride None
                Order allow,deny
                allow from all
+               DirectoryIndex index.shtml
        </Directory>
        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
```I did my tests in my user directory, but will try some stuff in /var/www if you continue to have troubles. Of course, the operational file name is "default", my diff above was on my various backup copies.

This fixed the issue right away. txh

So, what is the purpose of:
"
If you want includes in index pages then edit the /etc/apache2/mods-availables/dir.conf file from this:

<IfModule mod_dir.c>
          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
</IfModule>

to this (indent changed to fit onto one line in this document):

<IfModule mod_dir.c>
 DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm index.shtml
</IfModule>
"

if it does not work?

---

### Post by Doug S on 2013-04-04
I do not know. On my system, I actually have the line in the default file commented out, and it works, or not, as per the dir.conf file. I do not know why your system seems to be different. I tried my simple index.shtml file in var/www and it works as per the wiki page. If we could figure out the difference, then the wiki could be updated for the next person.

---

### Post by blwegrzyn on 2013-04-05
I tried remove all setup i had and make it minimalistic and i still needed DirectoryIndex.

---

### Post by Doug S on 2013-04-05
blwegrzyn, I wonder if you would bear with me a little while and try to figure out the difference between our two systems, with the goal of editing the wiki reference.

I have re-done all of my tests also, and even added some more. Summary: If I have the index.shtml added to the end of the line in the dir.conf file, then I do ***not*** need the "DirectoryIndex index.shtml" in the default file. If I do ***not*** have the index.shtml added to the end of the line in the dir.conf file, then I do need the "DirectoryIndex index.shtml" in the default file. This is regardless of having "Options Indexes" or not. I do not have an .htaccess file at the /var/www level. I do have dir.conf enabled:```
doug@s15:/etc/apache2$ [COLOR=#ff0000]ls -l mods-enabled/dir*[/COLOR]
lrwxrwxrwx 1 root root 26 Mar 14  2012 mods-enabled/dir.conf -> ../mods-available/dir.conf
lrwxrwxrwx 1 root root 26 Mar 14  2012 mods-enabled/dir.load -> ../mods-available/dir.load
```

---

### Post by blwegrzyn on 2013-04-05
Below is the setup when it fails.


ubuntu@:/etc/apache2$ sudo ls -l mods-enabled/dir*
lrwxrwxrwx 1 root root 26 Mar 25 15:42 mods-enabled/dir.conf -> ../mods-available/dir.conf
lrwxrwxrwx 1 root root 26 Mar 25 15:42 mods-enabled/dir.load -> ../mods-available/dir.load
ubuntu@:/etc/apache2$


ubuntu@:/etc/apache2$ cat mods-enabled/dir.conf
<IfModule mod_dir.c>

          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htmi index.shtml

</IfModule>
ubuntu@:/etc/apache2$

ubuntu@:/etc/apache2$ cat sites-available/default
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews Includes +Includes
                AllowOverride None
                Order allow,deny
                allow from all
                #DirectoryIndex index.shtml
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

---

### Post by Doug S on 2013-04-05
Well, I cann't figure it out. I did not have apache installed on my 13.04 test server, so I installed it and tried everything there. All was as I expected. I tried your exact files on my 12.04 server, same.
I'm reluctant to make a change to the wiki page without knowing why.

By the way, it doesn't matter, but This line:```
Options Indexes FollowSymLinks MultiViews Includes [COLOR=#ff0000]+Includes[/COLOR]
```can be this:```
Options Indexes FollowSymLinks MultiViews Includes
```And I think there is a typo in this line:```
DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm[COLOR=#ff0000]i [/COLOR]index.shtml
```and it should be:```
DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm index.shtml
```

---

