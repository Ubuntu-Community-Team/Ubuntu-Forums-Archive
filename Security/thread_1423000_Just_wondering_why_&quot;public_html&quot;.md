---
title: "Just wondering: why &quot;public_html&quot;?"
date: 2010-03-06
forum: Security
---

### Post by _godbout_ on 2010-03-06
Hi guys!

I'm just wondering. Before I used to put my websites on a centos box. Everything in the "var/www/html", and my httpd.conf with virtual hosts having as root document something like "/var/www/html/project". Everything used to work fine, I'm happy :p

Now I see more and more people putting a "public_html" folder in their home folder and making it a symlink to the web content of their projects. And I can't see a reason for that. Also, in that case, why not telling apache to directly point to the web content of the project instead of going through the public_html symlink?

Any idea?
Maybe I'm just missing something because I don't see the use of it.

Thx!!!

---

### Post by DrMelon on 2010-03-06
Some people host multiple websites on one server - having a separate directory for each user that links back to /var/www is good for security reasons.

---

### Post by wmcbrine on 2010-03-06
I think Apache *does* go directly to the content. The symlink is for human convenience (i.e., "cd public_html", and do some edits).

---

### Post by Sef on 2010-03-06
Moved to security discussions.

---

### Post by bodhi.zazen on 2010-03-07
> **_godbout_ said:**
> Hi guys!

I'm just wondering. Before I used to put my websites on a centos box. Everything in the "var/www/html", and my httpd.conf with virtual hosts having as root document something like "/var/www/html/project". Everything used to work fine, I'm happy :p

Now I see more and more people putting a "public_html" folder in their home folder and making it a symlink to the web content of their projects. And I can't see a reason for that. Also, in that case, why not telling apache to directly point to the web content of the project instead of going through the public_html symlink?

Any idea?
Maybe I'm just missing something because I don't see the use of it.

Thx!!!

It is as [DrMelon]("http://ubuntuforums.org/member.php?u=606437") says :

> **DrMelon said:**
> Some people host multiple websites on one server - having a separate directory for each user that links back to /var/www is good for security reasons.

And to expand on that , see :

[http://www.ivankristianto.com/operating-system/ubuntu-linux/howto-make-apache-user-directory-on-ubuntu/1019/](http://www.ivankristianto.com/operating-system/ubuntu-linux/howto-make-apache-user-directory-on-ubuntu/1019/)

mod userdir automates the process, otherwise if you prefer you can hand write virtualhosts.

more secure then allowing Apache to follow sym links ;)

---

