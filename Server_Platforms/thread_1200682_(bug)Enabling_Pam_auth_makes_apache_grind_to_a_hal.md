---
title: "(bug?)Enabling Pam auth makes apache grind to a halt"
date: 2009-06-30
forum: Server Platforms
---

### Post by eont on 2009-06-30
Long story short I decided to setup a webdav share and so far it has been an interesting journey to say the least but after lots and lots of troubleshooting I'm now down to my last problem which so far has taken me an entire day to diagnose :( . If I enable pam authentication loading a directory with lots of subdirectories in it takes ~14 seconds if I disable it it takes about 1 second why is this?

ps:
I've tried to enable regular authentication (as in from a file created with htpasswd) and then it takes roughly 2 seconds


Here is the relevant part from my file /etc/apache2/sites-enabled/000-default 
```

DAVLockDB /var/lock/apache2/DAVLock
Alias /webdav /srv/media
<Location /webdav>
        Dav On
        Options Indexes MultiViews
        IndexOptions FancyIndexing
        AddDefaultCharset UTF-8
        AuthType Basic
        AuthName "WebDAV server"
        AuthPAM_Enabled On
        #AuthPAM_FallThrough Off
        AuthUserFile /etc/shadow
        Require valid-user
        Order allow,deny
        Allow from all
</Location> 
```

---

