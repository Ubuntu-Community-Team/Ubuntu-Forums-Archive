---
title: "error in my web server (apache2)"
date: 2013-02-11
forum: Server Platforms
---

### Post by mohammad alsharqi on 2013-02-11
hi 

i'd installed videocache program in my ubuntu 10.4 and it works well but i can't access to it and when i try to browse [http://MYSERVERIP/videcache/](http://MYSERVERIP/videcache/) i get this error : 403 forbidden

and after check /var/log/apache2/error.log
i found this error: Directory index forbidden by Options directive: /var/spool/videocache/

please i want help

thanks and bye

---

### Post by lisati on 2013-02-11
*Thread moved to **Server Platforms**.*

---

### Post by SeijiSensei on 2013-02-11
The default in Ubuntu is to forbid options for directories other than /var/www.  Do you have a <Directory "/var/spool/videocache"> entry in your Apache configuration?  If so add "Options +Indexes" in that entry:

```

<Directory "/var/spool/videocache">
   [stuff]
   Options +Indexex
</Directory>

```

Also make sure the Apache user "www-data" has read permissions in that directory.  

```
sudo chmod a+rx /var/www/videocache
```

---

### Post by mohammad alsharqi on 2013-02-11
> **SeijiSensei said:**
> The default in Ubuntu is to forbid options for directories other than /var/www.  Do you have a <Directory "/var/spool/videocache"> entry in your Apache configuration?  If so add "Options +Indexes" in that entry:

```

<Directory "/var/spool/videocache">
   [stuff]
   Options +Indexex
</Directory>

```

Also make sure the Apache user "www-data" has read permissions in that directory.  

```
sudo chmod a+rx /var/www/videocache
```


thanks alot
but sorry i am not prof. in ubuntu . can you tell me where i add this code
<Directory "/var/spool/videocache">
   [stuff]
   Options +Indexex
</Directory>

please type a command that file where exist

---

### Post by SeijiSensei on 2013-02-11
> **mohammad alsharqi said:**
> thanks alot
but sorry i am not prof. in ubuntu . can you tell me where i add this code
<Directory "/var/spool/videocache">
   [stuff]
   Options +Indexex
</Directory>

please type a command that file where exist

First, there's a typo above; it should be "+Indexes".

On Ubuntu, the main configuration file for a web server is /etc/apache2/sites-available/default.  When you installed the video service, it either modified that file, or created a new one in /etc/apache2/sites-available.  See if you can find that file, and see if it has a <Directory "/var/spool/videocache"> entry.  If so, add the Options line to that.

You're going to get better support from the developers of the application you are trying to use than you are asking at a general Linux forum like this one. Since I have never used this application and have no idea how it installs itself, I'll just be shooting in the dark.

---

### Post by koenn on 2013-02-11
> **mohammad alsharqi said:**
> thanks alot
but sorry i am not prof. in ubuntu . can you tell me where i add this code
<Directory "/var/spool/videocache">
   [stuff]
   Options +Indexex
</Directory>

please type a command that file where exist


/etc/apache2/sites-enabled/000-default could work.

but if you had to ask, it's best you read the manual first
[https://help.ubuntu.com/12.04/serverguide/httpd.html](https://help.ubuntu.com/12.04/serverguide/httpd.html)

---

### Post by mohammad alsharqi on 2013-02-11
SeijiSensei, koenn thank you so much

after editing apache configuration and restart apache2 
i get this message 
 
 * Restarting web server apache2
Syntax error on line 5 of /etc/apache2/sites-enabled/000-default:
Invalid command '[stuff]', perhaps misspelled or defined by a module not included in the server configuration
   ...fail!

---

### Post by koenn on 2013-02-11
Sensei, 
there's a syntax error in your stuff, apparently

:)

---

### Post by mohammad alsharqi on 2013-02-11
> **koenn said:**
> Sensei, 
there's a syntax error in your stuff, apparently

:)

hahahaha

but i fixed now by changing the stuff by
<Directory "/var/spool/videocache">
            Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all 
        </Directory>



in all cases thank to Sensei for helping
and for your guiding 
and without you the problem will persist

---

### Post by koenn on 2013-02-11
> **mohammad alsharqi said:**
>  i fixed now by changing the stuff by 
good, you figured that one out. 
:)

---

