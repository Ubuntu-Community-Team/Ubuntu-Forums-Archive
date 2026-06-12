---
title: "Django+mod_fcgid+mysite.fcgi 403 Error"
date: 2010-09-20
forum: Server Platforms
---

### Post by Scottix on 2010-09-20
Running 10.04 Ubuntu Server

I have Django installed, when I run the builtin server it works fine.
I wanted Apache to run my Django site automatically and since this is a development platform I wanted it to be the same on the deployment using FastCGI.

I have Apache install, mod_fcgid, and mod_rewrite installed

I setup mysite.fcgi and .htaccess accordingly

I run the ./mysite.fcgi on the server and I get what I expect to see with django.

When I try to run it though the browser I get a 403 error.
You don't have permission to access /mysite.fcgi/ on this server.

I am guessing it has problems accessing stuff somewhere else on the server and I have set www-data as the permission for the site directory not sure where to go from here.

---

### Post by Scottix on 2010-09-20
Found the error, forgot +ExecCGI one of those moments haha.

---

