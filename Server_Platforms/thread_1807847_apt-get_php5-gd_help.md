---
title: "apt-get php5-gd help"
date: 2011-07-19
forum: Server Platforms
---

### Post by rherman5 on 2011-07-19
I am trying to install php5-gd using apt-get but I keep getting the following errors:

The following packages have unmet dependencies:
 php5-gd : Depends: libgd2-xpm (>= 2.0.36~rc1~dfsg) but 2.0.35.dfsg-3ubuntu2.1 is to be installed
           Depends: php5-common (= 5.3.2-1ubuntu4.9) but 5.3.5-1ubuntu7 is to be installed
E: Broken packages

What can I do?

---

### Post by schnelle02 on 2011-07-19
Maybe you should try 

apt-get install libgd2-xpm php5-common

Not sure if that will work since I am also a newb, but I did just install the gd library while getting my Drupal server up and going.

---

