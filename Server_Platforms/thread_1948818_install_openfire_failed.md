---
title: "install openfire failed"
date: 2012-03-28
forum: Server Platforms
---

### Post by netizen99 on 2012-03-28
I try to install openfire on Ubuntu 11.10 server (64.bit)

1 install the server with OpenSSH server and LAMP server option checked.

Install Java with command:
sudo apt-get install openjdk-6-jre
sudo apt-get install icedtea6-plugin

java -version shows

java version "1.6.0_23"
OpenJDK Runtime Environment (IcedTea6 1.11pre) (6b23~pre11-0ubuntu1.11.10.2)
OpenJDK 64-Bit Server VM (build 20.0-b11, mixed mode)

# download openfire

wget [http://www.igniterealtime.org/downloadServlet?filename=openfire/openfire_3.7.1_all.deb](http://www.igniterealtime.org/downloadServlet?filename=openfire/openfire_3.7.1_all.deb)

sudo dpkg -i openfire_3.7.1_all.deb
dpkg: regarding openfire_3.7.1_all.deb containing openfire, pre-dependency problem:
 openfire pre-depends on sun-java5-jre | sun-java6-jre | default-jre-headless
  sun-java5-jre is not installed.
  sun-java6-jre is not installed.
  default-jre-headless is not installed.
dpkg: error processing openfire_3.7.1_all.deb (--install):
 pre-dependency problem - not installing openfire
Errors were encountered while processing:
 openfire_3.7.1_all.deb

What's missing?

Thanks for your help!

---

