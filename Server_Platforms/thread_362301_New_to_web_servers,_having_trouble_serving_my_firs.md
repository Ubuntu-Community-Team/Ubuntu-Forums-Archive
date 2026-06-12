---
title: "New to web servers, having trouble serving my first real page"
date: 2007-02-15
forum: Server Platforms
---

### Post by mjpatey on 2007-02-15
Hello, group-

I'm brand-new to running a server, and am stuck on something probably very basic.  I've installed the following:

```
apt-get install apache2 php5 libapache2-mod-php5
```

... and created a file called index.php, whose contents is "Hello!"  When I point my browser to 127.0.0.1, I get "Hello!"  So far so good.

When I replace that file with a different document whose name used to be "index.htm" (I changed it to "index.php"), I get the following error:

> Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/var/www/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

Is there something about my HTML file that is causing this error?  It runs fine on another server as index.htm.  I thought it was possible to simply change the HTM extension to PHP and it would be recognized as a valid page.

Thanks for any help you may be able to provide!

-Mark

---

### Post by jtc on 2007-02-15
Sounds as if you somehow have gotten insufficient file-permissions on the file, when you transfered in to your server. Somehow the webbserver/php simply aren't allowed to read the file. At least that is my guess. Try making it globally readible.

```
chmod 644 index.php
```

---

### Post by mjpatey on 2007-02-15
That was it!

Thanks for the help... I've been away from Ubuntu and Linux for a while, so things like changing file permissions are still coming back to me, slowly.

Thanks again!

-Mark

---

### Post by digilink on 2007-02-15
Something else to consider would be changing your whole /var/www directory to user www-data as well as for the group and then adding your main user to the www-data group. 

I did this for mine as I wasn't comfortable with root permissions in that directory, not sure if it really makes a difference from a security perspective though.

---

### Post by jtc on 2007-02-15
That sounds like good advice, or simply making your main use the fileowner, if you are the only one using those files. The root-ownership itself isn't neccesary a problem, but indirectly it forces you to use your root/sudo powers more then necessary. To be on the safe side it is always good to be root as seldom as possible.

---

