---
title: "well mod_rewrite is loaded but why doesnt this code work?"
date: 2005-10-12
forum: Server Platforms
---

### Post by gnomes on 2005-10-12
i can see that its loaded with phpinfo, and i can test its conf file because i redirected / to [http://gooogle.com](http://gooogle.com) and it worked.

so why doesnt this line work?
```

RewriteRule ^([A-Za-z0-9-]+).([A-Za-z0-9-]+)/?$ index.php?action=view&filename=$1.$2


```
eh?

mysite.com/pic.jpg should go to
mysite.com/index.php?aciton=view&filename=pic.jpg

but it doesnt redirect me anywhere :(

---

### Post by simon w on 2005-10-13
Try adding this before the rule.
```
RewriteEngine On
```

---

### Post by majikstreet on 2005-10-13
[QUOTE=simon w]Try adding this before the rule.
```
RewriteEngine On
```[/QUOTE]
I bet that'll work.

---

### Post by XtremeGamer99 on 2005-10-13
I'm having the same problem. And yes, I have it on. -_-

---

