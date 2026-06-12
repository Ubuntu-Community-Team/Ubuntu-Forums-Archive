---
title: "debugging multiple PHP websites with Apache and NetBeans"
date: 2010-08-12
forum: Server Platforms
---

### Post by kidpurple on 2010-08-12
I've just started getting set up for debugging PHP with NetBeans on Ubuntu and I want to know if I'm doing this right.

My project source files live in var/www/project1.  NetBeans and Apache2 are set up to run/debug the project at [http://localhost](http://localhost) rather than [http://localhost/project1](http://localhost/project1).  I want to do that so that I can start an image/anchor tag with a slash and have it know where the root is.  

This setup seems to work fine for a single project but my concern comes when I want to add one or more projects to NetBeans.  Now every time I want to change the project I'm working on I have to tell Apache to change which site is active with the a2ensite and disable the old one with a2dissite.

I know this is a small problem and I can live with it if this is what needs to be done, it just seems like something that should have an easy work around that I have not thought of yet.

Thanks

---

