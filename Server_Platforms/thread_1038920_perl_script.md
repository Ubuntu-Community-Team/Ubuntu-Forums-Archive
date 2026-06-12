---
title: "perl script"
date: 2009-01-14
forum: Server Platforms
---

### Post by divinequran on 2009-01-14
Hi,

I am trying to write a perl script, it send's mail to a user i used system(mail -s test) and also send some messages using this.

but my issue is i receive mail with html code like <br> and so..
how to get a plain mail using this system command. thanks in advance.

---

### Post by cmnorton on 2009-01-22
I am confused. Does the content you are trying to send by email already contain html tags? If it does, you may want to write the content, including the html tags, to a temp file, and then pass it through a sed filter to remove the tags.

If you want to send html, you will have to create the page, and insert the content.

---

### Post by xentro on 2009-01-22
Here you have an example

[http://www.cyberciti.biz/faq/how-do-i-send-html-email-from-perl/]("http://www.cyberciti.biz/faq/how-do-i-send-html-email-from-perl/")

---

