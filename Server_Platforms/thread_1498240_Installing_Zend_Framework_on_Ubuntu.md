---
title: "Installing Zend Framework on Ubuntu"
date: 2010-05-31
forum: Server Platforms
---

### Post by kar2905 on 2010-05-31
I installed Zend framework for PHP from the Ubuntu repos .. 
Then I created a project using the zf tool named quickstart. 
I add 
[PHP]set_include_path(get_include_path().PATH_SEPARATOR.'/usr/share/php/libzend-framework-php');[/PHP]to the index.php file in the public directory so as to include the library of zend.

I am able to access [http://localhost/quickstart/public/](http://localhost/quickstart/public/) 
but when I create a controller named ActionController using zf create controller Action
then I am not able to access [http://localhost/quickstart/public/account/](http://localhost/quickstart/public/account/)

Pls help

---

### Post by sathyashrayan on 2011-05-29
Do anyone got an answer for this? I am also facing the same problem. When i create a controller I can not able to access with [path]/controllername. I dont see this problem with windows, WAMP or xamp. Even cakephp and codeignetar does not work. I use LAMP. Is there a problem on my lamp installation? My web root path is var/www/*

Any help?

---

