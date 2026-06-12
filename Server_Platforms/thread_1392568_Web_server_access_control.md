---
title: "Web server access control"
date: 2010-01-28
forum: Server Platforms
---

### Post by John Rivera on 2010-01-28
I have ubuntu based web server running in home which I use for varying purposes.
Now I have ran to situation that I would like ton set "access control" for my server so that on main page user can login and then he/she sees that what sites on server he can access.

Basically this would be simple to do with .htaccess protection, but it would be per directory solution and this is not so easy to manage.

However what I wish to get done here is that there would be access control check and an login prompt on webserver document root which would require to authenticate if heading to non public section of webserver.

currently I got my server root like this
/var/www (server root, no website and here would come access control point)
/var/www/site1 (primary website on my server to where most of visitors are going to)
/var/www/site2 (secondary site for specific things on my server)
/var/www/directory1/site3 (site which I do wish to have for closed group only)
/var/www/directory2/site4 (my online education and studying portal which I wish to control)

And I would want to allow everyone to access site1 and site2 without any restriction

Now what kind of solution would work here ?
I am not sure and I don't have full techical knowledge of making this reality, so I would like to have some help.

There probably is multiple ways to do this and one could be .htaccess control, however what I wish to have is an easy to manage system which is also expandable.

---

### Post by ICEB3AR on 2010-01-28
Do you have a domain/more than one for your webserver?
You could easily use subdomains to access the specific directories and in this use htaccess and htpasswd for access control.

---

### Post by John Rivera on 2010-01-28
No and even then it would bounce to starting point where to use .htaccess for access control.
For that I found instructions and it is fustrating if I need to manage access control per individual directory and there is multiple directories.

Reason why I need to get this done is that I have confidential and classified content coming to my server for which I need to have suffient protection against prying eyes. And yes that is legal obligation for me as server administrator.

---

