---
title: "Server 11.10 Book"
date: 2011-11-11
forum: Server Platforms
---

### Post by Justinba1010 on 2011-11-11
[FONT=Times New Roman]Is there a book on Ubuntu server 11.10, more importantly to me, 12.04? That goes over LAMP and PostgreSQL and DNS. Also I don't know the name, but is there a way to make 4-5 servers on 1 domain on like 
s1.mydomain.com
s2.mydomain.com
mydomain.com
s3.mydomain.com
etc?


On different servers?

Thanks. [/FONT]

---

### Post by MG&amp;TL on 2011-11-11
There's probably lots of books available but in the meantime (while your book comes!):

[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by Justinba1010 on 2011-11-12
Thank You! But also I have been very miscocieving the .deb compiling? Could you send me a link on that too. Thank you.

---

### Post by MG&amp;TL on 2011-11-13
.deb. compiling? You mean building a debian package from source code?

[https://wiki.ubuntu.com/PackagingGuide/Complete]("https://wiki.ubuntu.com/PackagingGuide/Complete")

Basically, in a few steps, create a debian directory, edit it, then run debuild to build the deb. But of course, the link is much more useful.

If you mean installing them:

```
sudo dpkg -i <file>.deb
```

---

### Post by cariboo on 2011-11-14
Check the server documentation wiki at:

[https://help.ubuntu.com/11.10/serverguide/C](https://help.ubuntu.com/11.10/serverguide/C)

---

