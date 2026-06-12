---
title: "Server Install"
date: 2006-06-06
forum: Server Platforms
---

### Post by rbrugman on 2006-06-06
Can anyone be so kind as to tell me what the difference is between using the Dapper Server install and using the Breezy CD, typing server and then upgrading to dapper (like I did a while back)?  Does Dapper Server have anything special?


Thanks,
Robert

---

### Post by az on 2006-06-06
[QUOTE=rbrugman]Can anyone be so kind as to tell me what the difference is between using the Dapper Server install and using the Breezy CD, typing server and then upgrading to dapper (like I did a while back)?  Does Dapper Server have anything special?



Thanks,
Robert[/QUOTE]



[http://www.ubuntu.com/download/releasenotes/606](http://www.ubuntu.com/download/releasenotes/606)
Quote:

On the Server
New kernels targeted at server platforms. The server kernels are 

tuned differently than the desktop kernels (providing better performance for server applications). 

There are both low-end, and "big iron" server kernels. The low-end 

server kernel is generic, and should work on the same equipment that the desktop kernel runs on. The highend server kernel is geared towards systems with greater than 8 CPUs (ES7000 / Summit / BIGSMP). 

Turn-key LAMP installation for this common deployment scenario 

Improved support for clusters and SANs 

Numerous thin client enhancements, including faster client startup, 

graphical boot process, reduced memory requirements, and sound device support





So to answer your question, the server release has specialised kernels, and server-specific software.  It is quite different from installing using the server optionin past releases.

---

### Post by rbrugman on 2006-06-07
Thanks for the quick reply.  Since my server is just an old desktop machine with a bunch of hard drives and just runs CUPS, Samba and a couple other thing, I think I'll leave it alone.

---

