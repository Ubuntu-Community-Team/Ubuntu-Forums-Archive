---
title: "mysql/bizarre permission denied errors as root"
date: 2008-06-03
forum: Server Platforms
---

### Post by heddhunter on 2008-06-03
i'm having a very weird problem installing mysql.  i created a big RAID-5 array (/dev/md0) mounted on /var/media.  if i do

mysql_install_db --datadir=/var/media/mysql

i get:

$ sudo mysql_install_db --datadir=/var/media/mysql
Installing MySQL system tables...
080603 20:22:53 [Warning] Can't create test file /var/media/mysql/monolith.lower-test
080603 20:22:53 [Warning] Can't create test file /var/media/mysql/monolith.lower-test
ERROR: 1005  Can't create table 'db' (errno: 13)
080603 20:22:53 [ERROR] Aborting

080603 20:22:53 [Note] /usr/sbin/mysqld: Shutdown complete

Installation of system tables failed!


It works just fine if I install it on /var/lib/mysql, or /tmp, or anywhere else basically.  Of course, I'm out of space everywhere else and I want to use the giant RAID i put together specifically for this purpose...

I don't have any problem creating files on this partition as root, or as a normal user in a directory that has user write permission.

I just noticed message like this in the system log:

Jun  3 20:22:53 monolith kernel: [ 9834.697327] audit(1212549773.394:53): type=1503 operation="inode_create" requested_mask="w::" denied_mask="w::" name="/var/media/mysql/monolith.lower-test" pid=11679 profile="/usr/sbin/mysqld" namespace="default"

That's a new one on me... ?

---

### Post by windependence on 2008-06-04
Check the ownership AND permissions on /var/lib/mysql and make them excactly the same on /var/media.

Also, from googling, it looks like this is an apparmor problem. I disable apparmor in my installs because IMHO it causes more problems than it's worth.

-Tim

---

### Post by heddhunter on 2008-06-04
> **windependence said:**
> Check the ownership AND permissions on /var/lib/mysql and make them excactly the same on /var/media.

Also, from googling, it looks like this is an apparmor problem. I disable apparmor in my installs because IMHO it causes more problems than it's worth.

-Tim

you're right, it was an apparmor issue.  i set it to complain on mysqld instead of enforce and now i'm good to go.

i am new to ubuntu (but have a dozen years of unix/bsd/redhat under my belt) so i'd never heard of apparmor before today.  i think you are right about it being more trouble than it's worth.

---

### Post by Xerp on 2008-06-05
I've also just hit this one, but I'm not doing anything "funny" - everything is the installation default. AppArmor won't let MySQL start. Would this class as a bug? Surely the default apt-get install mysql should work?

What needs to be changed? I assume it is something in /etc/apparmor.d/usr.sbin.mysqld

For now I am testing and have simply disabled the whole of AppArmor. Ultimately this is not what I want to do :)

I have the default:

# vim:syntax=apparmor
# Last Modified: Tue Jun 19 17:37:30 2007
#include <tunables/global>

/usr/sbin/mysqld {
  #include <abstractions/base>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>
  #include <abstractions/mysql>

  capability dac_override,
  capability setgid,
  capability setuid,

  /etc/hosts.allow r,
  /etc/hosts.deny r,

  /etc/group              m,
  /etc/passwd             m,

  /etc/mysql/*.pem r,
  /etc/mysql/conf.d/ r,
  /etc/mysql/conf.d/* r,
  /etc/mysql/my.cnf r,
  /usr/sbin/mysqld mr,
  /usr/share/mysql/** r,
  /var/lib/mysql/ r,
  /var/lib/mysql/** rwk,
  /var/log/mysql/ r,
  /var/log/mysql/* rw,
  /var/run/mysqld/mysqld.pid w,
  /var/run/mysqld/mysqld.sock w,
}

And it won't let MySQL create the socket, /var/run/mysqld/mysqld.sock

I get:

kernel: [ 1185.380430] audit(1212667771.111:15): type=1503 operation="inode_permission" requested_mask="w::" denied_mask="w::" name="/var/lib/lwidentity/lwidentity_privileged/pipe" pid=6770 profile="/usr/sbin/mysqld" namespace="default"

and

/etc/init.d/mysql[6932]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'

---

