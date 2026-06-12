---
title: "[SOLVED] vsftpd configuration"
date: 2009-01-11
forum: Server Platforms
---

### Post by AlexDudko on 2009-01-11
I've recently moved back to Ubuntu from Fedora. Apache, PHP, MySQL, vsftp are installed. 
I want to configure a number of virtual hosts with their root directories in local users' home directories. Apache was configured with the ease, but with ftp login a user can access the / directory of the server, which isn't a good idea. How can I configure vsftpd so that a remote user, which can login to the server could see just his directory directory and couldn't go beyond it? 
I had that configuration, but I can't get in in Ubuntu.

---

### Post by RealPSL on 2009-01-11
Below is text taken from the sample configuration file provided with Ubuntu it details the options for chrooting local users

```
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
chroot_list_enable=YES
# (default follows)
chroot_list_file=/etc/vsftpd.chroot_list

```

---

### Post by AlexDudko on 2009-01-12
Used this guide which suited me perfectly:
[http://www.howtoforge.com/vsftpd_mysql_debian_etch]("http://www.howtoforge.com/vsftpd_mysql_debian_etch")

---

