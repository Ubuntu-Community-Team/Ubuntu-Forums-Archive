---
title: "glob(returns) FALSE on no match when open_basedir is set"
date: 2010-09-14
forum: Server Platforms
---

### Post by megabuffen on 2010-09-14
On my web server the glob() function in PHP will return FALSE when no files are matched, even though the manual clearly states that it should return an empty array. This only happens when open_basedir is set.

Does anyone know why this happens or how I can fix it?

I am running Apache2 with PHP5 on Ubuntu 10.04.1 Lucid.

---

