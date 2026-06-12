---
title: "phpMyAdmin and php5-cgi with suPHP"
date: 2009-01-14
forum: Server Platforms
---

### Post by dmuir on 2009-01-14
I had things working in Hardy reasonably well, and decided to upgrade to Intrepid over Christmas. Thought everything was working dandy until I tried to access phpmyadmin yesterday. Seems like it's decided that it doesn't want to process php files for phpmyadmin, and instead asks me what I want to do with the file.

So after a pile of trial and error, I finally got it working, but had to download phpMyAdmin 3 and put it in the normal document root. It still tries to download index.php if I go to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/), but not if I got to [http://localhost/phpmyadmin/index.php](http://localhost/phpmyadmin/index.php). For the latter case, everything works as expected.
Oddly enough, all my other projects are able to resolve index.php without any issues (eg: [http://localhost/project1/](http://localhost/project1/) works).

As you can probably tell from the title, I'm using php5-cgi instead of mod_php5 so that I can run things with suPHP.

Any help getting Ubuntu's phpmyadmin working again would be much appreciated.

---

