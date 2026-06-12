---
title: "Lot of Apparmor &quot;DENIED&quot; and cant print"
date: 2022-09-26
forum: Ubuntu Development Version
---

### Post by osse7 on 2022-09-26
Since a couple of weeks, printing is an issue: print job is stopped.
Looking at logs, many Apparmor DENIED around cups and snap:

```
AVC apparmor="DENIED" operation="connect" profile="/usr/sbin/cups-browsed" name="/run/systemd/resolve/io.systemd.Resolve" pid=1244 comm="cups-browsed" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=101
kernel: audit: type=1400 audit(1664169645.447:47): apparmor="DENIED" operation="connect" profile="/usr/sbin/cups-browsed" name="/run/systemd/resolve/io.systemd.Resolve" pid=1244 comm="cups-browsed" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=101
kernel: audit: type=1400 audit(1664169645.471:48): apparmor="DENIED" operation="connect" profile="/usr/sbin/cups-browsed" name="/run/systemd/resolve/io.systemd.Resolve" pid=1244 comm="cups-browsed" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=101
 AVC apparmor="DENIED" operation="connect" profile="/usr/sbin/cups-browsed" name="/run/systemd/resolve/io.systemd.Resolve" pid=1244 comm="cups-browsed" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=101
audit[4546]: AVC apparmor="DENIED" operation="mkdir" profile="snap-update-ns.firefox" name="/usr/share/cups/doc-root/" pid=4546 comm="6" requested_mask="c" denied_mask="c" fsuid=0 ouid=0
audit[4546]: AVC apparmor="DENIED" operation="mkdir" profile="snap-update-ns.firefox" name="/usr/share/gimp/2.0/" pid=4546 comm="6" requested_mask="c" denied_mask="c" fsuid=0 ouid=0
 AVC apparmor="DENIED" operation="mkdir" profile="snap-update-ns.firefox" name="/usr/share/libreoffice/help/" pid=4546 comm="6" requested_mask="c" denied_mask="c" fsuid=0 ouid=0
 AVC apparmor="DENIED" operation="open" profile="snap-update-ns.firefox" name="/var/lib/" pid=4546 comm="6" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
kernel: audit: type=1400 audit(1664169970.403:58): apparmor="DENIED" operation="mkdir" profile="snap-update-ns.firefox" name="/usr/share/cups/doc-root/" pid=4546 comm="6" requested_mask="c" denied_mask="c" fsuid=0 ouid=0
kernel: audit: type=1400 audit(1664169970.403:59): apparmor="DENIED" operation="mkdir" profile="snap-update-ns.firefox" name="/usr/share/gimp/2.0/" pid=4546 comm="6" requested_mask="c" denied_mask="c" fsuid=0 ouid=0
kernel: audit: type=1400 audit(1664169970.403:60): apparmor="DENIED" operation="mkdir" profile="snap-update-ns.firefox" name="/usr/share/libreoffice/help/" pid=4546 comm="6" requested_mask="c" denied_mask="c" fsuid=0 ouid=0
kernel: audit: type=1400 audit(1664169970.403:61): apparmor="DENIED" operation="open" profile="snap-update-ns.firefox" name="/var/lib/" pid=4546 comm="6" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
audit[5282]: AVC apparmor="DENIED" operation="capable" profile="/usr/lib/snapd/snap-confine" pid=5282 comm="snap-confine" capability=12  capname="net_admin"
audit[5282]: AVC apparmor="DENIED" operation="capable" profile="/usr/lib/snapd/snap-confine" pid=5282 comm="snap-confine" capability=38  capname="perfmon"
kernel: audit: type=1400 audit(1664170061.076:62): apparmor="DENIED" operation="capable" profile="/usr/lib/snapd/snap-confine" pid=5282 comm="snap-confine" capability=12  capname="net_admin"
kernel: audit: type=1400 audit(1664170061.076:63): apparmor="DENIED" operation="capable" profile="/usr/lib/snapd/snap-confine" pid=5282 comm="snap-confine" capability=38  capname="perfmon"
```

I have tested and set cups in complain mode; but thart makes no difference, and print jobs still wait into the queue. Wonder if those are set by systemd processes ?

---

### Post by mIk3_08 on 2022-09-27
Please run the command below and paste the result here in thread. Regards and cheers.
```
hostnamectl
```
Have you tried driverless in your printer?

---

### Post by #&amp;thj^% on 2022-09-27
Can you include this as well please:
```
cd /etc/apparmor.d &&
find . -type f -exec grep -i -n firefox {} \; -print >/home/username/apparmor.txt
```
Replace username with your username.

---

### Post by osse7 on 2022-09-27
Thanks for your replies :P

 Operating System: Ubuntu Kinetic Kudu (development branch)
          Kernel: Linux 5.19.0-18-generic
    Architecture: x86-64

there is no problem with firefox itself; but mainly with cupsd, which some files are shown as "unknown type" into /etc/cupsd/  like cupsd.conf for example  and cant be edited

Multiple OS systems have recently reported same cups issues, like : [https://bugs.launchpad.net/ubuntu/+source/cups-filters/+bug/1989587](https://bugs.launchpad.net/ubuntu/+source/cups-filters/+bug/1989587)

---

### Post by osse7 on 2022-10-10
Previous Apparmor reported above are now gone :P
but the main issue is now with firefox:   apparmor="DENIED" operation="getattr" class="file" profile="snap.firefox.firefox" name="/var/lib/snapd/void/"

---

