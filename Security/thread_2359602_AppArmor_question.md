---
title: "AppArmor question"
date: 2017-04-25
forum: Security
---

### Post by antle on 2017-04-25
Hey.

So i finally decided to teach myself how to use apparmor properly, however i have ran into a problem. For what i understand apparmor is deny by default, so if i have defined profile and put it into enforce mode, then everything that is not defined in profile explicitly gets denied. However, when i created test profile for proftpd or vsftpd, i was still able to read and write whenever my heart pleased if file permissions allowed. What am i doing wrong?

This is my profile for vsftpd

```
# Last Modified: Tue Apr 25 23:38:54 2017
#include <tunables/global>


/usr/sbin/vsftpd {
  #include <abstractions/base>
  #include <abstractions/lxc/container-base>


  /etc/ftpusers r,
  /etc/group r,
  /etc/login.defs r,
  /etc/nsswitch.conf r,
  /etc/pam.d/* r,
  /etc/passwd r,
  /etc/securetty r,
  /etc/shadow r,
  /etc/shells r,
  /etc/vsftpd.conf r,
  /home/*/ rw,
  /usr/sbin/vsftpd mr,
  /var/log/vsftpd.log w,


}

```

---

### Post by antle on 2017-04-25
Took some already made profile and improoved upon it. It works with denying, but i still have not understood where was my error.

New profile looks like this, only difference is that this profile does not use **[COLOR=#000000][FONT=&amp]abstractions/lxc/container-base[/FONT][/COLOR]**[COLOR=#000000][FONT=&amp] but there is nothing there allowing writing to /tmp for example, or reading random files from /etc[/FONT][/COLOR]

```
# Last Modified: Wed Apr 26 00:39:00 2017
#include <tunables/global>


/usr/sbin/vsftpd {
  #include <abstractions/authentication>
  #include <abstractions/base>
  #include <abstractions/nameservice>


  capability audit_write,
  capability setgid,
  capability setuid,
  capability sys_admin,
  capability sys_chroot,


  /dev/urandom r,
  /etc/fstab r,
  /etc/ftpusers r,
  /etc/hosts.allow r,
  /etc/hosts.deny r,
  /etc/mtab r,
  /etc/shells r,
  /etc/vsftpd.* r,
  /etc/vsftpd/* r,
  /home/*/ r,
  /usr/sbin/vsftpd mrix,
  /var/log/vsftpd.log w,
  /var/log/xferlog w,
  @{HOMEDIRS} r,
  @{HOME}/** rwl,


}

```

---

### Post by anoda on 2017-04-28
Hi **Antle**. Could You check log files such as **/var/log/kern.log** etc. for any DENIED messages? And what excatlly do You want to achieve?  Thanks.

---

