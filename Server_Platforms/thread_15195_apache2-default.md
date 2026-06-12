---
title: "apache2-default"
date: 2005-02-12
forum: Server Platforms
---

### Post by Rock on 2005-02-12
How do it stop forwarding to that?

---

### Post by alastair on 2005-02-12
You might want to explain the question a little more. I might know - but don't understand the question.

---

### Post by Rock on 2005-02-12
Well it doesn't matter now because I fixed this problem.

---

### Post by Chris C on 2005-02-27
How exactly did you do it? I'm having the same problem of only the "Welcome to Apache2" page come up and not having access to any of the other files I uploaded.

What should /etc/apache2/sites-enabled/default and What should /etc/apache2/sites-available/default look like exactly?

---

### Post by Vaxis on 2005-08-03
You have to comment the line
```
RedirectMatch ^/$ /apache2-default/
```
in the file /etc/apache2/sites-available/default.

In other words, change
```
RedirectMatch ^/$ /apache2-default/
```
to
```
#RedirectMatch ^/$ /apache2-default/
```

You might also want to check your *DocumentRoot* entry in the same file. If you want the behaviour you described, it should be set to */var/www*.

I hope that does the trick ;)

---

### Post by LordHunter317 on 2005-08-03
You shouldn't have to do that, provided you put a valid file listed in DirectoryIndex in your webroot.

The redirect match isn't run if a file is already found there.

---

