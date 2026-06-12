---
title: "Zip a WWW directory"
date: 2006-12-06
forum: Server Platforms
---

### Post by cpminga on 2006-12-06
I have a friend who wants me to download all of his site's files. (IIS/PHP) Is there a way to compress all of those files on the server before downloading them? (prefferablely a tar ball but zip'll do). All I have is ftp access to the server. I'm thinking something along the lines of a PHP script? Any help would be GREATLY appreciated! Thank you.

---

### Post by tturrisi on 2006-12-07
php will work IF php on the server was compiled with zip to begin with.  Unlikely on IIS.  Why not just ftp in and select all folders & files and download to a new dir?  Should take a minute or two at best on broadband.

---

### Post by cpminga on 2006-12-07
> **tturrisi said:**
> Why not just ftp in and select all folders & files and download to a new dir?  Should take a minute or two at best on broadband.

Yeah, that's what I wound up doing last night. My friend said it would take a long time but it wasn't too bad. About 20-30 minutes. The only problem I'm having now is that I think there's a problem with dos to unix conversion.

This is what the page is supposed to look like

[http://halaween.net/index.html](http://halaween.net/index.html) (IIS)

and this is what I get

[http://elebug.com/halaween/index.html](http://elebug.com/halaween/index.html) (Apache)

Any thoughts on how this could be easily converted for multiple files?

---

### Post by tturrisi on 2006-12-07
[http://elebug.com/halaween/index.html](http://elebug.com/halaween/index.html) will not load for me.

---

### Post by hockey97 on 2007-02-17
Hi I need help, I want to unzip a zip file how can you do this?? I am new to linux ect, I tried unzip "filename" and I get a response saying no command found and then I did man unzip and it then said no manuel found.  Do I need to install any zip program or packages for this to work??

---

### Post by hockey97 on 2007-02-24
Is their any command that I can check is my database and ftp and domain name are all up and running like I would like to see if thier are error's with any database, I know my webserver is up and running becuse I put in ie localhost.

also is their any way to get around isp's like so you can have our own custom domain name like [www.somthing.com](www.somthing.com) in that order??  I got a domain namer server but don't know how to get my custom domain name up and running.

Thanks for your time.

---

