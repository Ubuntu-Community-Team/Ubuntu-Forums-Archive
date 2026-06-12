---
title: "server software"
date: 2007-07-12
forum: Server Platforms
---

### Post by ratbastard on 2007-07-12
I want to set up a server that allows remote users (on other networks) to browse Anonymously. 
What server software do I need? 
I want to host a site like Proxify.com or MegaProxy.com

---

### Post by kjacks on 2007-07-14
Assuming you already have a LAMPP server up and running it's quite easy with phpproxy.  Just download a copy of phpproxy from [https://sourceforge.net/projects/phpproxy/](https://sourceforge.net/projects/phpproxy/) and place those files in you /var/www/ directory.  When you navigate to [http://localhost/index.php](http://localhost/index.php) it should work.  

Another alternative would be CGIproxy.

---

### Post by ratbastard on 2007-07-24
did what you suggested: 
getting this error 
Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/var/www/index.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

can anyone make sense of this--

---

