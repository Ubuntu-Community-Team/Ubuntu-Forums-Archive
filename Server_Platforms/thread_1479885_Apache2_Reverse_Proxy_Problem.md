---
title: "Apache2 Reverse Proxy Problem"
date: 2010-05-11
forum: Server Platforms
---

### Post by daniele75 on 2010-05-11
Hello, I've this strange problem.

A first server with apache2 installed and configured as reverse proxy, that works great, with this version:

ii  apache2                                                 2.2.9-7ubuntu3.6              Apache HTTP Server metapackage


A second server, with another version of apache2

ii  apache2                         2.2.14-5ubuntu8                   Apache HTTP Server metapackage

that works mostly, but fail with an oma (outlook mobile access) redirection

It works for all reverse sites hosted, but when we try to connect to oma using a nokia phone, it fails.

I can see in access.log that it hangs on FolderSync istance.

I've used wireshark to sniff packets, and in oma server I can see only three way handshaking coming...

Any idea?

My doubt is: when I'll upgrade working server, also it will not work anymore...

Configurations are the same (I've copied /etc/apache2 folder from running one to new one).

Thanks.
Daniele

---

### Post by daniele75 on 2010-05-11
I'm investigating about this problem, I can see that apache2 from new machine don't try to connect to oma server (I've also configured host resolution in /etc/hosts).

I can't see any connection coming from apache2 server to oma server, port 443.

If I try

telnet omaserver 443

from command line, it works...

For some reason, apache2 don't try to connect to oma (iptables is not configured).

Any help will be appreciated.

Daniele

---

