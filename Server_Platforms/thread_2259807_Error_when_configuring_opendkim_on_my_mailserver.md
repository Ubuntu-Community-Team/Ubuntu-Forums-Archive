---
title: "Error when configuring opendkim on my mailserver"
date: 2015-01-07
forum: Server Platforms
---

### Post by Eloge_Bapfunya on 2015-01-07
Hi all,
I have already finished to install and configure opendkim for our mail server running on zentyal and when I start the module I got this error in my logs:
opendkim filter unable to bind to port 12301@localhost permission denied
There is no other opendkim process which is running and the port is not in use by other program.
Could you help me to figure out the problem?


Thank you in advance.

---

### Post by Eloge_Bapfunya on 2015-01-08
I have already found the source of the problem: I changed the script to launch the service so that it can create the socket at the startup. 
Opendkim is now running but I got this error when I send an email:
> Jan  8 14:30:42 mailserver postfix/cleanup[27884]: warning: milter
inet:localhost:8891: can't read SMFIC_EOH reply packet header: Success Jan  8 14:30:42 mailserver kernel: [15513.957477] opendkim[27641]:
segfault at 7f3821ff6000 ip 00007f38265d82ab sp 00007f3821fe2ee8 error 6 in libc-2.11.1.so[7f3826550000+17f
Could you help me to figure out the problem please.

Thanks in advance.

---

