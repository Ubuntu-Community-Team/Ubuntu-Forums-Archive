---
title: "Apparmor profile for Apache2"
date: 2009-09-15
forum: Security
---

### Post by Sporkman on 2009-09-15
Hi All,

Here's a template for apache2 that you can start with. It may be more or less restrictive for what you're running on your website (for example, I don't use MySQL), so you'll need to run it for a while in complain mode until you don't see any more "audit" warnings in /var/log/messages. You'll also need to add read permission for your website's document root.



/usr/sbin/apache2 flags=(complain) {
  #include <abstractions/base>

  capability kill,
  capability net_bind_service,
  capability setuid,
  capability setgid,
  network inet,
  network inet6,

  /dev/tty rw,
  /etc/apache2/** r,
  /etc/gai.conf r,
  /etc/group r,
  /etc/host* r,
  /etc/mime.types r,
  /etc/nsswitch.conf r,
  /etc/passwd r,
  /etc/php5/apache2/php.ini r,
  /etc/php5/conf.d/ r,
  /etc/php5/conf.d/*.ini r,
  /etc/protocols r,
  /etc/resolv.conf r,
  /etc/services r,
  /proc/[0-9]*/mounts r,
  /proc/filesystems r,
  /usr/bin/env rix,
  /usr/bin/host rix,
  /usr/lib/apache2/modules/** mr,
  /usr/lib/php5/[0-9]*/*.so rix,
  /usr/sbin/apache2 r,
  /usr/share/apache2/icons/* r,
  /usr/share/file/magic.mime r,
  /usr/share/zoneinfo/ r,
  /var/log/apache2/** rw,
  /var/run/apache2.pid w,
  /tmp/ rw,
  /tmp/php* rw,
}

---

### Post by TheAlien on 2010-09-29
I know that this thread is some old, but thanks anyway! :)

---

