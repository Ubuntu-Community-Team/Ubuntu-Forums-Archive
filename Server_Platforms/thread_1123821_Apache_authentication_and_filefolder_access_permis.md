---
title: "Apache authentication and file/folder access permissions"
date: 2009-04-12
forum: Server Platforms
---

### Post by smani on 2009-04-12
Hello,

I am working at a webbased file browser, where users will be able to access, rename, delete, etc files and folders. My question is, what is the best way to handle permissions / authentication with apache? Basically what I am searching for is something that works roughly the same as the windows integrated authentication, where the commands executed on server-side are executed as the user with witch the session was authenticated and hence access is controlled by the usual file/folder permissions. So essentially, is there an authentication method that uses local users of the server and their passwords as credentials?
Thanks for any help!

smani

---

### Post by JochenJung on 2009-04-16
Have a look at the Apache suEXEC module.
I think this is, what you are looking for.

[http://httpd.apache.org/docs/1.3/suexec.html](http://httpd.apache.org/docs/1.3/suexec.html)

---

### Post by smani on 2009-04-16
Thanks for your reply, does indeed look promising.
Just out of curiosity, could someone point me out what the security issues would be if one added the http_user to the sudoers as nopasswd, and then let the server execute controlled and verified php exec statements in the form of
exec("sudo -u username someprog")?
That is with the generous assumption that the site itself does not have any security holes that would allow some user to introduce arbitrary string expressions inside an exec statement and also that the site requires a user to authenticate.

Thanks!

smani

---

### Post by JochenJung on 2009-04-17
Well, each account on your server will be able to change to the http-user without a password. Maybe they could access these users not only via your webpage, but also via SSH. In this case only one of your users has to choose a bad password, so anyone could use this to SSH to your server and stop your webserver deamon.

So its not only about securing the website, that this user authenticates properly. But also any other service, these users are allowed to use on the server.

---

### Post by smani on 2009-04-17
Okay, thanks a lot!

---

