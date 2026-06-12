---
title: "WebDAV? CalDAV? HUH???"
date: 2005-12-28
forum: Server Platforms
---

### Post by audax321 on 2005-12-28
Hello,

I'm using the latest Sunbird 0.3 alpha 1 ([http://www.mozilla.org/projects/calendar/sunbird.html](http://www.mozilla.org/projects/calendar/sunbird.html)) and was wondering how to share a calendar over the internet. In the old version 0.2 I just used the address to my calendar file via my FTP server. (which doesn't exist anymore since I switched to SSH/sFTP).. but now it is asking for an address to a WebDAV or CalDAV server. How do I set this up???

Thanks. :)

---

### Post by audax321 on 2006-01-09
Anyone? Don't tell me these servers only run on Windows!

---

### Post by shadowman on 2006-01-11
I am not familiar with the sunbird application but I am with webdav.  Webdav is standard with apache2.  Just enable the module with a2enmod and follow the instructions (they are quite trivial, about 3 or 4 entries I think in your apache config file).  You can find the instructions at [http://httpd.apache.org/docs/2.0/mod/mod_dav.html](http://httpd.apache.org/docs/2.0/mod/mod_dav.html)

hth

---

### Post by audax321 on 2006-01-13
Thanks, I'll give it shot as soon as I get a chance... hopefully sometime next week.

---

### Post by nocturn on 2006-01-13
Please post back your experiences, this will be interested for many users.

---

### Post by ottothecow on 2006-01-16
CalDAV is an extension of WebDAV designed for calendars (I think it is supposed to support better multi-user access control) but I dont know much about it or how to work it.

I have however used Sunbird .2 and WebDAV for a long time (with my dreamhost linux server).  WebDAV runs as an apache module and is pretty easy to make work with sunbird (better than FTP at least)

---

### Post by audax321 on 2006-01-17
When I ran a2enmod, it had two modules that sound like they might be needed. One was dav and the other is dav_fs. Do I need both of these or just one?

Also that website says to put something like the following in httpd.conf:


```

DavLockDB /usr/local/apache2/var/DavLock

<Location /foo>
  Dav On

  AuthType Basic
  AuthName DAV
  AuthUserFile user.passwd

  <LimitExcept GET OPTIONS>
    require user admin
  </LimitExcept>
</Location>

```

I'm assuming that I would change /foo to the path where the .ics file for Sunbird would be (e.g. /home/user/calendar), but how do I set up a username/password and get the login to work through SSL?

If possible please provide step-by-step help.. I don't want to accidentally make this computer insecure. Thanks. :)

---

### Post by audax321 on 2006-01-18
Okay, I think I got it working (no SSL though). The only question I have now is, how do I have it so it asks me for a password when reading files from the folder. It only asks me when I have to write to the folder, but I want to restrict reading as well.

---

### Post by audax321 on 2006-01-18
Nevermind, just had to remove GET from the LimitExcept statement.. :)

---

### Post by audax321 on 2006-01-28
Just noticed the how-to I made is up here if anyone else is interested:

[http://ubuntuforums.org/showthread.php?t=119228](http://ubuntuforums.org/showthread.php?t=119228)

---

