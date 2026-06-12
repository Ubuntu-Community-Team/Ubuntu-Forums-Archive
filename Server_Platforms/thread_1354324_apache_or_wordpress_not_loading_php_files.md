---
title: "apache or wordpress not loading php files"
date: 2009-12-13
forum: Server Platforms
---

### Post by mellery on 2009-12-13
I'm trying to setup wordpress to run locally, but when I go to [http://192.168.2.200/wordpress/](http://192.168.2.200/wordpress/) I get a directory listing instead of index.php, my .htaccess has

DirectoryIndex index.html index.htm index.php

in it. It was working when I first installed it, but since then i've installed mythtv and changed the wordpress location from localhost to 192.168.2.200 in the config menu, I don't know if those are related to why it stopped working.

Any ideas please?

Here is some more info with what happens when I try loading different pages.

[http://192.168.2.200/wordpress/](http://192.168.2.200/wordpress/)
gives a directory listing

[http://192.168.2.200/wordpress/index.php](http://192.168.2.200/wordpress/index.php)
redirects to [http://192.168.2.200/wordpress/](http://192.168.2.200/wordpress/) and gives directory listing

[http://192.168.2.200/wordpress/wp-blog-header.php](http://192.168.2.200/wordpress/wp-blog-header.php)
gives a blank page

[http://192.168.2.200/wordpress/wp-admin/](http://192.168.2.200/wordpress/wp-admin/)
gives a directory listing

[http://192.168.2.200/wordpress/wp-admin/index.php](http://192.168.2.200/wordpress/wp-admin/index.php)
works

---

### Post by Xiuh on 2009-12-13
Did you install Wordpress based for multiple blogs based off the Debian setup script? To be more specific, there is a script that you may run in the /usr/share/doc/wordpress/examples folder. If you did, this writes up a file in /etc/wordpress named config-whateveryoursitenamewas.php. I belive, not only do you have to change the settings in the console, but you must also modify the php file in the /etc/wordpress folder. I haven't done this, however, below is a link to a doc in Community documentation that describes changing localhost on Wordpress.

[https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

---

### Post by Xiuh on 2009-12-13
I just took a look at my servername.php file in the /etc/wordpress folder. I don't see anything in it controlling the url name, just the upload folder it uses for the site. I may of been wrong in my suggestion above, but I suppose it's still something to check out.

---

### Post by mellery on 2009-12-13
Thanks for the reply.  I followed that when I first setup wordpress and it was working at the time.  Since then I changed the location from localhost to a static ip, and installed mythtv, one of those things must of been done wrong or changed some settings.  I've spent a lot of time searching google and trying things with no luck

---

### Post by Xiuh on 2009-12-14
I'd encourage you to look it over again. The wordpress that is distributed for Debian seems to aim at farming the sites out. That makes it a bit challenging at times. I've had a few minor problems like this and in most cases it was due the files being used outside of the root wordpress folder. /etc/wordpress files and the wp-upload directory. Do you use a custom theme? I believe these are kept separately for each site so multiple sites can have their own theme. This matters because the index.php in the wordpress folder (the file that apache should be sending connections to) will redirect a connection to the index file for the selected theme, which might explain why the admin index page loads up, but the blog site does not.

Another thing it could be or maybe part of the problem is with the permalinks. I won't comment on this because I'm still a bit foggy on the mod_rewrite for Apache that Wordpress will use if enabled. Here's a link though.

[http://codex.wordpress.org/Introduction_to_Blogging#Pretty_Permalinks](http://codex.wordpress.org/Introduction_to_Blogging#Pretty_Permalinks)

---

### Post by mellery on 2009-12-14
I'm using the default theme, I tried the classic theme but the problem remained.  From reading the page about pretty permalinks it looks like it just makes the links more readable, but I followed those instructions too and it didn't change anything.

---

