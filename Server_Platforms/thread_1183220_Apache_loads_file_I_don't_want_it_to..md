---
title: "Apache loads file I don't want it to."
date: 2009-06-09
forum: Server Platforms
---

### Post by guywithcable on 2009-06-09
I'm running Apache, and it seems to be correcting URLs it shouldn't be touching. I have a file named configure.php in a directory that it keeps running when I go to /configure/manage. That directory doesn't exist, but I use it in some rewriting, so I need Apache to give it to the rewriting engine. Even without a .htaccess file, it still executes configure.php when I go to /configure/manage.

Any ideas?

---

### Post by guywithcable on 2009-06-09
Anyone? This is a really persistent and confusing problem.

---

### Post by apel_2804 on 2009-06-10
Ok, I'm not shure if I'm getting it right but...

Maybe it isn't the server which is causing this situation, maybe you should just clear your browsers cache?

---

### Post by guywithcable on 2009-06-13
> **apel_2804 said:**
> Ok, I'm not shure if I'm getting it right but...

Maybe it isn't the server which is causing this situation, maybe you should just clear your browsers cache?

Still not working. :(

---

### Post by Vegan on 2009-06-13
Ignore the problem, there are 10001 reasons for traffic here and there and most of it is due to errors elsewhere. Of course there are bots galore nibbling away.

---

### Post by guywithcable on 2009-06-14
> **Vegan said:**
> Ignore the problem, there are 10001 reasons for traffic here and there and most of it is due to errors elsewhere. Of course there are bots galore nibbling away.

I can't ignore the problem. I need index.php to receive the request, because it parses /configure/manage as variables. I have a .htaccess file that redirects all requests to index.php. It receives other URLs (like /entity/test) fine. But I'm assuming since there's a configure.php file in the project's root, it's calling that for some reason. I need to figure out why it's doing this.

---

