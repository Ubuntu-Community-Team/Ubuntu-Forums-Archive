---
title: "apache2 is giving me a major headache"
date: 2009-02-14
forum: Server Platforms
---

### Post by D0T-C0M on 2009-02-14
I've got a YaBB perl based forum board running under username:test In order for everything to work I have to(chown -R www-data.test /home/test). 

www-data is the user that apache2 runs under. IF I (chown -R test.test /home/test) and log in to my forum I get "Unable to open ./Members/admin.vars - Permission denied". Not allowed to open files. All directories are chmodded 755.  I can't even FTP in to tranfer files until I chown back to "test" then after chown again to www-data so the forum will run. Ideally I want apache2 to be able to run in the user directories without having to "chown" to "www-data"


I've enabled user directories in /etc/apache2/mods-enabled/user.conf
```

<IfModule mod_userdir.c>
  UserDir public_html
  UserDir disabled root

  <Directory /home/*/public_html>
    AllowOverride FileInfo AuthConfig Limit
    Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
  </Directory>

  <Directory /home/*/public_html/cgi-bin/>
    AllowOverride None
    Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
    Order allow,deny
    Allow from all
    AddHandler cgi-script .cgi .pl
  </Directory>
</IfModule>

```

---

### Post by JeppeM on 2009-02-15
Hey,

If edit /etc/apache2/envvars, you can change the following lines:

```
export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data
```

to

```
export APACHE_RUN_USER=test
export APACHE_RUN_GROUP=test
```

and then restart apache - Now the apache process will run as the user and group test, instead og www-data...

---

### Post by D0T-C0M on 2009-02-15
Thanks for the response.  This would probably work but that wouldn't help the other users on my server.

---

### Post by JeppeM on 2009-02-15
Hmm, ok, i see the problem there...

Argh, it's been a long time since we've set anything like this up, so if i'm on the totally wrong path, then just ignore me :) 

Would be to possible to just chmod 757 or 777 on ./Members/admin.vars and any other file is complains about not having permission to write on?

This is indeed a big problem in general, i know we made it work back in the days, but i dont really remember how :S

---

### Post by khelben1979 on 2009-02-15
Have you tried [the Apache Wiki pages]("http://wiki.apache.org/general/")?

---

### Post by D0T-C0M on 2009-02-15
> **JeppeM said:**
> Hmm, ok, i see the problem there...

Argh, it's been a long time since we've set anything like this up, so if i'm on the totally wrong path, then just ignore me :) 

Would be to possible to just chmod 757 or 777 on ./Members/admin.vars and any other file is complains about not having permission to write on?

This is indeed a big problem in general, i know we made it work back in the days, but i dont really remember how :S

I'd have to change every file but not only that but when apache2 creates a file it creates it with permission 644. The bigger question is why can't the user www-data not be able to read "admin.vars" when it is chmodded 644?  Is there a system setting somewhere maybe overriding the chmod setting?

I'll have a look at the wiki pages.  I can't believe I am the only one that has had problems with this.

---

### Post by D0T-C0M on 2009-02-16
Is it because I don't have suexec enabled? I tried enabling it but renders apache2 useless probably but the following in the suexec.log.```
[2009-02-15 17:55:44]: user mismatch (test instead of www-data)
[2009-02-15 17:56:20]: uid: (1006/test) gid: (0/0) cmd: YaBB.pl
[2009-02-15 17:56:20]: cannot run as forbidden gid (0/YaBB.pl)
```

 I got to make sure I know what I'm doing here because I can open up some security holes. I've been reading a lot trying to get this problem fixed.  Apparently suexec allows apache2 to take over ownership of the user's cgi-bin directory if I read correctly. 

Right now I have 3 web users that can't run perl scripts from there user directory unless I "chown" them to "www-data" . I can't believe that I would be an isolated case?  I've been searching for answers now for days.

---

### Post by rrll1977 on 2009-05-18
Hi all,

Has anybody ever worked with mod_rewrite and mod_userdir on LAMPP?

It appears that mod_rewrite doesn't work with the user's websites (located on /home/user/public_html), although it appears to work fine with the home server websites (on /opt/lampp/htdocs)

Regards

---

