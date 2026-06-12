---
title: "Install php5"
date: 2012-07-09
forum: Server Platforms
---

### Post by pdcc on 2012-07-09
Hello,

I'm trying to install php5 in ubuntu 11.10 but I can't because i received errors.

If I try this:

apt-get install php5

i get this:

pkg: warning: files list file for package `libtext-wrapi18n-perl' missing, assuming package has no files currently installed.
(Reading database ... 2289 files and directories currently installed.)
Unpacking php5 (from .../php5_5.3.6-13ubuntu3.8_all.deb) ...
Setting up libapache2-mod-php5 (5.3.6-13ubuntu3. ...
dpkg: error processing libapache2-mod-php5 (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up php5-cli (5.3.6-13ubuntu3. ...
dpkg: error processing php5-cli (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up tomcat6 (6.0.32-5ubuntu1.2) ...
dpkg: error processing tomcat6 (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of php5:
 php5 depends on libapache2-mod-php5 (>= 5.3.6-13ubuntu3. | libapache2-mod-php5filter (>= 5.3.6-13ubuntu3. | php5-cgi (>= 5.3.6-13ubuntu3. | php5-fpm (>= 5.3.6-13ubuntu3.; however:
  Package libapache2-mod-php5 is not configured yet.
  Package libapache2-mod-php5filter is not installed.
  Package php5-cgi is not installed.
  Package php5-fpm is not installed.
dpkg: error processing php5 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libapache2-mod-php5
 php5-cli
 tomcat6
 php5
E: Sub-process /usr/bin/dpkg returned an error code (1)



if I try this:

apt-get install -f


i get this:



(Reading database ... 2289 files and directories currently installed.)
Unpacking php5 (from .../php5_5.3.6-13ubuntu3.8_all.deb) ...
Setting up libapache2-mod-php5 (5.3.6-13ubuntu3. ...
dpkg: error processing libapache2-mod-php5 (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up php5-cli (5.3.6-13ubuntu3. ...
dpkg: error processing php5-cli (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up tomcat6 (6.0.32-5ubuntu1.2) ...
dpkg: error processing tomcat6 (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of php5:
 php5 depends on libapache2-mod-php5 (>= 5.3.6-13ubuntu3. | libapache2-mod-php5filter (>= 5.3.6-13ubuntu3. | php5-cgi (>= 5.3.6-13ubuntu3. | php5-fpm (>= 5.3.6-13ubuntu3.; however:
  Package libapache2-mod-php5 is not configured yet.
  Package libapache2-mod-php5filter is not installed.
  Package php5-cgi is not installed.
  Package php5-fpm is not installed.
dpkg: error processing php5 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libapache2-mod-php5
 php5-cli
 tomcat6
 php5
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@vm107:/etc# clear
root@vm107:/etc# apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up libapache2-mod-php5 (5.3.6-13ubuntu3. ...
dpkg: error processing libapache2-mod-php5 (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of php5:
 php5 depends on libapache2-mod-php5 (>= 5.3.6-13ubuntu3. | libapache2-mod-php5filter (>= 5.3.6-13ubuntu3. | php5-cgi (>= 5.3.6-13ubuntu3. | php5-fpm (>= 5.3.6-13ubuntu3.; however:
  Package libapache2-mod-php5 is not configured yet.
  Package libapache2-mod-php5filter is not installed.
  Package php5-cgi is not installed.
  Package php5-fpm is not installed.
dpkg: error processing php5 (--configure):
 dependency problems - leaving unconfigured
Setting up php5-cli (5.3.6-13ubuntu3.8) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: error processing php5-cli (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up tomcat6 (6.0.32-5ubuntu1.2) ...
dpkg: error processing tomcat6 (--configure):
 subprocess installed post-installation script returned error exit status 10
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libapache2-mod-php5
 php5
 php5-cli
 tomcat6
E: Sub-process /usr/bin/dpkg returned an error code (1)



please somebody help me!


thanks

---

### Post by SlugSlug on 2012-07-09
```
sudo aptitude reinstall   libapache2-mod-php5
```
```
sudo aptitude install php5
```

---

### Post by lisati on 2012-07-09
> **SlugSlug said:**
> ```
sudo aptitude reinstall   libapache2-mod-php5
```
```
sudo aptitude install php5
```

+1

Also see [https://help.ubuntu.com/community/ApacheMySQLPHP#Installing_PHP_5](https://help.ubuntu.com/community/ApacheMySQLPHP#Installing_PHP_5)

---

### Post by pdcc on 2012-07-09
give me this error:

Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 3 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up libapache2-mod-php5 (5.3.6-13ubuntu3.8) ...
dpkg: error processing libapache2-mod-php5 (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of php5:
 php5 depends on libapache2-mod-php5 (>= 5.3.6-13ubuntu3.8) | libapache2-mod-php5filter (>= 5.3.6-13ubuntu3.8) | php5-cgi (>= 5.3.6-13ubuntu3.8) | php5-fpm (>= 5.3.6-13ubuntu3.8); however:
  Package libapache2-mod-php5 is not configured yet.
  Package libapache2-mod-php5filter is not installed.
  Package php5-cgi is not installed.
  Package php5-fpm is not installed.
dpkg: error processing php5 (--configure):
 dependency problems - leaving unconfigured
Setting up php5-cli (5.3.6-13ubuntu3.8) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: error processing php5-cli (--configure):
 subprocess installed post-installation script returned error exit status 10
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libapache2-mod-php5
 php5
 php5-cli
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by SlugSlug on 2012-07-09
Are you using aptitude?
```

sudo aptitude install libapache2-mod-php5 libapache2-mod-php5filter php5-cgi php5-fpm php5
```

---

### Post by SlugSlug on 2012-07-09
run 

```
sudo aptitude update
```

first

---

### Post by lisati on 2012-07-09
As a side note: some recent versions of Ubuntu don't have aptitude installed by default.... :(

---

### Post by pdcc on 2012-07-09
i'm using apt-get. its the same thing, or not?

The ubuntu don't recognized appitude

---

### Post by SlugSlug on 2012-07-09
```
sudo apt-get install aptitude
```

aptitude is better at resolving errors :)

---

### Post by pdcc on 2012-07-09
ok.
With appitude:


root@vm107:/var/lib/dpkg# aptitude install libapache2-mod-php5 libapache2-mod-php5filter php5-cgi php5-fpm php5
Uncaught exception: Not enough resources to create thread

---

### Post by SlugSlug on 2012-07-09
> **pdcc said:**
> ok.
With appitude:


root@vm107:/var/lib/dpkg# aptitude install libapache2-mod-php5 libapache2-mod-php5filter php5-cgi php5-fpm php5
Uncaught exception: Not enough resources to create thread

noticed your hostname is VM... is it a VPS or your own VM?  try giving it some more Memory..

---

### Post by pdcc on 2012-07-09
it's a VPS.

After a update i try again and get this:


dpkg: dependency problems prevent configuration of php5:
 php5 depends on libapache2-mod-php5 (>= 5.3.6-13ubuntu3. | libapache2-mod-php5filter (>= 5.3.6-13ubuntu3. | php5-cgi (>= 5.3.6-13ubuntu3. | php5-fpm (>= 5.3.6-13ubuntu3.; however:
  Package libapache2-mod-php5 is not installed.
  Package libapache2-mod-php5filter is not configured yet.
  Package php5-cgi is not configured yet.
  Package php5-fpm is not configured yet.
dpkg: error processing php5 (--configure):
 dependency problems - leaving unconfigured
Setting up php5-cli (5.3.6-13ubuntu3.8) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: error processing php5-cli (--configure):
 subprocess installed post-installation script returned error exit status 10
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libapache2-mod-php5filter
 php5-cgi
 php5-fpm
 php5
 php5-cli
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up php5-cgi (5.3.6-13ubuntu3. ...
dpkg: error processing php5-cgi (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up php5-fpm (5.3.6-13ubuntu3. ...
update-rc.d: warning: php5-fpm stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (none)
dpkg: error processing php5-fpm (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up php5-cli (5.3.6-13ubuntu3. ...
dpkg: error processing php5-cli (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up libapache2-mod-php5filter (5.3.6-13ubuntu3. ...
dpkg: error processing libapache2-mod-php5filter (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of php5:
 php5 depends on libapache2-mod-php5 (>= 5.3.6-13ubuntu3.8) | libapache2-mod-php5filter (>= 5.3.6-13ubuntu3.8) | php5-cgi (>= 5.3.6-13ubuntu3.8) | php5-fpm (>= 5.3.6-13ubuntu3.8); however:
  Package libapache2-mod-php5 is not installed.
  Package libapache2-mod-php5filter is not configured yet.
  Package php5-cgi is not configured yet.
  Package php5-fpm is not configured yet.
dpkg: error processing php5 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 php5-cgi
 php5-fpm
 php5-cli
 libapache2-mod-php5filter
 php5

---

### Post by SlugSlug on 2012-07-09
From what I can gather on the net, you need more memory to be able to run aptitude.

you could try start again if you've not configured anything?

```
sudo apt-get purge php5
```


```
sudo apt-get install php5
```

---

### Post by pdcc on 2012-07-09
Don't work.

there are also some days that dpkg returns these errors:


dpkg: warning: files list file for package `libpopt0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ncurses-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libnetcdf-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libossp-uuid16' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `console-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-minimal' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgssapi-krb5-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `g++-4.6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `procps' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjpeg62' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `fontconfig' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcurl3-gnutls' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lsb-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtasn1-3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgd2-xpm' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apache2-doc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libuuid1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lzma' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxinerama1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `isc-dhcp-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnutlsxx26' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgcrypt11' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdbm3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcairo2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libboost-serialization1.42-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `man-db' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libffi6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `module-init-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libflac8' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gettext-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libperl5.12' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdbus-1-3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openssl-blacklist' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libssl1.0.0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gpgv' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `login' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `telnet' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `console-tools-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `makedev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `initramfs-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `x11proto-input-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `postgresql-contrib' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcb-shm0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `finger' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `samba' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsysfs2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `debianutils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfreetype6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sudo' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `coreutils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgl1-mesa-dri' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libhdf5-serial-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxdmcp6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpq5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `shared-mime-info' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mktemp' missing, assuming package has no files currently installed.
(Reading database ... 35%
dpkg: warning: files list file for package `dash' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libltdl-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `debconf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgmpxx4ldbl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `java-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtext-wrapi18n-perl' missing, assuming package has no files currently installed.

---

### Post by osoriojr on 2012-07-17
I am with the same problem. I purged the php5 and now, when I trying to install I have the same error. 

I reverted my last snapshot and tried to upgrade php5. Same error.


root@nonono:~/# apt-get upgrade php5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-headers-server linux-image-server linux-server
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up libapache2-mod-php5 (5.3.2-1ubuntu4.17) ...
dpkg: error processing libapache2-mod-php5 (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of php5:
 php5 depends on libapache2-mod-php5 (>= 5.3.2-1ubuntu4.17) | libapache2-mod-php5filter (>= 5.3.2-1ubuntu4.17) | php5-cgi (>= 5.3.2-1ubuntu4.17); however:
  Package libapache2-mod-php5 is not configured yet.
  Package libapache2-mod-php5filter is not installed.
  Package php5-cgi is not installed.
dpkg: error processing php5 (--configure):
 dependency problems - leaving unconfigured
Setting up php5-cli (5.3.2-1ubuntu4.17) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: error processing php5-cli (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of php5-curl:
 php5-curl depends on phpapi-20090626; however:
  Package phpapi-20090626 is not installed.
  Package libapache2-mod-php5 which provides phpapi-20090626 is not configured yet.
  Package php5-cli which provides phpapi-20090626 is not configured yet.
dpkg: error processing php5-curl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php5-gd:
 php5-gd depends on phpapi-20090626; however:
  Package phpapi-20090626 is not installed.
  Package libapache2-mod-php5 which provides phpapi-20090626 is not configured yet.
  Package php5-cli which provides phpapi-20090626 is not configured yet.
dpkg: error processing php5-gd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php5-mysql:
 php5-mysql depends No apport report written because MaxReports is reached already
                                                                                  No apport report written because MaxReports is reached already
                                                                                                                                                No apport report written because MaxReports is reached already
                             on phpapi-20090626; however:
  Package phpapi-20090626 is not installed.
  Package libapache2-mod-php5 which provides phpapi-20090626 is not configured yet.
  Package php5-cli which provides phpapi-20090626 is not configured yet.
dpkg: error processing php5-mysql (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libapache2-mod-php5
 php5
 php5-cli
 php5-curl
 php5-gd
 php5-mysql
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

