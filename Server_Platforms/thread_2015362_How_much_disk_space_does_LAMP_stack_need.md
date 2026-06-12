---
title: "How much disk space does LAMP stack need?"
date: 2012-07-03
forum: Server Platforms
---

### Post by mastablasta on 2012-07-03
I have Xubuntu installed in Vbox on 8GB hard disk. I removed a few programes i don't need there (e.g. gimp, mail...). 
 
I now find a PHP tool i would like to try to see how well it works and though i haven't found the exact specs it needs but it does need a webserver. and from the part of documentation i read (didn't have time yet to read it all) it seems it also needs a MySQL. So the easiest route seems to be to install LAMP (or is it AMP).
 
I checked the disk space after clearing old kernels and it says 4 GB disk free. the vbox mashcine has 512MB ram (hopefully that is enough). disk will probably get clogged up again (with new kernels) so it would likely leave about 2GB to work with. Is that enough? How much disk space (approximatelly) does LAMP stack need? should i somehow increase the *virtual disk* space?

---

### Post by Cheesemill on 2012-07-03
I don't have a VM to test with at the moment but apt-get will tell you before you hit Y.
```
root@quantal:~# apt-get install lamp-server^
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libnet-daemon-perl' for task 'lamp-server'
Note, selecting 'libwrap0' for task 'lamp-server'
Note, selecting 'mysql-server' for task 'lamp-server'
Note, selecting 'perl' for task 'lamp-server'
Note, selecting 'libcap2' for task 'lamp-server'
Note, selecting 'libdbi-perl' for task 'lamp-server'
Note, selecting 'libapr1' for task 'lamp-server'
Note, selecting 'libhtml-template-perl' for task 'lamp-server'
Note, selecting 'perl-modules' for task 'lamp-server'
Note, selecting 'libapache2-mod-php5' for task 'lamp-server'
Note, selecting 'mysql-server-core-5.5' for task 'lamp-server'
Note, selecting 'libaprutil1-ldap' for task 'lamp-server'
Note, selecting 'apache2-mpm-prefork' for task 'lamp-server'
Note, selecting 'libmysqlclient18' for task 'lamp-server'
Note, selecting 'apache2-utils' for task 'lamp-server'
Note, selecting 'tcpd' for task 'lamp-server'
Note, selecting 'apache2' for task 'lamp-server'
Note, selecting 'apache2.2-common' for task 'lamp-server'
Note, selecting 'libclass-isa-perl' for task 'lamp-server'
Note, selecting 'libaprutil1-dbd-sqlite3' for task 'lamp-server'
Note, selecting 'mysql-client-core-5.5' for task 'lamp-server'
Note, selecting 'apache2.2-bin' for task 'lamp-server'
Note, selecting 'ssl-cert' for task 'lamp-server'
Note, selecting 'libdbd-mysql-perl' for task 'lamp-server'
Note, selecting 'libswitch-perl' for task 'lamp-server'
Note, selecting 'libplrpc-perl' for task 'lamp-server'
Note, selecting 'php5-mysql' for task 'lamp-server'
Note, selecting 'php5-cli' for task 'lamp-server'
Note, selecting 'libaprutil1' for task 'lamp-server'
Note, selecting 'mysql-common' for task 'lamp-server'
Note, selecting 'php5-common' for task 'lamp-server'
Note, selecting 'mysql-server-5.5' for task 'lamp-server'
Note, selecting 'mysql-client-5.5' for task 'lamp-server'
libcap2 is already the newest version.
libclass-isa-perl is already the newest version.
libswitch-perl is already the newest version.
libwrap0 is already the newest version.
mysql-common is already the newest version.
perl is already the newest version.
perl-modules is already the newest version.
php5-cli is already the newest version.
php5-common is already the newest version.
php5-common set to manually installed.
ssl-cert is already the newest version.
tcpd is already the newest version.
Suggested packages:
  apache2-doc apache2-suexec apache2-suexec-custom php-pear libipc-sharedcache-perl libterm-readkey-perl tinyca mailx
The following NEW packages will be installed:
  apache2 apache2-mpm-prefork apache2-utils apache2.2-bin apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libaprutil1-dbd-sqlite3 libaprutil1-ldap
  libdbd-mysql-perl libdbi-perl libhtml-template-perl libmysqlclient18 libnet-daemon-perl libplrpc-perl mysql-client-5.5 mysql-client-core-5.5 mysql-server
  mysql-server-5.5 mysql-server-core-5.5 php5-mysql
0 upgraded, 22 newly installed, 0 to remove and 19 not upgraded.
Need to get 33.6 MB of archives.
After this operation, 117 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
```
So on my current setup it will take 117MB. I already have some of the packages installed though.

---

### Post by spynappels on 2012-07-03
I think you should be ok, depending on the size of the data you will have in the /var/www folder and the size of the MySQL database. I've run LAMP machines from 8GB SD cards with no problems, only with small sites and small databases though.

---

### Post by trundlenut on 2012-07-03
I have a straightforward LAMP installation of 12.04 server (i.e. no GUI) and it takes up about 3.5Gb, this is with one fairly small mysql database and a simple php based website.

---

### Post by SeijiSensei on 2012-07-03
> **trundlenut said:**
> I have a straightforward LAMP installation of 12.04 server (i.e. no GUI) and it takes up about 3.5Gb, this is with one fairly small mysql database and a simple php based website.

That's the size of the entire OS image, right?  The actual disk space consumed by the packages associated with LAMP are much smaller than that.  Even if Cheesemill's 117 MB figure is an underestimate, the total size is probably still well under 200 MB.

Of course the size of the database itself will determine the total size of the image.  In most web applications these databases are also pretty miniscule.  Web applications in an office setting could have much larger databases, but they are likely to be hosted on another server and accessed over the network.

---

### Post by mastablasta on 2012-07-03
the tool i want to try is less than 20MB + maybe some data. alltogether no more than 100MB-150MB. so i gues it will be fine. thanks.

---

### Post by trundlenut on 2012-07-04
> **SeijiSensei said:**
> That's the size of the entire OS image, right?  The actual disk space consumed by the packages associated with LAMP are much smaller than that.  Even if Cheesemill's 117 MB figure is an underestimate, the total size is probably still well under 200 MB.


That is the total amount of disk space being used on that VM.  It has been running for about a monthso it includes whatever has accumulated in terms of updates, temp and log files etc.

---

