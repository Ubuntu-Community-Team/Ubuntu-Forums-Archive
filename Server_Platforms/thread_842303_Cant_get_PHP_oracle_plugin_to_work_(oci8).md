---
title: "Cant get PHP oracle plugin to work (oci8)"
date: 2008-06-27
forum: Server Platforms
---

### Post by madsporkmurderer on 2008-06-27
I've tried following several how-to articles but none of them have worked. The most successful has been [this one](http://ubuntuforums.org/showthread.php?t=92528) in that it appears to have worked- no errors were brought up and the oci8.so file appeared in /usr/lib/php5/20051025. However even with extension=oci8.so added to the php.ini files there is no mention of it in phpinfo- I assume this means that it hasn't been recognised properly.

Help



Thanks,
Mike

---

### Post by madsporkmurderer on 2008-06-27
Never mind- sorted it; tried running from CLI and found an error with libaio. Turns out libaio wasn't installed- installed it and it's showing up in phpinfo

Mike

---

