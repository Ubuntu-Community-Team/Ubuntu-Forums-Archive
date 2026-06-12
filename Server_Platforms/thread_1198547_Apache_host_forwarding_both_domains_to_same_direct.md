---
title: "Apache host forwarding both domains to same directory even with different folders set"
date: 2009-06-27
forum: Server Platforms
---

### Post by audaciousweb on 2009-06-27
I'm running an Ubuntu cloud server and have installed webmin. I have 2 domain names and have set each one to have a different root directory. For some reason both websites are showing the same directory so one of them is not pointing to the correct directory.

I don't know a lot about server admin so I'm wondering if anyone can point me in the right direction as far as which config files I need to look into changing as just doing it for apache within webmin doesn't seem to be working. Thanks for any help.

---

### Post by LepeKaname on 2009-06-29
Hello,

I suppose you have something like:

```
<VirtualHost *:80>
    ServerName  myfirsthost.com
    DocumentRoot /var/www/
</VirtualHost>
<VirtualHost *:80>
    ServerName  mysecondhost.com
    DocumentRoot /var/other
</VirtualHost>
```

and both are pointing to /var/www/ ...right?

If I remember correctly, it happened to me once and I fixed it
adding at the begging something like:

```
<VirtualHost *:80>
    ServerName myhost
    ServerAlias localhost
    ServerAlias 127.0.0.1
    ServerAlias 192.168.0.1
    DocumentRoot /var/web/root
</VirtualHost>
```

You must have a default path, without it, apache will pick the first VHost.

I can't reproduce it right now, so I'm not sure... 

HINT: It can be related to what you are calling. For example, it may not be the same to enter the URL: "www.myhost.com" from "myhost.com".

So be sure you have something like:
```

<VirtualHost *:80>
    ServerName  myfirsthost.com
    ServerAlias *.myfirsthost.com     (or www.myfirsthost.com)
    DocumentRoot /var/www/first
</VirtualHost>

```

Also the order is very important... sometimes the first virtual host will catch a call to the second and so on...

maybe it helps...

Update: I think this is the same question as:
[http://ubuntuforums.org/showthread.php?p=7533552](http://ubuntuforums.org/showthread.php?p=7533552)

---

