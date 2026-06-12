---
title: "Trying to install libmd5-perl on Ubuntu server 10.04!"
date: 2010-04-20
forum: Server Platforms
---

### Post by waloshin on 2010-04-20
Trying to install libmd5-perl on Ubuntu server 10.04 beta 2!

It says there is no candiate version found for libmd5-perl

---

### Post by waloshin on 2010-04-20
Solved:

wget [http://ftp.debian.org/pool/main/libm/libmd5-perl/libmd5-perl_2.03-2_all.deb](http://ftp.debian.org/pool/main/libm/libmd5-perl/libmd5-perl_2.03-2_all.deb)

sudo dpkg -i libmd5-perl_2.03-2_all.deb

---

### Post by cdenley on 2010-04-20
[https://bugs.launchpad.net/ubuntu/+bug/542798](https://bugs.launchpad.net/ubuntu/+bug/542798)

---

### Post by mjhasbach on 2010-05-20
I know the last post was 4 weeks ago, but I thought I would provide a link to the download locations for libmd5-perl:

[http://packages.debian.org/etch/all/libmd5-perl/download](http://packages.debian.org/etch/all/libmd5-perl/download)

I ran into the same problem when trying to install Webmin, it was pretty frustrating since I am very new at this.

Revised code that worked for me:
```

wget http://ftp.us.debian.org/debian/pool/main/libm/libmd5-perl/libmd5-perl_2.03-1_all.deb
sudo dpkg -i libmd5-perl_2.03-1_all.deb

```

---

### Post by jbbarnes on 2010-06-12
Thanks a million. That worked perfectly to get webmin installed!

---

### Post by alsrmurad on 2010-09-02
to install the webmin on 10.04 follow this little tutorial

sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl
wget [http://mirrors.kernel.org/ubuntu/pool/universe/libm/libmd5-perl/libmd5-perl_2.03-1_all.deb](http://mirrors.kernel.org/ubuntu/pool/universe/libm/libmd5-perl/libmd5-perl_2.03-1_all.deb)
sudo dpkg -i libmd5-perl_2.03-1_all.deb
 sudo wget [http://sourceforge.net/projects/webadmin/files/webmin/1.520/webmin_1.520_all.deb/download](http://sourceforge.net/projects/webadmin/files/webmin/1.520/webmin_1.520_all.deb/download)
sudo dpkg -i webmin_1.520_all.deb
If your server complains that there is some library things does not find. Just run the following command

sudo apt-get install -f

---

### Post by atomicmoose on 2010-10-21
> **alsrmurad said:**
> to install the webmin on 10.04 follow this little tutorial

sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl
wget [http://mirrors.kernel.org/ubuntu/pool/universe/libm/libmd5-perl/libmd5-perl_2.03-1_all.deb](http://mirrors.kernel.org/ubuntu/pool/universe/libm/libmd5-perl/libmd5-perl_2.03-1_all.deb)
sudo dpkg -i libmd5-perl_2.03-1_all.deb
 sudo wget [http://sourceforge.net/projects/webadmin/files/webmin/1.520/webmin_1.520_all.deb/download](http://sourceforge.net/projects/webadmin/files/webmin/1.520/webmin_1.520_all.deb/download)
sudo dpkg -i webmin_1.520_all.deb
If your server complains that there is some library things does not find. Just run the following command

sudo apt-get install -fThis worked well for me, thanks a bunch!

---

### Post by Deathstrike on 2012-02-09
> **mjhasbach said:**
> I know the last post was 4 weeks ago, but I thought I would provide a link to the download locations for libmd5-perl:

[http://packages.debian.org/etch/all/libmd5-perl/download](http://packages.debian.org/etch/all/libmd5-perl/download)

I ran into the same problem when trying to install Webmin, it was pretty frustrating since I am very new at this.

Revised code that worked for me:
```

wget http://ftp.us.debian.org/debian/pool/main/libm/libmd5-perl/libmd5-perl_2.03-1_all.deb
sudo dpkg -i libmd5-perl_2.03-1_all.deb

```

For some reason, my hatchling server had the same problem, it was able to install everything needed for webmin except libmd5-perl. This worked, and the ball still rolls :D Tyyy

---

### Post by chip_n_rut on 2012-08-07
I had to go to the archive to get it:
wget [http://archive.ubuntu.com/ubuntu/pool/universe/libm/libmd5-perl/libmd5-perl_2.03-1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libm/libmd5-perl/libmd5-perl_2.03-1_all.deb)

---

