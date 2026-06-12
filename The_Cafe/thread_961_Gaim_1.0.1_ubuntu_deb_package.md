---
title: "Gaim 1.0.1 ubuntu deb package"
date: 2004-10-17
forum: The Cafe
---

### Post by ubuntu-geek on 2004-10-17
Was bored and wanted the new gaim. Here is the package if anyone wants it.

Was built on a P4, Ubuntu 4.10 RC..

[http://ubuntuforums.org/dl/gaim_1.0.1-2_i386.deb](http://ubuntuforums.org/dl/gaim_1.0.1-2_i386.deb)

To install:

sudo dpkg -i gaim_1.0.1-2_i386.deb

---

### Post by Ronny on 2004-10-17
I wonder if Skype could be used in ubuntu?

I like Skype and used it in Fedora... but it comes in RPM's.
Can ubuntu utilize RPM's?

Thanks!!

[http://www.skype.com/products/skype/linux/](http://www.skype.com/products/skype/linux/)

---

### Post by eNiNjA on 2004-10-17
try this:

```
wget http&#58;//www.skype.com/go/getskype-linux-fc2

sudo alien -d skype-0.92.0.2-fc2.i386.rpm

sudo dpkg -i skype_0.92.0.2-1_i386.deb

note&#58; I had to install some qt stuff to get it to work

sudo apt-get install libqt3-mt-dev 
```

seemed to do the trick

---

### Post by eNiNjA on 2004-10-17
oh, here is more information on alien if you are interested:

[http://www.perldoc.com/perl5.6/bin/alien.html](http://www.perldoc.com/perl5.6/bin/alien.html)

---

### Post by Ronny on 2004-10-17
Wow... cool... Thanks!!   :D

---

### Post by renato on 2004-10-22
I installed Skype from the tarball, it worked perfectly at first attempt:-)

Dynamic (if you have QT):
[http://www.skype.com/go/getskype-linux-dynamic](http://www.skype.com/go/getskype-linux-dynamic)

Static (if you dont have QT)
[http://www.skype.com/go/getskype-linux-static](http://www.skype.com/go/getskype-linux-static)

Just untar the file in a directory.

---

