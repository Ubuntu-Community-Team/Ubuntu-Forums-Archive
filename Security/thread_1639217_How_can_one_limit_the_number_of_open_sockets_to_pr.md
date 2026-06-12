---
title: "How can one limit the number of open sockets to prevent exploiting?"
date: 2010-12-06
forum: Security
---

### Post by CyberAngel on 2010-12-06
Hello,

I was searching around and I stumbled upon a Linux Kernel Unix Sockets Local Denial of Service exploit.
I downloaded the exploit, compiled it and ran it to check if I am vulnerable...
As I was expecting, the exploit instantly "killed" my Maverick system and I had to use the power button to reset my computer...
Is there any way to limit the number of allowed open sockets?
I don't think that this can be done using /etc/security/limits.conf in a similar way of preventing the fork bombs.

[http://lkml.org/lkml/headers/2010/11/25/8](http://lkml.org/lkml/headers/2010/11/25/8)
[http://blog.openvz.org/34694.html](http://blog.openvz.org/34694.html)

---

### Post by CharlesA on 2010-12-06
Best thing to do would be to file a bug over on launchpad.

I think it's already listed here: [http://www.ubuntu.com/usn/usn-1023-1](http://www.ubuntu.com/usn/usn-1023-1)

But I am not sure as I don't know the specifics of the exploit.

---

