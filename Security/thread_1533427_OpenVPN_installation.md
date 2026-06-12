---
title: "OpenVPN installation"
date: 2010-07-17
forum: Security
---

### Post by cob on 2010-07-17
I just installed OpenVPN using apt, and it doesn't seem to have components which are distributed with the source, such as easy-rsa.  Why would tools like this be excluded from the package?  I prefer to use apt rather than compiling from source, to keep things neat and simple.

---

### Post by gombadi on 2010-07-18
If you installed openvpn by apt then have a look in /usr/share/doc/openvpn/examples/easy-rsa

---

### Post by awi on 2010-07-18
OpenVPN is not a "turn key" solution. You have to create several keys and configuration files in order to have it working.
Check the site quickstart:

[http://www.openvpn.net/index.php/open-source/documentation/howto.html#quick](http://www.openvpn.net/index.php/open-source/documentation/howto.html#quick)

---

