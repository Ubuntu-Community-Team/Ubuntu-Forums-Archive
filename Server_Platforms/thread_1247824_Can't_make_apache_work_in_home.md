---
title: "Can't make apache work in /home"
date: 2009-08-23
forum: Server Platforms
---

### Post by sawatdee on 2009-08-23
I set up a .dev domain to point to web applications that I am currently developing. The name server is set up correctly. I already had another domain called .local where I have my web sites under /usr/local/apache2/htdocs, and that all works perfectly. But the .dev domain gives me "403 Forbidden". The only thing different is that it points to a directory under my home directory where I do my development work. All of the file permissions are exactly the same in my home directory as they are under the .../apache2/htdocs directory. It gives me the 403 error even if I try it with a simple index.html file, blow away my .htaccess file, restart the web server, etc. No luck. Any ideas?

---

### Post by windependence on 2009-08-24
It's not permissions, it's ownership. Your document root should be accessible to user www-data or whatever user apache is using. Consider adding the apache user to your own group and chmod your home to 775.

Just a question, why are you serving out of your /home? You could also symlink your /home to your htdocs directory to achieve the same effect.

-Tim

---

### Post by sawatdee on 2009-08-24
Well, apache uses user daemon and the whole htdocs directory is owned by user and group root. daemon is not a member of root either. But I will try playing around with file ownership and see if that solves the problem.

I am serving from my home directory because that is where I do my development and that way I can edit right on the server and test and debug more quickly. If I used a symlink to htdocs, I would probably have similar permissions/ownership issues, but I will play around with that idea too. I have a different directory where I keep my most stable code under apache's htdocs directory.

---

