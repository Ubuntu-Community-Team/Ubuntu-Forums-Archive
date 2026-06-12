---
title: "Once And For All, How Do I Fix An Apache Permissions Error?"
date: 2009-11-26
forum: Server Platforms
---

### Post by charlesviper on 2009-11-26
I am hoping that the responses won't be "RTFM" or just a link to another thread. I have tried fixing a permissions error in Apache 2.2.12. If I type "localhost" into my address bar:

```
403 Forbidden
Forbidden
You don't have permission to access /html/index.html on this server.
Apache/2.2.12 (Ubuntu) Server at localhost Port 80
```

Here's what I've done so far:


[LIST=1]
[*]Install a fresh copy of Ubuntu 9.10 Karmic Koala, desktop edition
[*]Open terminal, type "sudo tasksel"
[*]Select "LAMP" installation and press enter
[*]Open up FireFox and type "localhost" into the browser. It Works!
[*]Drop my files into /var/www/html
[*]Refresh the page: "Forbidden"
[/LIST]

If someone could help me out, I'd really appreciate it. What do I need to do? chmod the entire /www/html folder? Edit settings in a .conf file? There are a million ways methods people suggest to fix a permissions error, but none of them are the same. 

This will use an offline Wikipedia installation (using PHP) as well as static HTML files. The data will only ever be used over a local area network, so security isn't much of a concern -- but it would be best if users couldn't accidentally delete a file.

I know this question gets asked a lot on forums, but there is never a complete response. Considering the installation of LAMP is so basic and uniform -- blank OS, sudo tasksel, done -- there shouldn't be too many variables to hammer out. Help!

---

### Post by Vegan on 2009-11-26
You need to change the permissions if you want the web folder to be something other than /var/www

sudo chmod -R 777 /path/webfolder

where ever you put put web site

---

