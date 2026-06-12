---
title: "same documentroot but different htaccess and robots.txt"
date: 2011-09-11
forum: Server Platforms
---

### Post by Sifro on 2011-09-11
Hello,

i have foo.com pointing to same document root of bar.com

Both sites have the same contents, but i need separate robots.txt and .htaccess files... I guess it's possible, but how? Could you please point me to the right direction?

Thanks!

---

### Post by zackwasa on 2011-09-11
It's not possible if the docroot is the same

You will need to separate them

---

### Post by tonym on 2011-09-11
Could you not put them in a separate folder and use a RewriteRule?

Regards

Tony

---

