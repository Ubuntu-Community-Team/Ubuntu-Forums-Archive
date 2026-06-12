---
title: "is PHP-PCRE UTF-8 enabled in Ubuntu?"
date: 2012-02-16
forum: Server Platforms
---

### Post by LepeKaname on 2012-02-16
```
Development: Ubuntu Oneiric 32bit
       PHP : 5.3.5-1ubuntu7.4
       PCRE: libpcre3 8.12-3ubuntu2
Production:  Ubuntu Lucid 64bit
       PHP : 5.3.2-1ubuntu4.14
       PCRE: libpcre3 7.8-3build1
```

I'm having some problems with preg_match in PHP, for example:

[PHP]<?php
$str = "&#38272;&#20489;";
if(preg_match("/[&#12288; \t]/", $str)) {
    echo "Contains spaces or tabs";
} else {
    echo "OK";
}
?>[/PHP]

In both (Development and Production) it is reporting that the string (in Japanese) contains spaces or tabs (which is not true). 

There is a quick "fix", using: 

```
preg_match("/(*UTF8)[&#12288; \t\r\n]/", $str))
```

but I'm getting a warning in the Production server (in the Development server seems to work fine): 

> Compilation failed: (*VERB) not recognized ...

At the Production server, **pcretest -C**:
PCRE version 7.8 2008-09-05
Compiled with
  UTF-8 support
  Unicode properties support
  Newline sequence is LF
  \R matches all Unicode newlines
  Internal link size = 2
  POSIX malloc threshold = 10
  Default match limit = 10000000
  Default recursion depth limit = 10000000
  Match recursion uses stack

Which states it supports UTF-8. In phpinfo, it shows the exact same PCRE version (I assume its using the same library). -- so why is not working? --

In the Development server, there is no "pcretest" as it seems it was removed in Maverick.

Anyone knows if PHP-PCRE supports UTF-8 or a way to fix this without having to recompile PHP and PCRE?

Thanks!

---

### Post by LepeKaname on 2012-02-21
Everything was fixed using the "/u" modifier:
[http://php.net/manual/en/reference.pcre.pattern.modifiers.php](http://php.net/manual/en/reference.pcre.pattern.modifiers.php)

:popcorn:

---

