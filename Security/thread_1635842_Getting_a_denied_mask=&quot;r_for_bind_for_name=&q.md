---
title: "Getting a denied_mask=&quot;r for bind for name=&quot;/usr/local/lib/libGeoIP.so.1.4.6&quot;"
date: 2010-12-02
forum: Security
---

### Post by MechaMechanism on 2010-12-02
Does any one know how to modify the bind apparmor profile to allow reading from name="/usr/local/lib/libGeoIP.so.1.4.6".  The apparmor is the default one that ships with Ubuntu 10.04 by default.

I'm thinking something like...
/usr/local/lib/** r
Or
/usr/local/lib/ r

Which one is correct.

Error message.
```
Dec  2 08:55:58 universal-mechanism kernel: [114310.720001] type=1503 audit(1291305358.425:23):  operation="open" pid=10765 parent=10758 profile="/usr/sbin/named" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/usr/local/lib/libGeoIP.so.1.4.6"
```I included my named apparmor profile as attachment.

---

### Post by MechaMechanism on 2010-12-03
Solved for those who want GeoIP for Bind9.

Put this in your apparmor profile for Bind9.

  /usr/local/lib/** r,
  /usr/local/lib/libGeoIP*.so* m,

The files need to be memory mapped.

EDIT.  It's possible that bind9 needs only access to /lib and not sub-dir.  But I'm too lazy to check.

---

