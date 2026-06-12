---
title: "Problems Running CGI Scripts on Ubuntu"
date: 2008-08-04
forum: Server Platforms
---

### Post by TurboSRT4 on 2008-08-04
Hello everyone, I am a rookie linux user. I set up ubuntu on a computer in my room so i can work on my website. I am seasond in perl and html but always paid for a host. Here is the link [http://96.238.53.88/](http://96.238.53.88/) the page displays the default "it works" page set during install. I have placed index.cgi into /usr/lib/cgi-bin. When i run index.cgi [http://96.238.53.88/cgi-bin/index.cgi](http://96.238.53.88/cgi-bin/index.cgi) i get internal server error. here is the perl file.

#!/usr/bin/perl

print "Content-type: text/html\n\n";
print "<html><h1>Hello!</h1></html>\n";

can someone please give me advice or telnet to my machine and fix it thanks brett

---

### Post by TurboSRT4 on 2008-08-04
please help

---

### Post by Archimedes0212 on 2008-08-04
have you checked the permissions on your cgi file?

Also, I suggest, if you want to save money, when designing, use a service like xampp (linux it is named lampp).  this is just like WAMP except it allows perl as well.  I've always had good experiences with it.

Hope this helps

---

### Post by TurboSRT4 on 2008-08-04
the permissions are 755 and this lamp thing whet the heck is that will u telnet to my machine and jsut get perl runnin for me or tell me how to do it this linux stuff is for the birds
lol.

---

### Post by TurboSRT4 on 2008-08-04
what should the permissions be on cgi-bin and also on index.cgi thanks

---

### Post by StickyStyle on 2008-08-04
Can you show us what's in the apache error log after you try to access the cgi?

```
$tail /var/log/apache2/error.log
```

---

