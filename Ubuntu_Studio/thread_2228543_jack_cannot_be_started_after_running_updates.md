---
title: "jack cannot be started after running updates"
date: 2014-06-08
forum: Ubuntu Studio
---

### Post by smaring on 2014-06-08
I'm running 14.04 with KDE.  I had jack running just fine ... playing nicely with jack-rack and Mixxx.  After running a bunch of updates, jack won't start.  When I open qjackctl, before I even press "start", the messages window says:

```
03:09:39.246 Patchbay deactivated.
03:09:39.254 Statistics reset.
03:09:39.261 ALSA connection change.
03:09:39.314 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
03:09:39.321 ALSA connection graph change.
```

and as it says, the dbus-daemon does appear to be running:

```
# ps aux | grep dbus
message+   514  0.0  0.0  40916  2840 ?        Ss   03:03   0:00 dbus-daemon --system --fork
nobody    1462  0.0  0.0  31028  1540 ?        S    03:03   0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.1.1 --conf-file=/var/run/NetworkManager/dnsmasq.conf --cache-size=0 --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d
rabbit    1842  0.1  0.0  41332  2596 ?        Ss   03:04   0:01 dbus-daemon --fork --session --address=unix:abstract=/tmp/dbus-nBQX3437p8
rabbit    1880  0.0  0.0  18112   412 ?        S    03:04   0:00 upstart-dbus-bridge --daemon --system --user --bus-name system
rabbit    1882  0.0  0.0  18112   408 ?        S    03:04   0:00 upstart-dbus-bridge --daemon --session --user --bus-name session
rabbit    1927  0.0  0.0  39232  1904 ?        S    03:04   0:00 /bin/dbus-daemon --config-file=/etc/at-spi2/accessibility.conf --nofork --print-address 3
rabbit    4980  0.0  0.0  77812  4188 ?        Ss   03:09   0:00 /usr/bin/jackdbus auto
root      5118  0.0  0.0  76580 10032 ?        S    03:09   0:00 /usr/bin/python /usr/share/apt-xapian-index/update-apt-xapian-index-dbus
```

Almost sounds like it can't find a pid file or something, but I'm stumped.

Any suggestions?

-Steve Maring
Orlando, FL  USA

---

### Post by smaring on 2014-06-08
I killed pulseaudio, restarted jackdbus, and then jack started OK.

Is there a way to keep pulseaudio from starting up like this each time?

---

### Post by jejeman on 2014-06-08
> **smaring said:**
> Is there a way to keep pulseaudio from starting up like this each time?Like what?

---

