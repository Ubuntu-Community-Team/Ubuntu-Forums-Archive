---
title: "AppArmor Skipping Profile (usr.sbin.mysqld)"
date: 2008-07-04
forum: Security
---

### Post by thornomad on 2008-07-04
Hi everyone -

I have upgraded from 6.06.1 to 8.04 on my headless server; everything is great except for a [problem with SqueezeCenter]("http://forums.slimdevices.com/showthread.php?t=46614"): there is a conflict with AppArmor that prevents it from running.  

Anyhow: there are suggestions for fixes at the SlimDevices forums, but all of these suggestions require me to edit and use my: /etc/apparmor.d/usr.sbin.msyql profile in AppArmor.

However, the problem I am having is that when I reload /etc/init.d/apparmor I get an error:

```
$ sudo /etc/init.d/apparmor reload
Reloading AppArmor profiles  Skipping profile /etc/apparmor.d/usr.sbin.mysqld
: Warning.
```

So I can't actually test any of the changes recommended by the SlimServer people 'cause this profile isn't loading to begin with.  AppArmor is new to me; how do I figure out what is wrong ?  My usr.sbin.mysqld file is the default one:

```
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
```

Any ideas ?  How do I find out what's wrong?

Thanks

---

### Post by Nomad64 on 2008-07-22
Hmm...not sure why AppArmor is skipping that profile, but your differs from the one I have with SqueezeCenter installed. Mine looks like:
```
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

  # SqueezeCenter Apparmor Changes for MySqld
  /var/lib/squeezecenter/cache/ r,
  /var/lib/squeezecenter/cache/my.cnf r,
  /var/lib/squeezecenter/cache/mysql.startup rw,
  /var/lib/squeezecenter/cache/mysql-error-log.txt rw,
  /var/lib/squeezecenter/cache/squeezecenter-mysql.pid w,
  /var/lib/squeezecenter/cache/squeezecenter-mysql.sock w,
  /var/lib/squeezecenter/cache/MySQL/ r,
  /var/lib/squeezecenter/cache/MySQL/** rwk,
 }

```

Also, I had to run the following command in order for AppArmor to work properly with SqueezeCenter.
```
sudo rm /etc/apparmor.d/usr.sbin.mysqld.squeezecenter.orig
```

This problem is a bug with SqueezeCenter: [http://bugs.slimdevices.com/show_bug.cgi?id=7580](http://bugs.slimdevices.com/show_bug.cgi?id=7580)

Hopefully this helps you!

---

### Post by PmDematagoda on 2008-07-23
If the OP is still around, post the outputs of:-
```
sudo apparmor_status
```
and
```
sudo apparmor_parser -a /etc/apparmor.d/usr.sbin.mysqld
```

---

