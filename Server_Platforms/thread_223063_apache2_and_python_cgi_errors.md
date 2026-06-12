---
title: "apache2 and python cgi errors"
date: 2006-07-25
forum: Server Platforms
---

### Post by grendelkhan on 2006-07-25
I'm trying to configure ViewVC on Ubuntu6.06 and rather than executing python cgi scripts, apache2 is only displaying them.

mod_python is enabled and showing in the server signature, the files are 755 and owned by www-data, does anyone have any ideas here?  I'm pulling my hair out!!

---

### Post by mexlinux on 2006-08-30
Does anyone knows how to get mod_python to work???
I'm also pulling my hair!
I have done things exactly as stated in the docs....
I have gone to the mod_pyhton faq.....:
[http://www.modpython.org/FAQ/faqw.py?req=show&file=faq02.004.htp]("http://www.modpython.org/FAQ/faqw.py?req=show&file=faq02.004.htp")
But answer is useless

---

### Post by theunseen14 on 2008-03-25
Here is what I tried using Gutsy and apache 2.2.4.

I created this line in apache2.conf

ScriptAlias /viewvc /usr/lib/cgi-bin/viewvc.cgi

that coupled with a properly configured /etc/viewvc/viewvc.conf (I just configured the repositories I am using) and all should be well.

---

