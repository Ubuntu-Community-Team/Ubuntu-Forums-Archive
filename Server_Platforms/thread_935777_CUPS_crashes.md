---
title: "CUPS crashes"
date: 2008-10-02
forum: Server Platforms
---

### Post by garysims on 2008-10-02
Hi,

I am trying to set-up a printer via CUPS on my Ubuntu 8.04 server and CUPS is crashing.

I can access CUPS fine (having tweaked the cupsd.conf via cupsctl to allow remote access) and my printer is detected via the Parallel port via I click on "Find New Printers". The correct model (Canon BJC 2100) is detected on the "Model/Driver" page, but when I click "Add Printer" cups crashes. The web browser says the page contains no data and cups needs to be restarted before the web interface will appear again.

This is ONLY a problem on the SERVER. I tried exactly the same thing on the desktop version and it works fine.

Has anyone else seen this?

Thanks, Gary

---

### Post by windependence on 2008-10-02
What is in your /var/log/messages?

-Tim

---

### Post by garysims on 2008-10-02
Tim,

Thanks for your reply.... Here is what I find in messages:

Oct  2 08:35:05 ubuntu466 kernel: [ 1478.184018] audit(1222932905.430:10): type=1503 operation="inode_permission" requested_mask="rw::" denied_mask="rw::" name="/var/lib/samba/secrets.tdb" pid=4355 profile="/usr/sbin/cupsd" namespace="default"
Oct  2 08:35:05 ubuntu466 kernel: [ 1478.187577] audit(1222932905.440:11): type=1503 operation="inode_permission" requested_mask="rw::" denied_mask="rw::" name="/var/lib/samba/passdb.tdb" pid=4355 profile="/usr/sbin/cupsd" namespace="default"
Oct  2 08:35:05 ubuntu466 kernel: [ 1478.190249] audit(1222932905.440:12): type=1503 operation="inode_permission" requested_mask="rw::" denied_mask="rw::" name="/var/lib/samba/passdb.tdb" pid=4355 profile="/usr/sbin/cupsd" namespace="default"
Oct  2 08:35:05 ubuntu466 kernel: [ 1478.193384] audit(1222932905.440:13): type=1503 operation="inode_permission" requested_mask="rw::" denied_mask="rw::" name="/var/lib/samba/secrets.tdb" pid=4355 profile="/usr/sbin/cupsd" namespace="default"
Oct  2 08:35:05 ubuntu466 kernel: [ 1478.195496] audit(1222932905.450:14): type=1503 operation="inode_permission" requested_mask="rw::" denied_mask="rw::" name="/var/lib/samba/secrets.tdb" pid=4355 profile="/usr/sbin/cupsd" namespace="default"
Oct  2 08:35:05 ubuntu466 kernel: [ 1478.206823] audit(1222932905.460:15): type=1503 operation="inode_permission" requested_mask="Ux::" denied_mask="Ux::" name="/usr/share/samba/panic-action" pid=4397 profile="/usr/sbin/cupsd" namespace="default"

---

### Post by windependence on 2008-10-02
Looks like a bug:

[https://lists.ubuntu.com/archives/ubuntu-server-bugs/2008-May/002067.html](https://lists.ubuntu.com/archives/ubuntu-server-bugs/2008-May/002067.html)

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/217787](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/217787)

This was in May, and it looks like you may be able to fix it by upgrading your apparmor package. It's an authentication error and it only occurs in the web GUI so you also could just configure CUPS using the command line:

[http://ubuntuforums.org/showthread.php?t=240282](http://ubuntuforums.org/showthread.php?t=240282)

Hope this helps.

-Tim

---

