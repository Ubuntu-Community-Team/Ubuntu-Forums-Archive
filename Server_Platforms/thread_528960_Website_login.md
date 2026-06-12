---
title: "Website login"
date: 2007-08-18
forum: Server Platforms
---

### Post by TorchlightJay on 2007-08-18
so, I have an apache webserver and I am hosting a few sites on it. Currently I use good ol' ssh and webmin to edit the webserver and only I have access. Some of the sites on the server aren't mine though and the people want access to mod their own server. I do not want them messing with toher things on the server (email mainly) nor other sites or my network as a whole. How do I setup a web access to my server for my customers without giving them access to everything? I could do webmin or ssh but maybe you have soemthing else in mind. Thanks

---

### Post by a9k on 2007-08-21
How much do they want to "change the server"? If they are just FTP'ing files to their site, that's easy. If they want to install Rails and ZOPE you've got a whole other level of trouble that would probably take Xen to solve.

---

### Post by TorchlightJay on 2007-08-23
I've heard a lot about Rails but know literally nothing about it. What's the 4-11 on it?

---

### Post by a9k on 2007-08-26
Try the rails screencast of making a blog in 15 minutes. It got me interested.
[http://www.rubyonrails.org/screencasts]("http://www.rubyonrails.org/screencasts")

---

