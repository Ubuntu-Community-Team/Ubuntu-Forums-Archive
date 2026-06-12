---
title: "Bind9 still failing"
date: 2008-12-21
forum: Server Platforms
---

### Post by docfx on 2008-12-21
Installed Hardy updated to 8.04.1LTS w/LVM

All was well, 
```
Dec 20 16:21:14 wonder named[31642]: starting BIND 9.4.2-P2 -u bind
Dec 20 16:21:14 wonder named[31642]: found 1 CPU, using 1 worker thread
Dec 20 16:21:14 wonder named[31642]: loading configuration from '/etc/bind/named.conf'
Dec 20 16:21:14 wonder named[31642]: listening on IPv6 interfaces, port 53

```

then I started going thru the Howtoforge "perfect server" tutorial. Got to the part where bind gets chrooted and... 

Bind 9 fails - acc'd to /var/log/syslog:
```
Dec 21 14:00:54 wonder named[6828]: starting BIND 9.4.2-P2 -u bind -t /var/lib/named
Dec 21 14:00:54 wonder named[6828]: found 1 CPU, using 1 worker thread
Dec 21 14:00:54 wonder named[6828]: loading configuration from '/etc/bind/named.conf'
Dec 21 14:00:54 wonder named[6828]: none:0: open: /etc/bind/named.conf: permission denied
Dec 21 14:00:54 wonder named[6828]: loading configuration: permission denied
Dec 21 14:00:54 wonder named[6828]: exiting (due to fatal error)
``` 

Have tried it, per the tutorial ( w/ AppArmor disabled/purged ) as well as per Ubuntu Forum ( ubuntuforums.org/showthread.php?t=735188&highlight=bind9+fail ). 

AppArmor is currently running and my usr.sbin.named is:
```
# vim:syntax=apparmor
# Last Modified: Fri Jun  1 16:43:22 2007
#include <tunables/global>

/usr/sbin/named {
  #include <abstractions/base>
  #include <abstractions/nameservice>

  capability net_bind_service,
  capability setgid,
  capability setuid,
  capability sys_chroot,

  # /etc/bind should be read-only for bind
  # /var/lib/bind is for dynamically updated zone (and journal) files.
  # /var/cache/bind is for slave/stub data, since we're not the origin of it.
  # See /usr/share/doc/bind9/README.Debian.gz
  # /etc/bind/** r,

  # Dynamic updates needs zone and journal files rw. We just allow rw for all
  # in /etc/bind, and let DAC handle the rest > moved to /var/lib/named/etc/bind
  /var/lib/named/etc/bind/* rw,

  # if local zones are in a subdirectory
  /var/lib/named/etc/bind/zones/* rw,
  /var/lib/named/etc/bind/zones/external/* rw,
  /var/lib/named/etc/bind/zones/internal/* rw,

  /var/lib/bind/** rw,
  /var/lib/bind/ rw,
  /var/cache/bind/** rw,
  /var/cache/bind/ rw,

  # some people like to put logs in /var/log/named/
  /var/log/named/** rw,

  # dnscvsutil package
  /var/lib/dnscvsutil/compiled/** rw,

  /proc/net/if_inet6 r,
  /usr/sbin/named mr,
  /var/lib/named/var/run/bind/run/named.pid w,
  #/var/run/bind/run/named.pid w,
  # support for resolvconf
  /var/lib/named/var/run/bind/named.options r,
  #/var/run/bind/named.options r,

# add also following lines thanks to Spezi2u
  /var/lib/named/dev/null rw,
  /var/lib/named/dev/random rw,

}

```

Contents of /etc/bind/ aka /var/lib/named/etc/bind/ are:
```
-rw-r--r-- 1 bind bind  237 2008-04-09 15:44 db.0
-rw-r--r-- 1 bind bind  271 2008-04-09 15:44 db.127
-rw-r--r-- 1 bind bind  237 2008-04-09 15:44 db.255
-rw-r--r-- 1 bind bind  353 2008-04-09 15:44 db.empty
-rw-r--r-- 1 bind bind  270 2008-04-09 15:44 db.local
-rw-r--r-- 1 bind bind 2878 2008-04-09 15:44 db.root
-rw-r--r-- 1 bind bind  907 2008-04-09 15:44 named.conf
-rw-r--r-- 1 bind bind  165 2008-04-09 15:44 named.conf.local
-rw-r--r-- 1 bind bind 3041 2008-12-21 13:51 named.conf.options
-rw------- 1 root root  695 2008-12-21 13:51 named.conf.options~
-rw-r----- 1 bind bind   77 2008-05-26 17:26 rndc.key
-rw-r--r-- 1 bind bind 1317 2008-04-09 15:44 zones.rfc1918
```

and still bind9 refuses to start from CLI or during reboot... It doesn't see to make any difference if I use OPTIONS="-u bind -t /var/lib/named" or OPTIONS="-u bind".

Any suggestions would greatly appreciated.

---

### Post by docfx on 2008-12-23
In that the error I'm seeing does not appear to be AppArmor related, I concentrated on just pure permission issues...

chmod 755 of /var/lib/named/etc and /var/lib/named quieted down that error, but then spawned two more errors (now that it could see named.conf and named.conf.options.

```
Dec 23 09:11:24 wonder named[10340]: starting BIND 9.4.2-P2 -u bind -t /var/lib/named
Dec 23 09:11:24 wonder named[10340]: found 1 CPU, using 1 worker thread
Dec 23 09:11:24 wonder named[10340]: loading configuration from '/etc/bind/named.conf'
Dec 23 09:11:24 wonder named[10340]: /etc/bind/named.conf.options:93: change directory to '/var/cache/bind'
Dec 23 09:11:24 wonder named[10340]: /etc/bind/named.conf.options:93: parsing failed
Dec 23 09:11:24 wonder named[10340]: loading configuration: permission denied
Dec 23 09:11:24 wonder named[10340]: exiting (due to fatal error
```

ok... so by commenting out the original directory string in named.conf.options (directory "/var/cache/bind"; ), I eliminated that error, but meant I no longer was specifying where the zone files are... 

chmod 755 to /var/lib/named/var/cache/bind and /var/lib/named/cache (or where-ever you plan to put them) fixed that error, but I was NOW getting errors regarding entropy /dev/random and named.pid...

```
Dec 23 10:37:19 wonder named[10423]: starting BIND 9.4.2-P2 -u bind -t /var/lib/named
Dec 23 10:37:19 wonder named[10423]: found 1 CPU, using 1 worker thread
Dec 23 10:37:19 wonder named[10423]: loading configuration from '/etc/bind/named.conf'
Dec 23 10:37:19 wonder named[10423]: listening on IPv6 interfaces, port 53
Dec 23 10:37:19 wonder named[10423]: listening on IPv4 interface lo, 127.0.0.1#53
Dec 23 10:37:19 wonder named[10423]: listening on IPv4 interface eth0, 192.168.5.11#53
Dec 23 10:37:19 wonder named[10423]: automatic empty zone: 254.169.IN-ADDR.ARPA
Dec 23 10:37:19 wonder named[10423]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
Dec 23 10:37:19 wonder named[10423]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
Dec 23 10:37:19 wonder named[10423]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Dec 23 10:37:19 wonder named[10423]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Dec 23 10:37:19 wonder named[10423]: automatic empty zone: D.F.IP6.ARPA
Dec 23 10:37:19 wonder named[10423]: automatic empty zone: 8.E.F.IP6.ARPA
Dec 23 10:37:19 wonder named[10423]: automatic empty zone: 9.E.F.IP6.ARPA
Dec 23 10:37:19 wonder named[10423]: automatic empty zone: A.E.F.IP6.ARPA
Dec 23 10:37:19 wonder named[10423]: automatic empty zone: B.E.F.IP6.ARPA
Dec 23 10:37:19 wonder named[10423]: command channel listening on 127.0.0.1#953
Dec 23 10:37:19 wonder named[10423]: command channel listening on ::1#953
Dec 23 10:37:19 wonder named[10423]: could not open entropy source /dev/random: permission denied
Dec 23 10:37:19 wonder named[10423]: using pre-chroot entropy source /dev/random
Dec 23 10:37:19 wonder named[10423]: couldn't open pid file '/var/run/bind/run/named.pid': Permission denied
Dec 23 10:37:19 wonder named[10423]: exiting (due to early fatal error)
```

chmod 755 to /var/lib/named/dev/ seems to fix the 'entropy source' error... ( /dev/random/ is actually /var/lib/named/dev/random due to chroot)

```
Dec 23 11:07:29 wonder named[10480]: starting BIND 9.4.2-P2 -u bind -t /var/lib/named
Dec 23 11:07:29 wonder named[10480]: found 1 CPU, using 1 worker thread
Dec 23 11:07:29 wonder named[10480]: loading configuration from '/etc/bind/named.conf'
Dec 23 11:07:29 wonder named[10480]: listening on IPv6 interfaces, port 53
Dec 23 11:07:29 wonder named[10480]: listening on IPv4 interface lo, 127.0.0.1#53
Dec 23 11:07:29 wonder named[10480]: listening on IPv4 interface eth0, 192.168.5.11#53
Dec 23 11:07:29 wonder named[10480]: automatic empty zone: 254.169.IN-ADDR.ARPA
Dec 23 11:07:29 wonder named[10480]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
Dec 23 11:07:29 wonder named[10480]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
Dec 23 11:07:29 wonder named[10480]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Dec 23 11:07:29 wonder named[10480]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Dec 23 11:07:29 wonder named[10480]: automatic empty zone: D.F.IP6.ARPA
Dec 23 11:07:29 wonder named[10480]: automatic empty zone: 8.E.F.IP6.ARPA
Dec 23 11:07:29 wonder named[10480]: automatic empty zone: 9.E.F.IP6.ARPA
Dec 23 11:07:29 wonder named[10480]: automatic empty zone: A.E.F.IP6.ARPA
Dec 23 11:07:29 wonder named[10480]: automatic empty zone: B.E.F.IP6.ARPA
Dec 23 11:07:29 wonder named[10480]: command channel listening on 127.0.0.1#953
Dec 23 11:07:29 wonder named[10480]: command channel listening on ::1#953
Dec 23 11:07:29 wonder named[10480]: couldn't open pid file '/var/run/bind/run/named.pid': Permission denied
Dec 23 11:07:29 wonder named[10480]: exiting (due to early fatal error)
```

chmod 755 to /var/lib/named/var/run/bind/, /var/lib/named/var/run/, and finally /var/lib/named/var/ eliminated the 'permission denied' error for named.pid (again, /var/run/bind/run/named.pid is actually /var/lib/named/var/run/bind/run/named.pid due to chroot)

```
Dec 23 11:14:37 wonder named[10604]: starting BIND 9.4.2-P2 -u bind -t /var/lib/named
Dec 23 11:14:37 wonder named[10604]: found 1 CPU, using 1 worker thread
Dec 23 11:14:37 wonder named[10604]: loading configuration from '/etc/bind/named.conf'
Dec 23 11:14:37 wonder named[10604]: listening on IPv6 interfaces, port 53
Dec 23 11:14:37 wonder named[10604]: listening on IPv4 interface lo, 127.0.0.1#53
Dec 23 11:14:37 wonder named[10604]: listening on IPv4 interface eth0, 192.168.5.11#53
Dec 23 11:14:37 wonder named[10604]: automatic empty zone: 254.169.IN-ADDR.ARPA
Dec 23 11:14:37 wonder named[10604]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
Dec 23 11:14:37 wonder named[10604]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
Dec 23 11:14:37 wonder named[10604]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Dec 23 11:14:37 wonder named[10604]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Dec 23 11:14:37 wonder named[10604]: automatic empty zone: D.F.IP6.ARPA
Dec 23 11:14:37 wonder named[10604]: automatic empty zone: 8.E.F.IP6.ARPA
Dec 23 11:14:37 wonder named[10604]: automatic empty zone: 9.E.F.IP6.ARPA
Dec 23 11:14:37 wonder named[10604]: automatic empty zone: A.E.F.IP6.ARPA
Dec 23 11:14:37 wonder named[10604]: automatic empty zone: B.E.F.IP6.ARPA
Dec 23 11:14:37 wonder named[10604]: command channel listening on 127.0.0.1#953
Dec 23 11:14:37 wonder named[10604]: command channel listening on ::1#953
Dec 23 11:14:37 wonder named[10604]: zone 0.in-addr.arpa/IN: loaded serial 1
Dec 23 11:14:37 wonder named[10604]: zone 127.in-addr.arpa/IN: loaded serial 1
Dec 23 11:14:37 wonder named[10604]: zone 255.in-addr.arpa/IN: loaded serial 1
Dec 23 11:14:37 wonder named[10604]: zone localhost/IN: loaded serial 2
Dec 23 11:14:37 wonder named[10604]: running
```

so is this unique to my install?... did I miss a permissions step somewhere in the tutorial?... should this be added to the 'perfect server' tutor?

I'm pretty sure that I followed the tutorial step-by-step (copy/pasting in most cases so as to NOT enter a typo anywhere), but have NOT seen anywhere where all these permissions needed resetting. 

That said, I'd be interested in hearing from those more clever than I, if this is normal, if I missed something earlier in the process that would have negated these permission changes, and/or if these changes have opened a hole I'm not immediately aware of.

Failing that, I hope this assists someone else if they see the same thing.

---

