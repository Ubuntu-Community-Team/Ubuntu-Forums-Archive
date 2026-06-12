---
title: "how to create our own option type for hop by hop extention header"
date: 2014-08-19
forum: Ubuntu, Linux and OS Chat
---

### Post by Maninder_Singh on 2014-08-19
Hello guys,

Do you know if we can define our own option type for Hop by hop  extension header ( IPv6 programming ). Say we have a subnet of x number  of routers and I need each of those routers to add some data into the  HBH header of the packets being forwarded. I believe existing option  types won't let me customise the length and value fields. Any suggestion  would be appreciated.


I need an option type which can  store a value of 16 bytes. I can keep first three bits as 001 so that  even if option is unrecognized by the routers, yet the packets will not  be dropped and I can still use it in my own way.



Thanks

---

