---
title: "Adding Python Virtual Host to LAMP Server"
date: 2010-05-22
forum: Server Platforms
---

### Post by mikessong on 2010-05-22
I have an Ubuntu EC2 instance running a site with PHP, MySQL, Apache2.  This works nicely.

I set up a Virtual Host.  It works nicely.

In the virtual host, I want to create a Django site.  I can not break the main server, and I don't yet want to pay for a second permeant instance of EC2.  But, I really want to do the second site using Python/Django.

So, I'm not sure how to do this, without breaking the PHP site.

Could you give some advice.

What packages do I install?

What mods do I add to Apache2 for the Django site?

I guess Django runs in CGI, as opposed to the way PHP scrips are parsed in the public folder.  I build Django sites before, but never set up the server.

What is the best, most sane, way to set up Apache2 for Django for only the Virtual Host or the 2nd host.  If there is no good way to do it, that's fine.

Thanks for your help.

Cheers!
Michael

---

