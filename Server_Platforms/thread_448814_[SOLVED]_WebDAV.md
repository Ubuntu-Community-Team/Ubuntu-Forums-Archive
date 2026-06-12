---
title: "[SOLVED] WebDAV"
date: 2007-05-19
forum: Server Platforms
---

### Post by Megaqwerty on 2007-05-19
Hi, I wanted to use WebDAV on my server so that I could transfer my photos home, while I am away, so I used  [audax321's tutorial]("http://ubuntuforums.org/showthread.php?t=119228&highlight=howto+WebDAV") to get WebDAV set up. The problem is, I can't upload or edit any files on the server.

I have dav and dav_fs modules enabled, and a folder in /var/www/davhome with: ```
drw-r--r--  2 www-data   www-data    4096 2007-05-19 10:44 davhome
``` (I have also tried it with folder permissions set at:) ```
drwxrwxrwx  2 www-data   www-data    4096 2007-05-19 10:44 davhome
```

Here is my /etc/apache2/mods-enabled/dav_fs.conf file:
```
DAVLockDB /var/lock/apache2/DAVLock
#DAVMinTimeout 600

<Location /davhome/>
        Dav On

        AuthType Basic
        AuthName davuser
        AuthUserFile /var/www/davhome/.DAVlogin

        <LimitExcept PUT OPTIONS>
                Require user davuser
        </LimitExcept>
</Location>

```

What did I do wrong?

Thanks,

Megaqwerty

---

### Post by ricrac on 2007-05-19
Did you also do this step?  
htpasswd -c /var/www/davhome/.DAVlogin davuser

Read the .DAVlogin file and make sure "davuser" matches the "Require user" 

Can you retrieve a normal web page from the server?
What errors show in the apache logs when you attempt to use webdav?

---

### Post by Megaqwerty on 2007-05-19
Yes, I can log into the server, I can read files, but I can't modify them, delete them, or add new ones to the server.

Here is my error.log: ```

$ sudo /etc/init.d/apache2 restart
Password:
 * Forcing reload of web server (apache2)...                                                                [ OK ] 
$ tail -f /var/log/apache2/error.log

[Sat May 19 13:20:21 2007] [notice] Apache/2.2.3 (Ubuntu) DAV/2 PHP/5.2.1 configured -- resuming normal operations
[Sat May 19 13:20:53 2007] [error] [client xx.xxx.xxx.xx] Could not DELETE /davhome/show.txt due to a failed precondition (e.g. locks).  [500, #0]
[Sat May 19 13:20:53 2007] [error] [client xx.xxx.xxx.xx] The locks could not be queried for verification against a possible "If:" header.  [500, #0]
[Sat May 19 13:20:53 2007] [error] [client xx.xxx.xxx.xx] Could not open the lock database.  [500, #400]
[Sat May 19 13:20:53 2007] [error] [client xx.xxx.xxx.xx] (13)Permission denied: Could not open property database.  [500, #1]

```

---

### Post by Frosty Cold Drink on 2007-05-19
Check to make sure the lock file exists and is writeable by www-data

---

### Post by ricrac on 2007-05-20
Sorry, didn't notice your conf file error.

The two files that DAVLockDB is suppose to write do not get written.

DAVLockDB /Library/WebServer/DAVLock/

The DAVLockDB directive requires a path to a database file (not directory). Try providing a file-name, ie:

DAVLockDB /Library/WebServer/DAVLock/DAVLockDB

If you do a websearch on your error you'll see many references.

"The locks could not be queried for verification against a possible "If:" header"

---

### Post by Megaqwerty on 2007-05-21
Yeah, thanks.
 I fixed it by creating a blank file with ```
$ sudo touch /var/lock/apache2/DAVLock
$ sudo chown www-data /var/lock/apache2/DAVLock
```

---

### Post by kwilliam on 2007-05-26
Thanks!  That worked for me too!

---

