---
title: "inherit sticky bit"
date: 2010-03-17
forum: Security
---

### Post by tanoloco on 2010-03-17
Hi guys,

I created a folder with chmod 1770
my umask is 027 and I can have acl control.

I would like users can create files / folder with chmod 1770 inside this folder
in other words I would like to permit users to create files / folder with the sticky bit already on
inside this folder and in any eventual sub-folder.

How can I do it?

Umask seems to affect only the last three digits of chmod  :confused:

Thanks in advance

---

