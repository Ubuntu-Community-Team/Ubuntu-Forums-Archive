---
title: "XAMPP setup question"
date: 2008-07-12
forum: Server Platforms
---

### Post by omarali on 2008-07-12
I just downloaded xampp for linux and installed it in /opt.

When I open the browser and type in locahost it redirects me to /localhost/xampp. How do I stop it from redirecting?

---

### Post by Dr Small on 2008-07-12
Delete /opt/lampp/htdocs/index.html

---

### Post by omarali on 2008-07-12
> **Dr Small said:**
> Delete /opt/lampp/htdocs/index.html

I tried that but the problem still exists. I'm guess the redirect is set somewhere in apache's config files, but I can't find out where.

---

### Post by RHAnthony on 2008-07-12
Are there any virutal hosts setup?
What are the config files defined data dirs?
Are there any error handlers set to that directory?

All common things I've missed in the past years with similar situations :)

---

### Post by omarali on 2008-07-13
> **RHAnthony said:**
> Are there any virutal hosts setup?
What are the config files defined data dirs?
Are there any error handlers set to that directory?

I'm not sure how to check for those things. Everything is still set to the default settings. I just installed xampp today. If you know how xampp does the redirect by default then that's what I need to change.

---

### Post by RHAnthony on 2008-07-13
A default redirect should be in your /etc/apache2/apache2.conf file.  Just look for any line that lists that directory it's sending you to.  You could also grep the entire /etc/apache2 dir for that as well I would think, incase it's in another file.

Are there any symbolic links to that directory on your machine that you know of?

---

