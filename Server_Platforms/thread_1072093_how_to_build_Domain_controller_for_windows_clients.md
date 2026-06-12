---
title: "how to build Domain controller for windows clients?"
date: 2009-02-17
forum: Server Platforms
---

### Post by real_magiz on 2009-02-17
[SIZE=5][FONT=Verdana]Dear all,

I would like to build my domain controller with my Hardy which is without internet.

and it must be used by all windows clients like active directory or novell edirectory for all central adminstration purposes.

thanks
[/FONT][/SIZE]

---

### Post by faustcoder on 2009-04-15
You can use Fedora Directory Server (a LDAP server) and pGINA to auth windows clients against FDS. You can also use FDS or OpenLDAP to sync to AD. Unfortunately there is **NOTHING** like AD if you want items like GPO's etc.

---

### Post by balloooza on 2009-04-15
NO, install ebox, real_magiz (sorry faustcoder I didn;t think so before I started using ebox)

It is magical, ebox-platform.com
and install the repositorys!! no internet access, get the disks from on-disk for $5 (us)
[http://on-disk.com/product_info.php/cPath/28_143/products_id/208](http://on-disk.com/product_info.php/cPath/28_143/products_id/208)

---

