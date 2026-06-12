---
title: "Upgrade Phpmyadmin"
date: 2009-06-30
forum: Server Platforms
---

### Post by wxman on 2009-06-30
Is there an easy way to uphgrade phpmyadmin from the version in the repository (2.11.3deb1ubuntu1.1) to the 3.x version? I'd like to do this without moving it from where it is now if possible.

---

### Post by dtoronto on 2009-06-30
I believe you can add the personal repository from launchpad.  Here is the link 

[https://launchpad.net/~nijel/+archive/ppa](https://launchpad.net/~nijel/+archive/ppa)

I'm not sure if adding it to the repository will let you upgrade your current installation of phpmyadmin though

---

### Post by wxman on 2009-06-30
Thanks. I gave it a try, but it didn't upgrade phpmyadmin. Nice try though.

---

### Post by wxman on 2009-07-03
If anyone is interested, I actually did it. I used the K.I.S. method. I renamed the /usr/share/phpmyadmin directory to keep a backup. I downloaded the latest copy of phpmyadmin as a ZIP file, and uploaded that to my /usr/share directory as root. Then I copied the cfg files from the backup phpmyadmin dir into the new one, and it seems to work perfectly. I don't know if that's the "correct" way to do it, but it's at least working using version 3.2.0.1 now.

---

### Post by ajmc on 2011-12-26
I uninstalled the previous version of phpmyadmin.

I added the following on the source list:

deb [http://ppa.launchpad.net/nijel/ppa/ubuntu](http://ppa.launchpad.net/nijel/ppa/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/nijel/ppa/ubuntu](http://ppa.launchpad.net/nijel/ppa/ubuntu) lucid main

and installed phpmyadmin using software center.

---

