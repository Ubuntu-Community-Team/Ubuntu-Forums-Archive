---
title: "How can I setup multiple document root for apache in ubuntu?"
date: 2007-07-16
forum: Server Platforms
---

### Post by yinglcs on 2007-07-16
Hi,

In apache, can I do this:
[http://127.0.0.1:/dir1/index.html](http://127.0.0.1:/dir1/index.html)

will go to /var/www/dir1/index.html

and then
[http://127.0.0.1:/dir2/index.html](http://127.0.0.1:/dir2/index.html)

will go to /usr/local/bin/www/dir2/index.html

If yes, can you please tell me how can I do that?

Thank you.

---

### Post by primski on 2007-07-17
Find the line where it says 'DocumentRoot /var/www'

and add this under it:

```

Alias dir2/ /usr/local/bin/www/dir2/

```

or, if u cant find that line add it to file 'default' in folder /etc/apache2/sites-available (assuming u have apache2)

---

