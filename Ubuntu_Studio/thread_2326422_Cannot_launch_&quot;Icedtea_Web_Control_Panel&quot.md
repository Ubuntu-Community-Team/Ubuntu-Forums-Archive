---
title: "Cannot launch &quot;Icedtea Web Control Panel&quot; in Ubuntu Studio 16.04."
date: 2016-05-31
forum: Ubuntu Studio
---

### Post by sethanath2 on 2016-05-31
Hi,

I have just installed "Icedtea Web Control Panel" in Ubuntu Studio 16.04 through "Software".
However, I get the error message "Failed to execute child process /usr/bin/itweb-setting".

Please note that my java version is 1.8.0_91

$ java -showversion
openjdk version "1.8.0_91"
OpenJDK Runtime Environment (build 1.8.0_91-8u91-b14-0ubuntu4~16.04.1-b14)
OpenJDK 64-Bit Server VM (build 25.91-b14, mixed mode)

I hope someone can help.

---

### Post by sethanath2 on 2016-06-02
It solved. I uninstalled it through "Software", and reinstalled using the following command.

sudo apt-get install icedtea-8-plugin

---

