---
title: "Setting Up Apache 1.3x LAMP on Dapper"
date: 2006-10-06
forum: Server Platforms
---

### Post by Burgresso on 2006-10-06
I'm trying to set up development LAMP server. Nothing particularly difficult here, but I want to use Apache 1.3x. The specs I'm going for are Apache 1.3x, MySQL 5x, PHP5.

How should I set this up? I've used [these]("https://help.ubuntu.com/community/ApacheMySQLPHP") directions before but they spec Apache 2.x.

The difficulty I'm running into is that in the repositories I don't see packages I think I would need - such as [libapache-mod-php5]("http://packages.debian.org/unstable/web/libapache-mod-php5") - are not in Ubuntu repositories. How should I proceed?

Thank you very much in advance, I appreciate the help!

gracias

burgresso

---

### Post by JLTB on 2006-10-06
In my experience ubuntu doesn't support 'older technology' as much as Debian.  I think you'll have better luck running debian if you want to use Apache 1.3.x.

One other thought, try searching for 'httpd' in the packages.  I seem to remember the renamed some of the apache 1.x packages httpd.

Good luck!

---

### Post by Burgresso on 2006-10-07
Thanks, but I'm am loving Ubuntu and would like to stay with it. It only needs to run well enough to support a localhost, not scale or run large sites.

---

