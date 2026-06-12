---
title: "Execute .rb files from apache2"
date: 2012-03-16
forum: Server Platforms
---

### Post by fizgig on 2012-03-16
Argh!  I've changed the settings in the /etc/apache2/sites-available/my_site file by doing this: [http://www.editrocket.com/articles/ruby_apache_windows.html](http://www.editrocket.com/articles/ruby_apache_windows.html)

Trouble is, when I browse to my ruby file, it still thinks I'm trying to download it instead of execute it.

It's executable, owned by www-data, is called "test.rb" so it has an .rb extension, I've restarted apache2 since I made this change.

Anyone have any ideas?

---

### Post by fizgig on 2012-03-16
Nevermind, the ruby code was causing a problem when run as www-data.  All good now.

---

