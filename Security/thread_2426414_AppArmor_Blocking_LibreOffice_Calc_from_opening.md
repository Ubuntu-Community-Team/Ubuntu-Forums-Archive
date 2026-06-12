---
title: "AppArmor Blocking LibreOffice Calc from opening"
date: 2019-09-09
forum: Security
---

### Post by lance bermudez on 2019-09-09
AppArmor Blocking LibreOffice Calc from opening How do I stop this? I try to open the program and I get a message at the top of my ubuntu 18.04 gnome desktop. Message says "AppArmor Message" and has what is found in /var/log/kernel.log

# aa-status
```
apparmor module is loaded.
75 profiles are loaded.
40 profiles are in enforce mode.
   /sbin/dhclient
   /snap/core/7396/usr/lib/snapd/snap-confine
   /snap/core/7396/usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   /usr/bin/freshclam
   /usr/bin/man
   /usr/bin/pidgin
   /usr/bin/pidgin//launchpad_integration
   /usr/bin/pidgin//sanitized_helper
   /usr/bin/totem
   /usr/bin/totem-audio-preview
   /usr/bin/totem-video-thumbnailer
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/NetworkManager/nm-dhcp-helper
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/lightdm/lightdm-guest-session
   /usr/lib/lightdm/lightdm-guest-session//chromium
   /usr/lib/snapd/snap-confine
   /usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   /usr/sbin/apt-cacher-ng
   /usr/sbin/clamd
   /usr/sbin/cups-browsed
   /usr/sbin/cupsd
   /usr/sbin/cupsd//third_party
   /usr/sbin/ippusbxd
   /usr/sbin/named
   /usr/sbin/tcpdump
   gst_plugin_scanner
   libreoffice-senddoc
   libreoffice-xpdfimport
   man_filter
   man_groff
   snap-update-ns.core
   snap-update-ns.gnome-characters
   snap-update-ns.gnome-logs
   snap-update-ns.gnome-system-monitor
   snap.core.hook.configure
   snap.gnome-characters.gnome-characters
   snap.gnome-logs.gnome-logs
   snap.gnome-system-monitor.gnome-system-monitor
35 profiles are in complain mode.
   /usr/bin/irssi
   /usr/lib/dovecot/anvil
   /usr/lib/dovecot/auth
   /usr/lib/dovecot/config
   /usr/lib/dovecot/deliver
   /usr/lib/dovecot/dict
   /usr/lib/dovecot/dovecot-auth
   /usr/lib/dovecot/dovecot-lda
   /usr/lib/dovecot/dovecot-lda///usr/sbin/sendmail
   /usr/lib/dovecot/imap
   /usr/lib/dovecot/imap-login
   /usr/lib/dovecot/lmtp
   /usr/lib/dovecot/log
   /usr/lib/dovecot/managesieve
   /usr/lib/dovecot/managesieve-login
   /usr/lib/dovecot/pop3
   /usr/lib/dovecot/pop3-login
   /usr/lib/dovecot/ssl-params
   /usr/sbin/avahi-daemon
   /usr/sbin/dnsmasq
   /usr/sbin/dnsmasq//libvirt_leaseshelper
   /usr/sbin/dovecot
   /usr/sbin/identd
   /usr/sbin/mdnsd
   /usr/sbin/nmbd
   /usr/sbin/nscd
   /usr/sbin/smbd
   /usr/sbin/smbldap-useradd
   /usr/sbin/smbldap-useradd///etc/init.d/nscd
   /usr/{sbin/traceroute,bin/traceroute.db}
   klogd
   libreoffice-oopslash
   ping
   syslog-ng
   syslogd
7 processes have profiles defined.
5 processes are in enforce mode.
   /sbin/dhclient (5920) 
   /usr/bin/freshclam (1569) 
   /usr/sbin/clamd (1591) 
   /usr/sbin/cups-browsed (20179) 
   /usr/sbin/cupsd (20178) 
2 processes are in complain mode.
   /usr/sbin/avahi-daemon (1543) 
   /usr/sbin/avahi-daemon (1556) 
0 processes are unconfined but have a profile defined.

```

/var/kern.log
```

Sep  8 22:08:35 type40tardis kernel: [ 5682.525887] audit: type=1400 audit(1568002115.612:146): apparmor="ALLOWED" operation="exec" info="profile transition not found" error=-13 profile="libreoffice-oopslash" name="/usr/lib/libreoffice/program/soffice.bin" pid=22734 comm="osl_executeProc" requested_mask="x" denied_mask="x" fsuid=1000 ouid=0 target="/usr/lib/libreoffice/program/soffice.bin"
Sep  8 22:14:28 type40tardis kernel: [ 6035.886301] audit: type=1400 audit(1568002468.987:147): apparmor="ALLOWED" operation="exec" info="profile transition not found" error=-13 profile="libreoffice-oopslash" name="/usr/lib/libreoffice/program/soffice.bin" pid=28880 comm="osl_executeProc" requested_mask="x" denied_mask="x" fsuid=1000 ouid=0 target="/usr/lib/libreoffice/program/soffice.bin"

```

# aa-logprof 
```

Reading log entries from /var/log/syslog.
Updating AppArmor profiles in /etc/apparmor.d.

```

---

