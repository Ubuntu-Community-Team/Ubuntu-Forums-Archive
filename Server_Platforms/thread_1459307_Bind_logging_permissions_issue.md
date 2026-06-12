---
title: "Bind logging permissions issue"
date: 2010-04-21
forum: Server Platforms
---

### Post by stevetmlp on 2010-04-21
****Hello all,

I'd like to get some help with a permissions issue. Have a Hardy BIND server built using Howtoforge tutorial. Here are my logging parameters:

logging {

  channel default_file { file "default.log" versions 3 size 5m; severity dynamic
; print-time yes; };
  channel xfer-in_file { file "xfer-in.log" versions 3 size 5m; severity dynamic
; print-time yes; };
  channel queries_file { file "queries.log" versions 3 size 5m; severity dynamic
; print-time yes; };

  category default { default_file; };
  category xfer-in { xfer-in_file; };
  category queries { queries_file; };
  
};

Here's the syslog errors:

Apr 21 08:58:26 res4 named[7140]: logging channel 'default_file' file 'default.l
og': permission denied
Apr 21 08:58:26 res4 named[7140]: logging channel 'xfer-in_file' file 'xfer-in.l
og': permission denied
Apr 21 08:58:26 res4 named[7140]: logging channel 'queries_file' file 'queries.l
og': permission denied

Here's the permissions settings:

administrator@res4:/etc/bind$ sudo ls -l /var/lib/named/var/cache
total 4
drwxr-xr-x 2 bind bind 4096 2010-04-21 09:10 bind

Can someone help with this?

Thanks

---

### Post by tumandro on 2010-04-21
Try setting the permissions to 777 in chmod and see if it works. If it does you just have a permissions issue.

---

