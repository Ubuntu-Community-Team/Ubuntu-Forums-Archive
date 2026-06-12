---
title: "Subversion Webdav only serves 16k truncated files"
date: 2011-05-18
forum: Server Platforms
---

### Post by jharish on 2011-05-18
I'm using 10.04 on AMD-64. I have Subversion  1.6.6dfsg-2ubuntu1.2 installed with Apache 2.2.14-5ubuntu8.4 and have webdav enabled. 

Right now, firefox4 and Chromium are both only downloading 16k files when a link is clicked on while using Linux and on Windows, IE8 and Firefox4 both had the issue but strangely, Chrome downloaded the full file.

What setting would be controlling this and how would I turn it off? I searched my config files and only found a buffer limit of 16k in my php.ini and I changed that to
realpath_cache_size = 1024M
(From /etc/php5/apache2/php.ini)

Any ideas what might be causing this behavior?

---

### Post by jharish on 2011-05-19
Let me know if I should provide any configuration files to help troubleshoot. I'll post them here, but since several are huge, I'll hold off until someone suggests I post one.

---

