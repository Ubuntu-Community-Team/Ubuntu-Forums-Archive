---
title: "CUPS problem with LTSP"
date: 2010-06-22
forum: Server Platforms
---

### Post by rybl on 2010-06-22
I have attempted to install CUPS on an LTSP fat client. Both the client and the server are running Ubuntu 9.10 and cups runs fine on the server. When I try to start it on a client I get this:

```

root@ltsp52:~# service cups start  
* Starting Common Unix Printing System: cupsd  
/usr/sbin/cupsd: error while loading shared libraries: libcupsmime.so.1:  
cannot open shared object file: No such file or directory  
                                                                 [ OK ]  
root@ltsp52:~#

```

libcupsmime.so.1 exists in /usr/lib/libcupsmime.so.1 (the same place it exists on the server). I'm not quite sure what I am doing wrong, but the problem is becoming quite frustrating and any help would be greatly appreciated.

---

