---
title: "Removing x-power-by header"
date: 2011-01-21
forum: Server Platforms
---

### Post by mrhuhk on 2011-01-21
I'm running 10.10 server.  

How do I remove the x-powered-by header?

I tried using Apache headers, that didn't work.  I turned off php_expose.

The only thing that works is going into the actual PHP code and setting the x-powered-by header to null.

This seems like a pain in the *** to disable such a simple thing.  Am I missing the better way?

---

### Post by Thirtysixway on 2011-01-21
> **mrhuhk said:**
> I'm running 10.10 server.  

How do I remove the x-powered-by header?

I tried using Apache headers, that didn't work.  I turned off php_expose.

The only thing that works is going into the actual PHP code and setting the x-powered-by header to null.

This seems like a pain in the *** to disable such a simple thing.  Am I missing the better way?

[http://www.ducea.com/2006/06/16/apache-tips-tricks-hide-php-version-x-powered-by/](http://www.ducea.com/2006/06/16/apache-tips-tricks-hide-php-version-x-powered-by/)

---

### Post by mrhuhk on 2011-01-21
> **Thirtysixway said:**
> [http://www.ducea.com/2006/06/16/apache-tips-tricks-hide-php-version-x-powered-by/](http://www.ducea.com/2006/06/16/apache-tips-tricks-hide-php-version-x-powered-by/)

I already tried that.  Did you bother to read my post?

---

