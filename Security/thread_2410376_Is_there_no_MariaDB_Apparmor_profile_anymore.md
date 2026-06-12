---
title: "Is there no MariaDB Apparmor profile anymore?"
date: 2019-01-14
forum: Security
---

### Post by espressobeanie on 2019-01-14
Hi,

I'm trying to setup my Apparmor with MariaDB and I'm not seeing that there's a profile for MariaDB that appears. I have one for MySQL, but even with MariaDB installed, Apparmor is unable to find it and activate the profile for it. I saw it did work previously, but I'm not sure why not on Ubuntu Bionic.

Thanks

---

### Post by deadflowr on 2019-01-14
Mariadb-servers come with a disclaimer in place of the apparmor profiles in the /etc/apparmor.d/usr.sbin.mysqld file that reads:
> # This file is intensionally empty to disable apparmor by default for newer
# versions of MariaDB, while providing seamless upgrade from older versions
# and from mysql, where apparmor is used.
#
# By default, we do not want to have any apparmor profile for the MariaDB
# server. It does not provide much useful functionality/security, and causes
# several problems for users who often are not even aware that apparmor
# exists and runs on their system.
#
# Users can modify and maintain their own profile, and in this case it will
# be used.
#
# When upgrading from previous version, users who modified the profile
# will be promptet to keep or discard it, while for default installs
# we will automatically disable the profile.

i guess that means no more default profiles, but you are totally free to make one or try to reuse one.

---

### Post by espressobeanie on 2019-01-16
Is there a MySQL apparmor profile?

---

### Post by deadflowr on 2019-01-17
> **espressobeanie said:**
> Is there a MySQL apparmor profile?

Yes

---

### Post by espressobeanie on 2019-01-17
Ah I see the issue. It doesn't appear to have ported over to 18.04 the same way as 16.04. something about installing mysql-source-5.7 to somehow get the profile. Thanks!

---

