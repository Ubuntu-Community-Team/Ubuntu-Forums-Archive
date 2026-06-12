---
title: "ModSecurity: Failed to access DBM file &quot;/tmp//global&quot;"
date: 2013-05-17
forum: Server Platforms
---

### Post by tiolpx on 2013-05-17
Hello,

After chrooting my apache.
watching the error logs i found the following:

```
 ModSecurity: Failed to access DBM file "/tmp//global": No such file or directory
```
```
ModSecurity: Failed to access DBM file "/tmp//ip": No such file or directory
```

in the /etc/modsecurity.conf:
SecTmpDir /tmp/
SecDataDir /tmp/

Any idea ?

---

### Post by tiolpx on 2013-05-17
Problem solved,
I just had to create the directory "tmp" inside the new chrooted folder and give it write permissions for apache user to be able to write to.

BR

---

