---
title: "mdadm monitor test e-mails not working under 18.04"
date: 2020-01-19
forum: Ubuntu, Linux and OS Chat
---

### Post by TZiebura on 2020-01-19
@mods: sorry if this doesn't fit here. Move it or delete it if you like.

I could not find any solution for this on these forums or elsewhere so I would like to leave my workaround here for others who might struggle with the same issue.

I followed this tutorial to set up e-mail notifications for mdadm: [https://ubuntuforums.org/showthread.php?t=1185134](https://ubuntuforums.org/showthread.php?t=1185134)
This used to work in old Ubuntu versions but when I tried it with 18.04 I would not receive test mails on boot. DAEMON-OPTIONS in /etc/default/mdadm would just be ignored.

The reason seems to be that new Ubuntu versions rely on systemd which was not the case at the time when the tutorial was written.

The solution is is to copy **/lib/systemd/system/mdmonitor.service** to **/etc/systemd/system/** and edit it there.

You need to add your desired daemon options to the ExecStart line and also add "After=network-online.target" to the unit-section to make sure the system does not try to send your test mail before the network is up.

**/etc/systemd/system/mdmonitor.service** will look like this when you are done:

#  This file is part of mdadm.
#
#  mdadm is free software; you can redistribute it and/or modify it
#  under the terms of the GNU General Public License as published by
#  the Free Software Foundation; either version 2 of the License, or
#  (at your option) any later version.

[Unit]
Description=MD array monitor
DefaultDependencies=no
After=network-online.target

[Service]
ExecStart=/sbin/mdadm --monitor --scan --syslog --test

---

