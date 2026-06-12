---
title: "CGI for Individual users"
date: 2011-03-12
forum: Server Platforms
---

### Post by seanmccaskey on 2011-03-12
How can I get Apache to allow CGI from users directories.  It is already working in the default directory.

  I want it to run from /home/*username*/public_html/cgi-bin.  I would like it to be available to several users but not all.  It seems to me I had this working years ago.. but I can't seem to find my notes.](*,)

---

### Post by wongo888 on 2011-03-12
Read up on ScriptAlias and "Options +ExecCGI". How you should proceed will depend on how you have your user dirs set up.

[http://httpd.apache.org/docs/current/howto/cgi.html](http://httpd.apache.org/docs/current/howto/cgi.html)

---

### Post by seanmccaskey on 2011-03-13
I think that will do it.  It is starting to look familiar again.  Thanks for your help

---

### Post by seanmccaskey on 2011-03-13
That did it!  Thanks!

---

