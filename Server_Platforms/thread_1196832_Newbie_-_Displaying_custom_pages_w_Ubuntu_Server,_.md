---
title: "Newbie - Displaying custom pages w/ Ubuntu Server, MySQL, Apache2"
date: 2009-06-25
forum: Server Platforms
---

### Post by SysiphusSmile on 2009-06-25
Hey there Ubuntu gurus,

I am trying to accomplish a project, which in your eyes may seem easy, but I am impressed with myself that I have gotten this far! :)

So far I have:

1)Installed Ubuntu server and set it up on a local network
2)Installed Apache2 with PHP5
3)Installed MySQL

I used PHPMyAdmin to create a MySQL database, it is a very basic database that contains server inventory information (for a datacenter) such as serial numbers and when warranty expires.

Now I am stuck.  What I would like to do is be able to point everyone in my department to a page (ex. [http://domain/page](http://domain/page)), and from there they can view all the information in a list or select a link/button that would run a query I have written and bring those results up (such as, HP Blades that were bought in 2006, etc).  

I am trying to minimize the amount of work they have to do to get this information.  

I am a non-gui newbie, and don't know how to do this - or even what to search!

Can anybody point me in the right direction?  I'm not asking you to do it for me, I want to learn, I just don't know where to go :confused:

Thanks!

---

### Post by Wim Sturkenboom on 2009-06-25
[http://dev.mysql.com/tech-resources/articles/ddws/index.html](http://dev.mysql.com/tech-resources/articles/ddws/index.html) helped me on the way a couple of years ago. Note that some of the info might be outdated so some things might no longer work (e.g old variable styles for post and get).

You can search for *database driven website* and *dynamic website*, possibly in combination with *PHP* and/or *MySQL*.

---

### Post by SysiphusSmile on 2009-06-26
Thanks Wim,  That's a good start

---

