---
title: "webdav : digest authentication"
date: 2010-05-15
forum: Server Platforms
---

### Post by clement.analogue on 2010-05-15
Hello, 

I'm trying to do a webdav on my apache server, but I can't connect. I'm  using Digest authentication. 

cadaver [http://www.forumanalogue.fr/webdav/](http://www.forumanalogue.fr/webdav/) 
Authentication required for webdav on server `[www.forumanalogue.fr':]("http://www.forumanalogue.fr%27/") 
Username: clement 
Password: 
Authentication required for webdav on server `[www.forumanalogue.fr':]("http://www.forumanalogue.fr%27/") 
Username: clement 
Password: 
Could not open collection: 
Could not authenticate to server: rejected Digest challenge 
dav:*/webdav/*? 

Here the logs : 
[Wed May 12 16:42:13 2010] [error] [client 127.0.0.1] GROUP: clement not  in required group(s). 

I enable the folowing mod : dav dav_fs auth_digest 
I create the password file in this way : 
sudo htdigest -c /home/www/www/webdav/passwd.dav webdav clement 

And I add this to my virtual host : 

        <Location /webdav/>
        Dav On
        AuthType Digest
        AuthName "webdav"
        AuthDigestDomain /webdav/
        AuthDigestProvider file
        AuthUserFile /home/www/www/.htdigest
        Require valid-user
        </Location>

But, it doesn't work.

I'm running on Ubuntu 10.04 LTS Lucid Lynx.

Someone has an idea to solve my problem ? 

Thanks.

---

### Post by clement.analogue on 2010-05-21
up

---

### Post by clement.analogue on 2010-07-16
I still have this problem. No one has an idea ?

---

### Post by ar-jar on 2011-10-23
I seem to be having exactly the same issue and would appreciate any hints. Thanks! -Arto

---

### Post by clement.analogue on 2011-10-23
Hi Arto,

I gave up. I asked on the French forum, the French and English Mailing lists, on the apache ML, no one found the origin of the problem or a solution.
Apparently in the Ubuntu package, there are some module which aren't a part of the apache distribution.

---

### Post by Kenny82 on 2013-02-20
Hi, I had the same problem and found that the AuthDigestDomain was wrong - seems similar in your case! Set it to the (web-)location you want to mount.

In the VirtualHost section, I have this Webdav share:

```

    Alias /alice /var/www/data/alice/
    <Location /alice>
        Dav On
        Options +Indexes
        DirectoryIndex none

        AuthType Digest
        AuthName "Chiara@LL"
        AuthDigestDomain /alice/ localhost/alice

        AuthDigestProvider file
        AuthUserFile /var/www/data/passwd.dav
        Require user alice
    </Location>

```

---

