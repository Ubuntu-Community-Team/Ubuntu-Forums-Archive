---
title: "clamav-0.98.3"
date: 2014-05-29
forum: Security
---

### Post by dapps2 on 2014-05-29
I have a lot of friends and family who have not apparently seen the light and still using Windows. It was with this thought in mind that i installed clamav-0.98.1 but everytime i updated the program using freshclam i was informed that the version i was using is out of date and to either upgrade or install clamav-0.98.3.

I immediately uninstalled clamav-0.98.1 and then downloaded clamav-0.98.3.tar.gz
Then i opened a terminal and typed: tar -zxvf clamav-0.98.3.tar.gz and a new folder appeared called clamav-0.98.3. But i have failed to install it?

I tried to install clamav-0.98.3 by going along to the Downloads directory and then typing: sudo apt-get install clamav-0.98.3 but still no luck.

Could someone help me to install clamav-0.98.3 please

---

### Post by bashiergui on 2014-05-30
When installing a tar.gz file (known as tar balls) you must understand that it contains source code and you must build it and then install it manually. The software center uses the apt-get package manager that does it automatically for you, but it will not handle tar balls for you. For a general explanation on how installing tar balls works, see this: [http://www.cyberciti.biz/faq/install-tarballs/](http://www.cyberciti.biz/faq/install-tarballs/)

See this guide for directions to specifically install clamav from source.
[http://wiki.opensource-excellence.com/index.php?title=How_to_install_ClamAV](http://wiki.opensource-excellence.com/index.php?title=How_to_install_ClamAV)

If that is intimidating then you will be fine using the one in the Ubuntu software center, which uses the apt-get package manager and does all that work for you. Yes it's a version or two behind but that doesn't make much difference.

---

### Post by bashiergui on 2014-05-30
Forgot to mention...

if you install it from source (i.e. Using the tar ball) then you will have to manually check for updates and download new tarballs when they are released. It will not automatically update.

If you use the version in the software center then updates will be pushed to you routinely.

---

### Post by TheFu on 2014-06-04
> **bashiergui said:**
> Forgot to mention...

if you install it from source (i.e. Using the tar ball) then you will have to manually check for updates and download new tarballs when they are released. It will not automatically update.

If you use the version in the software center then updates will be pushed to you routinely.

This is a big reason to avoid installing any software from non-repo/PPA sources. I won't do it. Too much hassle to maintain, period.
OTOH, my clamAV is also out of date.  Isn't there a PPA that is current-enough to make the auto-clam download process happy?

---

