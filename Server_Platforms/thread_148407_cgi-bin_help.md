---
title: "cgi-bin help"
date: 2006-03-22
forum: Server Platforms
---

### Post by peanut butter on 2006-03-22
i want to use [http://changepassword.sourceforge.net/](http://changepassword.sourceforge.net/) on my webserver and have a pretty much cleaninstall except for apache2 and samba. could someone please help me.
any help would be appreciated
ubuntu server newby

---

### Post by herrpoon on 2006-03-22
What problems are you having with your cgi-bin exactly?  I know some users who are new to apache etc try and create a cgi-bin, but there should be one located at /usr/lib/cgi-bin/ which you need to know for this:

> configure options:

--enable-cgidir=cgidir		   Absolute path do cgi-bin dir
				   Default: /home/httpd/cgi-bin

Is that what you are looking for?

---

### Post by peanut butter on 2006-03-22
i just didn't know where cgi-bin was located on the filesystem

thank you so much

---

