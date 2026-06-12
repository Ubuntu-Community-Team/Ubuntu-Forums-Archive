---
title: "want to use include files for my headers and footers."
date: 2009-02-17
forum: Server Platforms
---

### Post by kapi on 2009-02-17
want to use include files for my headers and footers.

Have used the statement: <!--#include file="includes/footerInclude.shtml" -->

but nothing happens.

An doing the work on my laptop and wonder if I am supposed to configure the apache server software some way.

any ideas welcome

many thanks

Kapi

---

### Post by cdenley on 2009-02-17
[http://ubuntuforums.org/showthread.php?t=300413](http://ubuntuforums.org/showthread.php?t=300413)

You need to load the "include" module, and configure your site to use SSI.

---

### Post by HermanAB on 2009-02-17
I use the execute flag trick.  You can configure Apache to treat files as SHTML when the execute flag is set:
XBitHack on

Some googling for 'apache shtml xbithack' will get you going.

Cheers,

Herman

---

### Post by kapi on 2009-02-20
Thanks for the input - I went to w3Schools and decided to RTFM haha

now the includes work well in php files

Kapi

---

