---
title: "Stop directory password protected using htdigest from asking for login on every load?"
date: 2013-03-02
forum: Server Platforms
---

### Post by fatgeek on 2013-03-02
Hey all,

First off, I'm running Ubuntu 11.10 and Apache 2.2.20.

Desdription:  I have a working Apache2 server on my machine. One of the directories is home to a Glype proxy script. Obviously I don't want to give the planet access to my own proxy, so I password protected the directory using digest authentication. It took some fiddling, but I finally got the authentication working. Possibly a little too well. 

When I am using the proxy, every time that I have a page load occur the browser will ask for the login again. I've tried multiple browsers and saved the passwords, and it does the same thing. It is quite annoying. 

The (fake) address to my proxy is http://www.mysite.net/proxy/

I added to following to /etc/apache2/sites-available/default to get the authentication working:

```
 <Directory /var/www/proxy/>
                AllowOverride All
                AuthType Digest
                AuthName "Private"
                AuthDigestDomain /proxy/ http://www.mysite.net/proxy/
                AuthUserFile /path/to/.htdigest
                Require valid-user
        </Directory>
```

Is there a way that I can get it to stop asking for my user/pass every time i load a page?

Googling time on this problem so far: 2.5 hours.

Any help would be appreciated.

---

