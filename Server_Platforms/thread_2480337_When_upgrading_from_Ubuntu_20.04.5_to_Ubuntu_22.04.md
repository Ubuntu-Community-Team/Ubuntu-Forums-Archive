---
title: "When upgrading from Ubuntu 20.04.5 to Ubuntu 22.04.1 pam_auth stops working"
date: 2022-10-26
forum: Server Platforms
---

### Post by adeka on 2022-10-26
I had Ubuntu 20.04.5 LTS and used pam_auth to authenticate users against an Active Directory.
After upgrading to Ubuntu 22.04.1 LTS it stopped working.
It seems that the libpam-radius-auth package is broken.

**The solution** has been to clone the pam_auth project and install the generated package:[INDENT][I]
git clone [https://github.com/FreeRADIUS/pam_radius](https://github.com/FreeRADIUS/pam_radius)
apt install build-essential libpam0g-dev libpam-dev debhelper-compat
cd pam_radius/
make deb && dpkg -i ../libpam-radius-auth_2.0.1_amd64.deb[/I]
[/INDENT]


***[COLOR=#0000cd]Is there any idea when the correct package will be included in the distribution?[/COLOR]***

Best Regards.

---

