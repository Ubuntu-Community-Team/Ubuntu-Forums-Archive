---
title: "can't remove courier-imap"
date: 2009-10-15
forum: Server Platforms
---

### Post by richard42 on 2009-10-15
I can't uninstall courier-imap.  When I run:

```
apt-get remove courier-imap
```

I get the following error:

```
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Anyone got any ideas how to get rid of it?

---

### Post by timothy_tim on 2009-10-15
I guess some other installation depends on it.
```
$ apt-cache rdepends courier-imap
courier-imap
Reverse Depends:
 |phpgroupware-0.9.16-core
  dtc-postfix-courier
  couriergraph
  courier-imap-ssl
  courier-base
```Maybe uninstalling some of these will help.

But I'm no expert so uninstall only one of these packages if you're sure you don't need them anymore.

---

### Post by richard42 on 2009-10-15
Thanks for your thoughts Tim.

Eventually, I resolved the problem by following the instructions here:

[http://itechlog.com/linux/2008/12/18/fix-broken-package-ubuntu/]("http://itechlog.com/linux/2008/12/18/fix-broken-package-ubuntu/")

---

