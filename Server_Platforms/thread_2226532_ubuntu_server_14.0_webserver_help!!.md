---
title: "ubuntu server 14.0 webserver help!!"
date: 2014-05-27
forum: Server Platforms
---

### Post by christian26 on 2014-05-27
i having a hard time triying to configure apache2 i re-code index.html and add some picture for some reason i can see the web site but not images at all please i need some help. thank you

<img src="/var/www/html/ms1.jpg" alt="musicianspaces" width="1075" height="600">

sudo chmod 777 /var/www/html/ms1.jpg

---

### Post by Doug S on 2014-05-27
Instead of this```
<img src="/var/www/html/ms1.jpg" alt="musicianspaces" width="1075" height="600">
```do this```
<img src="./ms1.jpg" alt="musicianspaces" width="1075" height="600">
```

---

### Post by christian26 on 2014-05-28
damm one dot revolved hours of headches thanks a lot :)

---

### Post by SeijiSensei on 2014-05-29
Well, the more important reason is that <img src> requires the URL, not the path on the local computer.  All the links in an HTML document use the external URL addresses.  It's not because of the dot, it's because
```
./ms1.jpg
```
is a *relative* URL.  It expands to
```
http://www.example.com/ms1.jpg
```

---

### Post by Doug S on 2014-05-29
@ Seiji : Thanks. I was in a hurry when I replied and didn't give the expanded explanation. I had meant to come back and give more information.

If I might take it a step further, the original link would have looked for this file: /var/www/html/var/www/html/ms1.jpg

---

