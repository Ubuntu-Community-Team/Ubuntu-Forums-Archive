---
title: "sudo apt-get install ubuntu-desktop fails"
date: 2010-12-10
forum: Server Platforms
---

### Post by fistv on 2010-12-10
and has been failing for the last two days, I installed both the lto and the 10.10 newest, starts out OK and runs for about 5 minutes then finishes with many 'failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/](http://us.archive.ubuntu.com/ubuntu/pool/main/p/)....' size mismatch issues.
This is the first one after many installs over the last two years. Is there something going on with the US servers ?

On closer examination of running sudo apt-get update it seems to be fine till it hits the pool directory on the server, lucid main and lucid-updates are fine, breaks when it goes past those.

---

### Post by fistv on 2010-12-10
OK, tried again, apt-get install ubuntu-desktop will not get anything past lucid-update/main or lucid/main. Any suggestions.

---

### Post by FreeComputerHelp on 2010-12-10
If you want to update your Ubuntu Distro Please type in:

sudo do-release-upgrade

:-)

---

### Post by fistv on 2010-12-13
This is a sample of what I get when I try to do an update on anything below lucid/main or lucid-update/main.
There appears to be a problem below those directories and this is after reinstalling the server a few times just in case I messed up the install somehow. 
Somebody might want to take a look at it.

cut from the update manager

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/tar/tar_1.22-2ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/tar/tar_1.22-2ubuntu1_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-24-generic-pae_2.6.32-24.43_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-24-generic-pae_2.6.32-24.43_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-26-generic-pae_2.6.32-26.48_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-26-generic-pae_2.6.32-26.48_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.1/mysql-common_5.1.41-3ubuntu12.8_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.1/mysql-common_5.1.41-3ubuntu12.8_all.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.1/mysql-server_5.1.41-3ubuntu12.8_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.1/mysql-server_5.1.41-3ubuntu12.8_all.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.1/libmysqlclient16_5.1.41-3ubuntu12.8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.1/libmysqlclient16_5.1.41-3ubuntu12.8_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.1/mysql-client-core-5.1_5.1.41-3ubuntu12.8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.1/mysql-client-core-5.1_5.1.41-3ubuntu12.8_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.1/mysql-client-5.1_5.1.41-3ubuntu12.8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.1/mysql-client-5.1_5.1.41-3ubuntu12.8_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.1/mysql-server-core-5.1_5.1.41-3ubuntu12.8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.1/mysql-server-core-5.1_5.1.41-3ubuntu12.8_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.1/mysql-server-5.1_5.1.41-3ubuntu12.8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.1/mysql-server-5.1_5.1.41-3ubuntu12.8_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.7.25.3ubuntu9.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.7.25.3ubuntu9.3_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8k-7ubuntu8.5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8k-7ubuntu8.5_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libcomerr2_1.41.11-1ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libcomerr2_1.41.11-1ubuntu2.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libss2_1.41.11-1ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libss2_1.41.11-1ubuntu2.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-utils_0.7.25.3ubuntu9.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-utils_0.7.25.3ubuntu9.3_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bzip2/bzip2_1.0.5-4ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bzip2/bzip2_1.0.5-4ubuntu0.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bzip2/libbz2-1.0_1.0.5-4ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bzip2/libbz2-1.0_1.0.5-4ubuntu0.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/ureadahead/ureadahead_0.100.0-4.1.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/ureadahead/ureadahead_0.100.0-4.1.3_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.12-1.1ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.12-1.1ubuntu2.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/i/ifupdown/ifupdown_0.6.8ubuntu29.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/i/ifupdown/ifupdown_0.6.8ubuntu29.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/lvm2/libdevmapper1.02.1_1.02.39-1ubuntu4.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/lvm2/libdevmapper1.02.1_1.02.39-1ubuntu4.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/udev/libudev0_151-12.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/udev/libudev0_151-12.2_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_151-12.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_151-12.2_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/lvm2/dmsetup_1.02.39-1ubuntu4.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/lvm2/dmsetup_1.02.39-1ubuntu4.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mountall/mountall_2.15.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mountall/mountall_2.15.3_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_0.7.25.3ubuntu9.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_0.7.25.3ubuntu9.3_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/krb5/libk5crypto3_1.8.1+dfsg-2ubuntu0.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/krb5/libk5crypto3_1.8.1+dfsg-2ubuntu0.4_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/krb5/libgssapi-krb5-2_1.8.1+dfsg-2ubuntu0.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/krb5/libgssapi-krb5-2_1.8.1+dfsg-2ubuntu0.4_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5-3_1.8.1+dfsg-2ubuntu0.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5-3_1.8.1+dfsg-2ubuntu0.4_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5support0_1.8.1+dfsg-2ubuntu0.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5support0_1.8.1+dfsg-2ubuntu0.4_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.7.6.dfsg-1ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.7.6.dfsg-1ubuntu1.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisc60_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisc60_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libdns64_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libdns64_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc60_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc60_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg60_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg60_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres60_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres60_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-60_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-60_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/man-db/man-db_2.5.7-2ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/man-db/man-db_2.5.7-2ubuntu1_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/plymouth/plymouth-theme-ubuntu-text_0.8.2-2ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/plymouth/plymouth-theme-ubuntu-text_0.8.2-2ubuntu2.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apr-util/libaprutil1-ldap_1.3.9+dfsg-3ubuntu0.10.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apr-util/libaprutil1-ldap_1.3.9+dfsg-3ubuntu0.10.04.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apr-util/libaprutil1-dbd-sqlite3_1.3.9+dfsg-3ubuntu0.10.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apr-util/libaprutil1-dbd-sqlite3_1.3.9+dfsg-3ubuntu0.10.04.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apr-util/libaprutil1_1.3.9+dfsg-3ubuntu0.10.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apr-util/libaprutil1_1.3.9+dfsg-3ubuntu0.10.04.1_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apache2/apache2_2.2.14-5ubuntu8.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apache2/apache2_2.2.14-5ubuntu8.4_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-mpm-prefork_2.2.14-5ubuntu8.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-mpm-prefork_2.2.14-5ubuntu8.4_i386.deb)
  Size mismatch

---

