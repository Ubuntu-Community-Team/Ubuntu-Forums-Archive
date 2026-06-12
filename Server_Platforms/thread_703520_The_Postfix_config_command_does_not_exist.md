---
title: "The Postfix config command does not exist"
date: 2008-02-21
forum: Server Platforms
---

### Post by midcocc on 2008-02-21
I just followed the install instructions for postfix install 
[https://help.ubuntu.com/7.04/server/C/postfix.html](https://help.ubuntu.com/7.04/server/C/postfix.html)

However, there is no postconf.  
When I try to run postconf it's not found.  When I search for "postconf", there is no file on the server.
thanks
-BT

---

### Post by MJN on 2008-02-21
It should be in /usr/sbin/

(The filelist at [http://packages.ubuntu.com/feisty/i386/postfix/filelist](http://packages.ubuntu.com/feisty/i386/postfix/filelist) confirms this also)

Mathew

---

