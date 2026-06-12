---
title: "Configuring mime types in squid."
date: 2006-10-02
forum: Server Platforms
---

### Post by epilas on 2006-10-02
I want to configure some mime types in squid to be denied. Those are types like msn messenger, video files, audio files, etc.How can i do that?Is there any guide cause mime.types and mime.conf files really confused me.Thanks in advance.

---

### Post by baastie on 2006-10-02
Hi,

I think you would have to create something like these lines
in your squid.conf.

acl BLOCK url_regex "/etc/squid/block.acl"

BLOCK is ACL name, the function is url_regex and what to blok is found in the block.acl file ( here you would put something like asx or X-MSN-Messenger oid ) .

And then create an rule to block the BLOCK acl:

http_access deny BLOCK

Cheers

---

### Post by epilas on 2006-10-09
This helped but only a bit.Is there any how to guide i can use anywhere?

---

### Post by epilas on 2006-10-11
Well finally found my way out of this.Visit 
[http://epilas.blogspot.com](http://epilas.blogspot.com) 
for instructions and example access lists.

---

