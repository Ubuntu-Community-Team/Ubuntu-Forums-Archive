---
title: "Insert OTP to server"
date: 2011-01-07
forum: Server Platforms
---

### Post by pras on 2011-01-07
Hi all,

I have a server Ubuntu 10.04.1 and I have a medical site in this server (openemr).

Due to medical data in that site/server I want to implement a OTP (one time password) for accessing the sites folder.

Can you please guide me to do that..?

And if there is any Android or any other smartphone OTP generator?

Thank you in advance

Regards
Christos

---

### Post by RayVad on 2011-01-11
Hi Pras,

Am looking for the same implementation and did find this information:

The open OTP solution:
[http://www.linotp.org/](http://www.linotp.org/)
[http://www.linotp.org/index.php/howtos/5/22-howto-install-linotp2-with-ubuntu-1010-to-secure-your-desktop-with-otp](http://www.linotp.org/index.php/howtos/5/22-howto-install-linotp2-with-ubuntu-1010-to-secure-your-desktop-with-otp)

And a token generator m-otp to be used with open OTP:
[http://motp.sourceforge.net/](http://motp.sourceforge.net/)
(I have a Nokia 6303i Classic running with this .jad and .jar software)

Think that will do the trick.
Regards,
Raymond

---

### Post by RayVad on 2011-01-13
This is really genius!! Generating a random code on my Nokia 6303i Classic and then login to my system.

Did install and configured it as instructed on those sites on a Virtualbox with Ubuntu 10.04 i386. be aware that for 10.04 you need libcurl3 (see dependencies here below).

The dependencies you need to install first are (102Mb):
sudo apt-get install apache2 apache2-mpm-worker apache2-utils apache2.2-bin apache2.2-common javascript-common libapache2-mod-wsgi libapr1 libaprutil1 libaprutil1-dbd-sqlite3 libaprutil1-ldap libcurl3 libjpeg62 libjs-prototype libjs-scriptaculous liblcms1 libmysqlclient16 libpaper-utils libpaper1 libxslt1.1 mysql-server mysql-common pwgen python-beaker python-beautifulsoup python-cheetah python-crypto python-decorator python-docutils python-formencode python-imaging python-ldap python-lxml python-m2crypto python-mako python-mysqldb python-nose python-openid python-paste python-pastedeploy python-pastescript python-pygments python-pylons python-roman python-repoze.who
 python-routes python-scgi python-simplejson python-sqlalchemy python-tempita python-weberror python-webhelpers python-webob python-webtest ssl-cert wwwconfig-common


It didn't work to add the packages to the repo. 

But, downloading these files:
wget [http://www.linotp.org/download/libpam-linotp_2.2_i386.deb](http://www.linotp.org/download/libpam-linotp_2.2_i386.deb)
wget [http://www.linotp.org/download/linotp_2.2_all.deb](http://www.linotp.org/download/linotp_2.2_all.deb)
wget [http://www.linotp.org/download/linotpadminclientce_2.2_all.deb](http://www.linotp.org/download/linotpadminclientce_2.2_all.deb)
wget [http://www.linotp.org/download/linotpuseridresolver_2.2_all.deb](http://www.linotp.org/download/linotpuseridresolver_2.2_all.deb)

And then install them with:
sudo dpkg -i linotp_2.2_all.deb linotpuseridresolver_2.2_all.deb libpam-linotp_2.2_i386.deb linotpadminclientce_2.2_all.deb
(linotp failed to install. But i reinstalled linotp_2.2_all.deb again without regenerating the keys and creating the database again. It worked and i do not know why it failed. i'll try to find out why this did happen.)

Used the token authentication only for ssh login (one user is able to login from the internet) as i want for myself and is working great :)
All other logins (GDM) doesn't need a token, since they are local actions. But can be defined as well if you like.

Tokens can be generated for users by use of webpage on the system.

I'm trying to get it work on a 64bit machine now.
Maybe someone can help me with a 64-bit package for this!?

Ray

---

### Post by RayVad on 2011-10-28
An other solution based on the same MobileOTP is my post at:

[http://ubuntuforums.org/showthread.php?t=1870995&highlight=OTP]("http://ubuntuforums.org/showthread.php?t=1870995&highlight=OTP")

---

