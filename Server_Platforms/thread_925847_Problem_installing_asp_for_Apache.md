---
title: "Problem installing asp for Apache"
date: 2008-09-21
forum: Server Platforms
---

### Post by yodomino6 on 2008-09-21
I'm trying to install ASP for Apache on my 8.04 server. I did some Googling and discovered that I need to run the following command:
```
sudo aptitude install mono-apache-server2 libapache2-mod-mono
```

The problem is, I keep getting messages like:

```
Couldn't find any package whose name or description matched "mono-apache-server2
"
No candidate version found for libapache2-mod-mono
Couldn't find any package whose name or description matched "mono-apache-server2
"
No candidate version found for libapache2-mod-mono
No Packages will be installed, upgraded, or removed.
```

I've tried several different variations of similar commands, and all give back similar responses.
Yes, it's connected to the internet :)

---

### Post by gpredrag on 2008-09-21
It works here,
Those packages are in universe repository
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by Vegan on 2008-09-21
Try this page. I will warn you, what you want is hard to implement. Linux is Apache, MySQL, PHP and Perl etc.

Microsoft uses IIS, Visual Basic and C#. There is a world of difference to be overcome.

[http://www.codeproject.com/KB/cross-platform/introtomono2.aspx?print=true](http://www.codeproject.com/KB/cross-platform/introtomono2.aspx?print=true)

---

### Post by yodomino6 on 2008-09-21
Thanks, that worked! Now my only other question is that I would like to run asp, not aspx. Is there a way to do that? Everything I find seems to be for ASP.NET

---

### Post by gpredrag on 2008-09-22
Well, as Vegas has pointed...
ASP (as in server side vbscript or jscript) is not exactly supported on linux. Closest thing would be Apache2 ASP,
check [http://www.devstack.com/]("http://www.devstack.com/"),
or [http://search.cpan.org/dist/Apache2-ASP/]("http://search.cpan.org/dist/Apache2-ASP/"), there are ubuntu packages in the repositories also. It uses Perl, but also has Global.asa and tries to be like ASP
PHP is also about embedding code into HTML, and is well documented and tested on Linux ( it's at home on Linux).
So, If you are not into testing .net on Linux, but rather into server side scripting, you should try one of the above.

---

