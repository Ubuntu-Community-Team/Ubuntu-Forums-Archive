---
title: "FedoraDS and Ubuntu 8.1"
date: 2008-11-28
forum: Server Platforms
---

### Post by CorvisRex on 2008-11-28
Has anyone tried, perferrably successfully to install Fedora DS on Ubuntu 8.1?  Been evaluating Ubuntu server and doing a comparison vs RH based distros, and seem to be hitting a wall on this one point.  I get everything installed right, Java, Fedora ds, everything, abut can't seem to launch the setup scripts.  I get a perl error...

perl: symbol lookup error: /usr/lib/perl5/auto/Mozilla/LDAP/API/API.so: undefined symbol: Perl_Tstack_sp_ptr

I have seen several howto/tutorials, went through two of them,step by step, just to make sure I was not missing something, but still this.  

Just curious,  I guess I can use OpenLDAP, but I started checking out Fedora DS a couple of months ago, and really liked (running on a CentOS server)

---

### Post by madscientist159 on 2009-02-04
> **CorvisRex said:**
> Has anyone tried, perferrably successfully to install Fedora DS on Ubuntu 8.1?  Been evaluating Ubuntu server and doing a comparison vs RH based distros, and seem to be hitting a wall on this one point.  I get everything installed right, Java, Fedora ds, everything, abut can't seem to launch the setup scripts.  I get a perl error...

perl: symbol lookup error: /usr/lib/perl5/auto/Mozilla/LDAP/API/API.so: undefined symbol: Perl_Tstack_sp_ptr

I have seen several howto/tutorials, went through two of them,step by step, just to make sure I was not missing something, but still this.  

Just curious,  I guess I can use OpenLDAP, but I started checking out Fedora DS a couple of months ago, and really liked (running on a CentOS server)

I have updated the instructions located here:
[https://help.ubuntu.com/community/FedoraDirectoryServer#Installation%20of%20Fedora%20Directory%20Server%201.1.x%20under%20Ubuntu%208.10](https://help.ubuntu.com/community/FedoraDirectoryServer#Installation%20of%20Fedora%20Directory%20Server%201.1.x%20under%20Ubuntu%208.10)

They are now based on my repository for Fedora DS that is based on the Debian packaging scripts and uses the latest Fedora DS 1.1.3 ;)

It works on my systems perfectly; report any bugs you may find to [http://bugs.pearsoncomputing.net](http://bugs.pearsoncomputing.net)

Tim

---

### Post by senor_smile on 2009-02-05
I am interested in trying out the Fedora directory services.  Correct me if I'm wrong, but it would provide a perfect replacement for a network of just a couple computers with one server all currently running windows to provide user authentication and file sharing.  

I first installed a brand new 8.10 server in virtualbox, applied updates and verified host networking works with static ip I set up.  

I followed the steps on [https://help.ubuntu.com/community/FedoraDirectoryServer#Installation%20of%20Fedora%20Directory%20Server%201.1.x%20under%20Ubuntu%208.10]("https://help.ubuntu.com/community/FedoraDirectoryServer#Installation%20of%20Fedora%20Directory%20Server%201.1.x%20under%20Ubuntu%208.10")
exactly, and couldn't get very far.  Here is the output of the long apt-get install line: 

```
Fetched 25.0MB in 1min14s (337kB/s)                                            
Extracting templates from packages: 100%
Preconfiguring packages ...
Selecting previously deselected package libnspr4-0d.
(Reading database ... 20573 files and directories currently installed.)
Unpacking libnspr4-0d (from .../libnspr4-0d_4.7.1+1.9-0ubuntu4_i386.deb) ...
Selecting previously deselected package libnss3-1d.
Unpacking libnss3-1d (from .../libnss3-1d_3.12.0.3-0ubuntu5_i386.deb) ...
Selecting previously deselected package libsvrcore0.
Unpacking libsvrcore0 (from .../libsvrcore0_1%3a4.0.4-9_i386.deb) ...
Selecting previously deselected package libmozldap-0d.
Unpacking libmozldap-0d (from .../libmozldap-0d_6.0.6+dfsg-1_i386.deb) ...
Selecting previously deselected package libsnmp-base.
Unpacking libsnmp-base (from .../libsnmp-base_5.4.1~dfsg-7.1ubuntu6.1_all.deb) ...
Selecting previously deselected package libperl5.10.
Unpacking libperl5.10 (from .../libperl5.10_5.10.0-11.1ubuntu2.2_i386.deb) ...
Selecting previously deselected package libsysfs2.
Unpacking libsysfs2 (from .../libsysfs2_2.1.0-4_i386.deb) ...
Selecting previously deselected package libsensors3.
Unpacking libsensors3 (from .../libsensors3_1%3a2.10.7-1_i386.deb) ...
Selecting previously deselected package libsnmp15.
Unpacking libsnmp15 (from .../libsnmp15_5.4.1~dfsg-7.1ubuntu6.1_i386.deb) ...
Selecting previously deselected package libicu38.
Unpacking libicu38 (from .../libicu38_3.8.1-2_i386.deb) ...
Selecting previously deselected package libdirsrv0.
Unpacking libdirsrv0 (from .../libdirsrv0_1.1.3-2_i386.deb) ...
Selecting previously deselected package libmozilla-ldap-perl.
Unpacking libmozilla-ldap-perl (from .../libmozilla-ldap-perl_1.5.2-4_i386.deb) ...
Selecting previously deselected package dirsrv.
Unpacking dirsrv (from .../dirsrv_1.1.3-2_i386.deb) ...
Selecting previously deselected package libadminutil1.
Unpacking libadminutil1 (from .../libadminutil1_1.1.7-1_i386.deb) ...
Selecting previously deselected package libds-admin-serv0.
Unpacking libds-admin-serv0 (from .../libds-admin-serv0_1.1.6-2_i386.deb) ...
Selecting previously deselected package libnss3-tools.
Unpacking libnss3-tools (from .../libnss3-tools_3.12.0.3-0ubuntu5_i386.deb) ...
Selecting previously deselected package libapr1.
Unpacking libapr1 (from .../libapr1_1.2.12-4_i386.deb) ...
Selecting previously deselected package mysql-common.
Unpacking mysql-common (from .../mysql-common_5.0.67-0ubuntu6_all.deb) ...
Selecting previously deselected package libmysqlclient15off.
Unpacking libmysqlclient15off (from .../libmysqlclient15off_5.0.67-0ubuntu6_i386.deb) ...
Selecting previously deselected package libpq5.
Unpacking libpq5 (from .../libpq5_8.3.5-0ubuntu8.10_i386.deb) ...
Selecting previously deselected package libaprutil1.
Unpacking libaprutil1 (from .../libaprutil1_1.2.12+dfsg-7_i386.deb) ...
Selecting previously deselected package apache2-utils.
Unpacking apache2-utils (from .../apache2-utils_2.2.9-7ubuntu3_i386.deb) ...
Selecting previously deselected package apache2.2-common.
Unpacking apache2.2-common (from .../apache2.2-common_2.2.9-7ubuntu3_i386.deb) ...
Selecting previously deselected package apache2-mpm-worker.
Unpacking apache2-mpm-worker (from .../apache2-mpm-worker_2.2.9-7ubuntu3_i386.deb) ...
Selecting previously deselected package libapache2-mod-nss.
Unpacking libapache2-mod-nss (from .../libapache2-mod-nss_1.0.8-3_i386.deb) ...
Selecting previously deselected package dirsrv-admin.
Unpacking dirsrv-admin (from .../dirsrv-admin_1.1.6-2_i386.deb) ...
Selecting previously deselected package openssl-blacklist.
Unpacking openssl-blacklist (from .../openssl-blacklist_0.4.2_all.deb) ...
Selecting previously deselected package fedora-ds-admin-console.
Unpacking fedora-ds-admin-console (from .../fedora-ds-admin-console_1.1.2-1_all.deb) ...
Selecting previously deselected package fedora-ds-console.
Unpacking fedora-ds-console (from .../fedora-ds-console_1.1.2-1_all.deb) ...
Selecting previously deselected package libjss-java.
Unpacking libjss-java (from .../libjss-java_4.2.5-2_i386.deb) ...
Selecting previously deselected package ssl-cert.
Unpacking ssl-cert (from .../ssl-cert_1.0.23_all.deb) ...
Processing triggers for man-db ...
Processing triggers for ufw ...
Setting up libnspr4-0d (4.7.1+1.9-0ubuntu4) ...

Setting up libnss3-1d (3.12.0.3-0ubuntu5) ...

Setting up libsvrcore0 (1:4.0.4-9) ...

Setting up libmozldap-0d (6.0.6+dfsg-1) ...

Setting up libsnmp-base (5.4.1~dfsg-7.1ubuntu6.1) ...
Setting up libperl5.10 (5.10.0-11.1ubuntu2.2) ...

Setting up libsysfs2 (2.1.0-4) ...

Setting up libsensors3 (1:2.10.7-1) ...
udev active, devices will be created in /dev/.static/dev/
rm: cannot remove `i2c-0-': Read-only file system
mknod: `i2c-0-': Read-only file system
makedev i2c-0 c 89 0 root root 0600: failed
rm: cannot remove `i2c-0-': Read-only file system
rm: cannot remove `i2c-1-': Read-only file system
mknod: `i2c-1-': Read-only file system
makedev i2c-1 c 89 1 root root 0600: failed
rm: cannot remove `i2c-1-': Read-only file system
rm: cannot remove `i2c-2-': Read-only file system
mknod: `i2c-2-': Read-only file system
makedev i2c-2 c 89 2 root root 0600: failed
rm: cannot remove `i2c-2-': Read-only file system
rm: cannot remove `i2c-3-': Read-only file system
mknod: `i2c-3-': Read-only file system
makedev i2c-3 c 89 3 root root 0600: failed
rm: cannot remove `i2c-3-': Read-only file system
rm: cannot remove `i2c-4-': Read-only file system
mknod: `i2c-4-': Read-only file system
makedev i2c-4 c 89 4 root root 0600: failed
rm: cannot remove `i2c-4-': Read-only file system
rm: cannot remove `i2c-5-': Read-only file system
mknod: `i2c-5-': Read-only file system
makedev i2c-5 c 89 5 root root 0600: failed
rm: cannot remove `i2c-5-': Read-only file system
rm: cannot remove `i2c-6-': Read-only file system
mknod: `i2c-6-': Read-only file system
makedev i2c-6 c 89 6 root root 0600: failed
rm: cannot remove `i2c-6-': Read-only file system
rm: cannot remove `i2c-7-': Read-only file system
mknod: `i2c-7-': Read-only file system
makedev i2c-7 c 89 7 root root 0600: failed
rm: cannot remove `i2c-7-': Read-only file system

Creating config file /etc/sensors.conf with new version

Setting up libsnmp15 (5.4.1~dfsg-7.1ubuntu6.1) ...

Setting up libicu38 (3.8.1-2) ...

Setting up libdirsrv0 (1.1.3-2) ...
Setting up libmozilla-ldap-perl (1.5.2-4) ...
Setting up dirsrv (1.1.3-2) ...
Adding group `dirsrv' (GID 116) ...
Done.
Adding system user `dirsrv' (UID 106) ...
Adding new user `dirsrv' (UID 106) with group `dirsrv' ...
Not creating home directory `/var/lib/dirsrv'.
chown: cannot access `/var/run/dirsrv/': No such file or directory
chmod: cannot access `/var/run/dirsrv/': No such file or directory
Your new DS instance 'ubuntuds' was successfully created.
Exiting . . .
Log file is '/tmp/setupou8psq.log'

 * Starting FDS instances : ...                                                  * ubuntuds ...                                                                  * already running...                                                    [ OK ] 

Setting up libadminutil1 (1.1.7-1) ...

Setting up libds-admin-serv0 (1.1.6-2) ...

Setting up libnss3-tools (3.12.0.3-0ubuntu5) ...
Setting up libapr1 (1.2.12-4) ...

Setting up mysql-common (5.0.67-0ubuntu6) ...
Setting up libmysqlclient15off (5.0.67-0ubuntu6) ...

Setting up libpq5 (8.3.5-0ubuntu8.10) ...

Setting up libaprutil1 (1.2.12+dfsg-7) ...

Setting up apache2-utils (2.2.9-7ubuntu3) ...
Setting up apache2.2-common (2.2.9-7ubuntu3) ...
Enabling site default.
Enabling module alias.
Enabling module autoindex.
Enabling module dir.
Enabling module env.
Enabling module mime.
Enabling module negotiation.
Enabling module setenvif.
Enabling module status.
Enabling module auth_basic.
Enabling module deflate.
Enabling module authz_default.
Enabling module authz_user.
Enabling module authz_groupfile.
Enabling module authn_file.
Enabling module authz_host.

Setting up apache2-mpm-worker (2.2.9-7ubuntu3) ...
 * Starting web server apache2                                           [ OK ] 

Setting up libapache2-mod-nss (1.0.8-3) ...

Setting up dirsrv-admin (1.1.6-2) ...
Starting dirsrv-admin: 
 * /var/run/dirsrv is not writable for 
invoke-rc.d: initscript dirsrv-admin, action "start" failed.
dpkg: error processing dirsrv-admin (--configure):
 subprocess post-installation script returned error exit status 1
Setting up openssl-blacklist (0.4.2) ...
Setting up fedora-ds-admin-console (1.1.2-1) ...
Setting up fedora-ds-console (1.1.2-1) ...
Setting up libjss-java (4.2.5-2) ...
Setting up ssl-cert (1.0.23) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 dirsrv-admin
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Not sure how to correct the errors.  I then proceeded to run setup-ds(I figured it wouldn't work with all the errors, but what the heck) and it seemed to go through a normal setup routine.  

I then get to the client set up section, and run cd /opt/fedora-ds, except the directory does not exist.  

Any idea where I messed up?

--shaun

---

### Post by CorvisRex on 2009-02-05
Cool, I really got to try this out one more time, I got side tracked (again, funny how easy that can be) I'll pour over this this weekend.  Probably something silly last time, eay to make mistake when you are trying to install something you have never used before.  Personally, I would really like to test it out on Ubuntu and maybe do a little write up for my site, If I run into any problems, I'll let you know.

raven

---

### Post by francois.mdlh on 2009-04-16
Hey guys

Anyone make any progress on this?

Thanks in advance.

---

