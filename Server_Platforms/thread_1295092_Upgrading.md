---
title: "Upgrading"
date: 2009-10-19
forum: Server Platforms
---

### Post by happyhacker on 2009-10-19
I have Webmin (older version) and Ubunutu 9 and am considering upgrading all packages. Should I do Ubuntu first followed by Webmin?

---

### Post by aprigiosimoes on 2009-11-25
In Ubuntu Server

#sed -i "s/jaunty/karmic/g" /etc/apt/sources.list
#apt-get update
#apt-get dist-upgrade

In Ubuntu Desktop
#update-manager -d

;)

---

