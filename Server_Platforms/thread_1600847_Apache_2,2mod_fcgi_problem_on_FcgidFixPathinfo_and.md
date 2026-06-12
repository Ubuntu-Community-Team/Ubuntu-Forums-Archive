---
title: "Apache 2,2/mod_fcgi problem on FcgidFixPathinfo and SSLStrictSNIVHostCheck? Help!"
date: 2010-10-19
forum: Server Platforms
---

### Post by leesiulung on 2010-10-19
I'm running both Ubuntu 9.10 and 10.4 and in both cases installed Apache with mod_fcgi/PHP. 

Problem is the exact same installation steps work on Ubuntu 10.4, but  not on 9.10. I narrowed down the version differences between Apache from  2.2.12-1ubuntu2 and 2.2.14-5ubuntu8.2, but since they are so minor I don't expect major functionality to be missing?

The problems are:

a) SSLStrictSNIVHostCheck

Error Message:
"Invalid command 'SSLStrictSNIVHostCheck', perhaps misspelled or defined by a module not included in the server configuration
  ...fail!"

Setting in httpd.conf:
SSLStrictSNIVHostCheck off

This works just fine on Ubuntu 10.4, but not on Ubuntu 9.10

b) FcgidFixPathinfo 1

Error Message:
"Invalid command 'FcgidFixPathinfo', perhaps misspelled or defined by a module not included in the server configuration
   ...fail!"

Setting in httpd.conf:
FcgidFixPathinfo 1

However, if I instead use the older syntax "PHP_Fix_Pathinfo_Enable" it works! I found that in the Apache 2.2 documentation and it is listed as old syntax!!!

What the heck?

So the questions are:

1. Anyone have any suggestions?

2. Is there really that much compatibility issues between a minor revision? If so, how the heck do people keep this stuff straight when upgrading. That's a pain!

---

