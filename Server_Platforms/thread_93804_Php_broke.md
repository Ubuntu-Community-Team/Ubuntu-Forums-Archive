---
title: "Php broke"
date: 2005-11-22
forum: Server Platforms
---

### Post by 3dmaker on 2005-11-22
I have no idea what happend. Now on my local machine whenever I click a php file in firefox like (http://localhost/test.php"), it tries to save the file instead of opening and showing it. What happend?

---

### Post by narcolept on 2005-11-22
Have you edited your httpd/apache config? I would check there first and see if the module for php is still being added and loaded.  should look like "AddModule php4.c<etc" and the same for LoadModule.  I'm just assuming that you're talking about php installed on a local machine, and not that you're trying to view a site elesewhere that isn't displaying php properly, of course.

---

### Post by 3dmaker on 2005-11-22
Yeah I am talking about it on my local machiene. I will look at the httpd file now.
Edit:
I dont seam to have an httpd file on the computer.

---

### Post by narcolept on 2005-11-23
I don't run apache2 or ubuntu on any machines I serve web stuff from. I would check /etc/apache2 though, I believe. should be a /conf directory under it with the config in it.  I am a little fuzzy on where an apache2 config is precisely though.

---

