---
title: "How do I install .htaccess on my Edgy server?"
date: 2007-02-11
forum: Server Platforms
---

### Post by kenhead on 2007-02-11
Can someone tell me how I install .htaccess on my Ubuntu 6.10 "Edgy Eft" Apache server?

---

### Post by SSamiK on 2007-02-11
Try this: [https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles]("https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles")

Worked for me! :)

---

### Post by jtc on 2007-02-11
You will have to specify [AllowOverride]("http://httpd.apache.org/docs/2.0/mod/core.html#allowoverride") for those directories where you want to use .htaccess

---

### Post by kenhead on 2007-02-11
Thanks, I'll try it.

---

### Post by Brazen on 2007-02-11
[http://httpd.apache.org/docs/2.0/howto/htaccess.html](http://httpd.apache.org/docs/2.0/howto/htaccess.html)

.htaccess files are not "installed."  They are just text files that you put in your Apache website directories.

---

