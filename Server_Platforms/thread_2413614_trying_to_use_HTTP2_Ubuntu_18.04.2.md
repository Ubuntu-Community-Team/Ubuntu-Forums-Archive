---
title: "trying to use HTTP2 Ubuntu 18.04.2"
date: 2019-02-27
forum: Server Platforms
---

### Post by psd-joshe on 2019-02-27
I've been trying to get http2 working on my ubuntu 18.04 server for the last few weeks. 

I used the guide located here -> [https://helgeklein.com/blog/2018/11/enabling-http-2-in-apache-on-ubuntu-18-04/?PageSpeed=noscript](https://helgeklein.com/blog/2018/11/enabling-http-2-in-apache-on-ubuntu-18-04/?PageSpeed=noscript)

I was able to get things serving in HTTP2 however I'm having this issue that any kind of load above just me poking around the website will bring apache to its knees for a few minutes. and then it will eventually recover.

the error log will throw out “server reached pm.max_children setting (5), consider raising it”

I tried to meddle with those setting for testing purposes but nothing seems to actually stop apache from locking up.

It seems to me that the problem seems to be related to mpm_event which according to the guide i used is required to use over prefork to use http2.

please let me know if there is any additional info wanted.

---

### Post by psd-joshe on 2019-03-21
is nobody trying to do anything with HTTP2 yet?

---

