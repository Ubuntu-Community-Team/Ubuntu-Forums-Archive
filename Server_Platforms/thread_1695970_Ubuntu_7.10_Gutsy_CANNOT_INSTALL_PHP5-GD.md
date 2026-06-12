---
title: "Ubuntu 7.10 Gutsy CANNOT INSTALL PHP5-GD"
date: 2011-02-26
forum: Server Platforms
---

### Post by wjrhee77 on 2011-02-26
Hello All,

Hopefully this is matter of getting right repo list.

apt-get install php5-gd

...
The following NEW packages will be installed:
  libgd2-xpm libt1-5 php5-gd
...
WARNING: The following packages cannot be authenticated!
  libgd2-xpm libt1-5 php5-gd
...
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libgd2-xpm 2.0.34-1ubuntu1.1
  404 Not Found [IP: 91.189.92.169 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libt1-5 5.1.0-3
  404 Not Found [IP: 91.189.92.169 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main php5-gd 5.2.3-1ubuntu6.3
  404 Not Found [IP: 91.189.92.169 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libgd2-xpm 2.0.34-1ubuntu1.1
  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libg/libgd2/libgd2-xpm_2.0.34-1ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libg/libgd2/libgd2-xpm_2.0.34-1ubuntu1.1_i386.deb)  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/t1lib/libt1-5_5.1.0-3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/t1lib/libt1-5_5.1.0-3_i386.deb)  404 Not Found [IP: 91.189.92.169 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/php5/php5-gd_5.2.3-1ubuntu6.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/php5/php5-gd_5.2.3-1ubuntu6.3_i386.deb)  404 Not Found [IP: 91.189.92.169 80]

So basically it seems like it's not in the repository.
I have enabled all the /etc/apt/sources.list

I'm not too familiar with where to find the correct repo that has php5-gd package that I need.  Searching the internet seems like "apt-get install php5-gd" worked for everyone.  Please help!!!

---

### Post by wjrhee77 on 2011-02-26
So I got php5-gd installed via repo list below :

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy main restricted

Now, I think I need to enable it in php...
hmmm....

---

### Post by wjrhee77 on 2011-02-26
After getting php5-gd installed, i ran 

php -m

This gave me 

PHP Warning: PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/gd.so' - /usr/lib/php5/20060613+lfs/gd.so: undefined symbol: gdImageCreateFromJpeg in Unknown on line 0


As it turns out, /usr/lib/php5/20060613+lfs/gd.so had a dependency on /usr/local/lib/libgd.so.2.0.0 on my machine. But when I check the symbol definitions in /usr/local/lib/libgd.so.2.0.0, gdImageCreateFromJpeg indeed was missing.

nm -D /usr/local/lib/libgd.so.2.0.0 | grep gdImageCreateFromJpeg


On the other hand, I have another /usr/lib/libgd.so.2.0.0, which does have the symbol defined. So I did:

cd /usr/local/lib
sudo cp libgd.so.2.0.0 libgd.so.2.0.0.broken
sudo ln -f /usr/lib/libgd.so.2.0.0 libgd.so.2.0.0

Now run 

php -m

The undefined symbol error disappeared and "gd" appears.

In short, the problem was not caused by missing packages; rather, the broken dynamic library was being linked by php5-gd.

Hope this helps some one.


Please see [http://ubuntuforums.org/showthread.php?t=252842&page=3](http://ubuntuforums.org/showthread.php?t=252842&page=3)

---

