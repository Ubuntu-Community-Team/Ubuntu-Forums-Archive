---
title: "Help with escaping characters using sed"
date: 2010-05-06
forum: Server Platforms
---

### Post by altonbr on 2010-05-06
I need to do a search and replace, along with a lot of other patches, on some of my work's software but I can't figure out how/what characters to escape.

I'm trying to find> $_SERVER['DOCUMENT_ROOT']with> '/home/brett/www/svn/'

I've tried running sed with many, all, some characters escaped but it keeps replacing characters and phrases I don't want changed.

Example:```
sed --in-place -e "s/$_SERVER['DOCUMENT_ROOT']/'\/home\/brett\/www\/svn\/'/g" code.php
```
```
sed --in-place -e "s/$_SERVER[\'DOCUMENT_ROOT\']/\'\/home\/brett\/www\/svn\/\'/g" code.php
```

---

### Post by DaithiF on 2010-05-06
Hi, you don't have to use / as the delimiter between the search and replace expressions, for example you could use #, and then you wouldn't need to escape the slashes in your path.  You'll need to escape the $ and [ chars in your search expression.  Something like this:
```
sed -e "s#\$_SERVER\['DOCUMENT_ROOT']#'/home/brett/www/svn/'#" somefile
```

---

### Post by altonbr on 2010-05-06
> **DaithiF said:**
> Hi, you don't have to use / as the delimiter between the search and replace expressions, for example you could use #, and then you wouldn't need to escape the slashes in your path.  You'll need to escape the $ and [ chars in your search expression.  Something like this:
```
sed -e "s#\$_SERVER\['DOCUMENT_ROOT']#'/home/brett/www/svn/'#" somefile
```
That's fantastic and works! Thank you!

---

