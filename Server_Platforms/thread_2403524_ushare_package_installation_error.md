---
title: "ushare package installation error"
date: 2018-10-12
forum: Server Platforms
---

### Post by trip5 on 2018-10-12
Hi. Quick background. I've got a headless box running ubuntu server 18.04 (upgraded from 16.04). I use it for home file storage and media sharing via ushare. I've inherited a newer desktop with an SSD on which I have performed a clean install of ubuntu server 18.04. I'm getting everything set up, but I keep getting an install error when I try to install ushare. I have tried purging, apt-get remove --purge --auto-remove ushare, reboot, and reinstall. Output is:

Job for ushare.service failed because the control process exited with error code .
See "systemctl status ushare.service" and "journalctl -xe" for details.
invoke-rc.d: initscript ushare, action "start" failed.
&#9679; ushare.service - LSB: uShare
Loaded: loaded (/etc/init.d/ushare; generated)
Active: failed (Result: exit-code) since Fri 2018-10-12 14:25:38 UTC; 7ms ago
Docs: man:systemd-sysv-generator(8)
Process: 3042 ExecStart=/etc/init.d/ushare start (code=exited, status=2)


Oct 12 14:25:38 motorsport systemd[1]: Starting LSB: uShare...
Oct 12 14:25:38 motorsport ushare[3042]: /etc/init.d/ushare: 31: .: Can't open / etc/default/rcS
Oct 12 14:25:38 motorsport systemd[1]: ushare.service: Control process exited, c ode=exited status=2
Oct 12 14:25:38 motorsport systemd[1]: ushare.service: Failed with result 'exit- code'.
Oct 12 14:25:38 motorsport systemd[1]: Failed to start LSB: uShare.
dpkg: error processing package ushare (--configure):
installed ushare package post-installation script subprocess returned error exi t status 1
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for libgdk-pixbuf2.0-0:amd64 (2.36.11-2) ...
Processing triggers for ureadahead (0.100.0-20) ...
Processing triggers for systemd (237-3ubuntu10.3) ...
Errors were encountered while processing:
ushare
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help here is much appreciated!

---

### Post by #&amp;thj^% on 2018-10-12
Is  "net-tools" installed?
as it is needed by /var/lib/dpkg/info/ushare.config

---

### Post by trip5 on 2018-10-12
Yes it is installed

---

### Post by trip5 on 2018-10-12
Probably not the right way to do it, but I figured it out. I just created /etc/default/rcS and left it blank. Then reinstalled without issue.

---

### Post by trip5 on 2018-10-12
I also then copied the rcS file contents from my existing server:

# '0' means always, -1 or 'infinite' disables the feature
#TMPTIME=0


# spawn sulogin during boot, continue normal boot if not used in 30 seconds
#SULOGIN=no


# do not allow users to log in until the boot has completed
#DELAYLOGIN=no


# be more verbose during the boot process
#VERBOSE=no


# automatically repair filesystems with inconsistencies during boot
#FSCKFIX=no

---

