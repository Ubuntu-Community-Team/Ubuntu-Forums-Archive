---
title: "Cannot keep NUT running"
date: 2016-11-17
forum: Server Platforms
---

### Post by Karl_Shea on 2016-11-17
I had NUT running just fine on Ubuntu 14.04 and updated (with a new install) the box to 16.04. Since then I keep getting "Data for UPS [qnapups] is stale - check driver" and "Send ping to UPS [qnapups] failed: Resource temporarily unavailable" from upsd and "Poll UPS [qnapups@localhost] failed - Data stale" from upsmon.

I have no clue where to even start looking. Everything works fine for up to a couple of hours and then just stops. What would help track down the issue? Any logs I'm missing?


[IMG]http://i.imgur.com/X78gujjl.png[/IMG]

nut.conf:

```
MODE=netserver
```

ups.conf:

```

maxretry = 5
retrydelay = 5

[qnapups]
        driver = usbhid-ups
        port = auto
```



upsd.conf:

```

MAXAGE 30

LISTEN 0.0.0.0 3493
LISTEN ::0 3493
```

upsd.users:

```
[admin]
        password = 123456
        upsmon master
```

upsmon.conf:

```
MONITOR qnapups@localhost 1 admin 123456 master

POLLFREQ 10
POLLFREQALERT 5
HOSTSYNC 15
DEADTIME 30
```

---

### Post by Karl_Shea on 2016-11-17
Sorry about the spam, the thread wouldn't post.

---

### Post by DuckHook on 2016-11-17
Same  topic  threads merged. Duplicates jailed.

---

### Post by Karl_Shea on 2016-11-17
Thank you. After a couple I figured I'd give up and try today.

---

### Post by cr0wkn0ws on 2017-01-07
I had the same problem when upgrading (migrating) from Linux Mint 17.1 to Ubuntu 16.04.1. Copying the drivers and binaries over didn't help either. Ultimately, I followed the instructions provided here [https://www.mail-archive.com/nut-upsuser@lists.alioth.debian.org/msg09823.html](https://www.mail-archive.com/nut-upsuser@lists.alioth.debian.org/msg09823.html) to recompile the nut binaries with libusb-1.0 (the default Ubuntu package uses the archaic libusb-0.4). I used the config string:


./configure --includedir=/usr/include --mandir=/usr/share/man \ 
--infodir=/usr/share/info --sysconfdir=/etc/nut --localstatedir=/var \ 
--libexecdir=/usr/lib/nut --srcdir=. --disable-maintainer-mode \ 
--disable-dependency-tracking --disable-silent-rules 
--libdir=/usr/lib/x86_64-linux-gnu \ --with-ssl --with-nss --with-cgi 
--with-dev --enable-static \ --with-statepath=/var/run/nut 
--with-altpidpath=/var/run/nut \ --with-drvpath=/lib/nut 
--with-cgipath=/usr/lib/cgi-bin/nut \ --with-htmlpath=/usr/share/nut/www 
--with-pidpath=/var/run/nut \ --datadir=/usr/share/nut 
--with-pkgconfig-dir=/usr/lib/aarch64-linux-gnu/pkgconfig \ --with-user=nut 
--with-group=nut --with-udev-dir=/lib/udev \ 
--with-systemdsystemunitdir=/lib/systemd/system --bindir=/bin --sbindir=/sbin

I then copied the binaries manually to their respective directories (/bin and /sbin) -- DO NOT run 'make install' as the Debian configuration won't work for Ubuntu (!)

Hope this helps.

---

### Post by Karl_Shea on 2017-01-10
FYI I found a PPA in the NUT GitHub issue queue that has been working for me for over a month now: [https://github.com/networkupstools/nut/issues/300#issuecomment-257876389](https://github.com/networkupstools/nut/issues/300#issuecomment-257876389)

---

