---
title: "php5 without apache"
date: 2008-08-19
forum: Server Platforms
---

### Post by zanlus on 2008-08-19
I'm trying to install php5 but I'm running lighttpd and don't need apache. I can't seem to find any information about how to turn off the apache dependencies from the command line. Any help in doing so would be greatly appreciated.

Thanks!

---

### Post by hufman on 2009-01-07
You need to install php5-cgi, not php5. php5 is a metapackage that include a whole bunch of other stuff, while php5-cgi only provides the cgi connector to php.

---

### Post by Iowan on 2009-01-07
There's also a [php5-cli]("https://launchpad.net/ubuntu/hardy/i386/php5-cli/5.2.3-1ubuntu6") version.

---

