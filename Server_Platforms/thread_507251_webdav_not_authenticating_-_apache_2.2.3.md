---
title: "webdav not authenticating - apache 2.2.3"
date: 2007-07-22
forum: Server Platforms
---

### Post by psyncho on 2007-07-22
Hi, 

I had webdav working with Ubuntu 6. I'm setting up a new server now with 7 and am running into problems.

I've tried several different configs, here's my latest:
#webdav directories
        Alias /webdav-porcelain /home/webdav/porcelain
        <Location /home/webdav/porcelain>
                Options Indexes MultiViews
                Order Allow,Deny
                Allow from all
                DAV On

                AuthType Basic
                AuthName "webdav-porcelain"
                AuthUserFile /home/webdav/auth/test
                Require valid-user
        </Location>

I have no directory corresponding to this and I get a 403 error when navigating to it with a browser, and cadaver won't find it.

I previously had /var/www-ssl served through encryption, and that was working, then I had
/var/www-ssl/webdav and then I got a 405 error from cadaver though I could least see the webdav dir with a browser through port 443.

I'm just using basic authentication...I've got all the dav mods enabled, I just can't figure it out. Like I said, I had the same config working on my previous server.

I've specified custom logs for ssl and nothing is really coming out in the logs...basically with this config the request is denied from the server configuration.  With the previous configuration, then it seems the authentication wouldn't start...the pages would get served, and encrypted, but the actual authentication never started.

Any help or pointers where I might look would be appreciated. This was so incredibly simple last time so its very frustrating for me that I've now spent 2 days on this.

---

### Post by psyncho on 2007-07-29
I finally found the problem...in my Location block, at the top, where it says "Location"...that should point at the alias, not the actual location of the files i.e.

Alias /webdav-porcelain /home/webdav/porcelain
<Location /webdav-porcelain>
...


Silly me. I've always found that the hardest problems are most often the result of going to fast and thinking too hard. Taking a break always helps.

Cheers, 
John

---

