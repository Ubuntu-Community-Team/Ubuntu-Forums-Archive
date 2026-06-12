---
title: "Apache2 Secure Login"
date: 2009-07-12
forum: Server Platforms
---

### Post by bbarcelo on 2009-07-12
I've got an apache2 server running a HTTPS only site that is working fine and now I want to add a user name/password to it to secure the entire website. This way, only the home page with the login prompt will be visible to any user not logged in. What's the best way of doing this? I'm not new to apache2 but I'm pretty new to PHP and that seems to be what keeps turning up when I look for this. Could anyone provide a really good step-by-step through how I'd want to set this up (PHP or not)? I don't want to use .htaccess as they don't seem secure enough from my reading and they do not allow user accounts (plus I know how to do that and want to learn something new).

Some notes:
[LIST]
[*]I'll be creating and handling all logins/passwords
[*]I don't have PHP installed
[*]Must be secured (SSL/TLS) for both the login form, page, and transmission
[/LIST]

Thanks for any advice/help!

---

### Post by abaden on 2009-07-13
Coding your own authentication system will take a bit of time, and is probably beyond the scope of what we can cover here. If you want to start learning some PHP, I'd check out [NetTuts.com]("http://net.tutsplus.com/") as well as the [PHP Documentation]("http://www.php.net/docs.php").

Another option is to use a prebuilt authentication and content management system, like [Joomla]("http://www.joomla.org"). Then you can just specify what users you want to have access to specific pages, or simply put your site into maintenance mode to force login for all users.


Alex

---

