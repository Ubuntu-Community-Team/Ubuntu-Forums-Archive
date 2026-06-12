---
title: "Shorewall Ubuntu 14.04.5"
date: 2017-01-06
forum: Server Platforms
---

### Post by slkamath on 2017-01-06
Hi All,

We are using Ubuntu 14.04.5 Server and using Shorewall version 4.5.21.6

When ever server restarts initially shorewall was not starting automatically. I have to goto webmin - bootup & shutdown there i have to restart shorewall then only shorewall getting start.

Today morning onwards Shorewall is starting while bootup but it will work only when if i restart the service in bootup & shutdown.

I am not understanding where i did wrong. Can anyone please help me to solve my issue?

Thanks in advance.

Lokesh kamath

---

### Post by darkod on 2017-01-06
webmin is not supported and not recommended. Some problems can be a result of using webmin and how it changes files.

Have you tried without webmin? Just use simple ssh session.

How did you install shorewall, using apt-get or another method? Using apt-get usually configured start up services where necessary and you don't need to take further actions.

---

### Post by slkamath on 2017-01-06
Thanks for your response Darkod.

while installing the shorewall i used the apt-get through ssh. This issue happens only if i restart the server. Also if i check the service status it shows running. but internet will not work until i restart the service of shorewall.

Lokesh Kamath

---

### Post by slkamath on 2017-01-12
Anyone can help to solve this issue?

---

### Post by darkod on 2017-01-12
Have you tried reinstalling shorewall? Any messages in the logs when the service doesn't start on reboot?

---

### Post by slkamath on 2017-02-05
Sorry for delayed response.

Log info.

```
**> cat /var/log/boot.log**
 * Starting Read required files in advance[122G[ OK ]
 * Stopping Send an event to indicate plymouth is up[122G[ OK ]
 * Starting Mount filesystems on boot[122G[ OK ]
 * Starting Fix-up sensitive /proc filesystem entries[122G[ OK ]
 * Starting Populate /dev filesystem[122G[ OK ]
 * Starting Populate and link to /run filesystem[122G[ OK ]
 * Stopping Fix-up sensitive /proc filesystem entries[122G[ OK ]
 * Stopping Populate /dev filesystem[122G[ OK ]
 * Stopping Populate and link to /run filesystem[122G[ OK ]
 * Stopping Track if upstart is running in a container[122G[ OK ]
 * Starting Initialize or finalize resolvconf[122G[ OK ]
 * Starting Signal sysvinit that virtual filesystems are mounted[122G[ OK ]
 * Starting Signal sysvinit that virtual filesystems are mounted[122G[ OK ]
 * Starting Bridge udev events into upstart[122G[ OK ]
 * Starting Signal sysvinit that remote filesystems are mounted[122G[ OK ]
 * Starting Signal sysvinit that the rootfs is mounted[122G[ OK ]
 * Starting device node and kernel event manager[122G[ OK ]
 * Starting load modules from /etc/modules[122G[ OK ]
 * Starting cold plug devices[122G[ OK ]
 * Starting log initial device creation[122G[ OK ]
 * Starting Clean /tmp directory[122G[ OK ]
 * Stopping Read required files in advance (for other mountpoints)[122G[ OK ]
 * Stopping load modules from /etc/modules[122G[ OK ]
 * Starting configure network device security[122G[ OK ]
 * Starting configure network device security[122G[ OK ]
 * Starting configure network device security[122G[ OK ]
 * Stopping Clean /tmp directory[122G[ OK ]
 * Starting Signal sysvinit that local filesystems are mounted[122G[ OK ]
 * Starting flush early job output to logs[122G[ OK ]
 * Stopping Mount filesystems on boot[122G[ OK ]
 * Stopping flush early job output to logs[122G[ OK ]
 * Starting D-Bus system message bus[122G[ OK ]
 * Starting Mount network filesystems[122G[ OK ]
 * Starting SMB/CIFS File Server[122G[ OK ]
 * Starting Failsafe Boot Delay[122G[ OK ]
 * Stopping Mount network filesystems[122G[ OK ]
 * Starting Bridge file events into upstart[122G[ OK ]
 * Starting Bridge socket events into upstart[122G[ OK ]
 * Starting configure network device[122G[ OK ]
 * Starting SystemD login management service[122G[ OK ]
 * Starting system logging daemon[122G[ OK ]
 * Starting configure network device[122G[ OK ]
 * Starting Mount network filesystems[122G[ OK ]
 * Starting Samba Winbind[122G[ OK ]
 * Stopping Mount network filesystems[122G[ OK ]
 * Starting configure network device[122G[ OK ]
 * Starting SMB/CIFS File and Active Directory Server[122G[ OK ]
 * Starting NetBIOS name server[122G[ OK ]
 * Starting SMB/CIFS File and Active Directory Server[122G[[31mfail[39;49m]
 * Stopping cold plug devices[122G[ OK ]
 * Stopping log initial device creation[122G[ OK ]
 * Starting load fallback graphics devices[122G[ OK ]
 * Starting configure network device security[122G[ OK ]
 * Stopping load fallback graphics devices[122G[ OK ]
 * Starting set console font[122G[ OK ]
 * Stopping set console font[122G[ OK ]
 * Starting userspace bootsplash[122G[ OK ]
 * Starting Send an event to indicate plymouth is up[122G[ OK ]
 * Stopping Send an event to indicate plymouth is up[122G[ OK ]
 * Starting configure virtual network devices[122G[ OK ]
 * Stopping userspace bootsplash[122G[ OK ]
 * Stopping Failsafe Boot Delay[122G[ OK ]
 * Starting System V initialisation compatibility[122G[ OK ]
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
Skipping profile in /etc/apparmor.d/disable: usr.sbin.squid3
 * Starting AppArmor profiles       [128G 
[122G[ OK ]
Starting "Shorewall firewall": done.
 * Stopping System V initialisation compatibility[122G[ OK ]
 * Starting System V runlevel compatibility[122G[ OK ]
 * Starting deferred execution scheduler[122G[ OK ]
 * Starting regular background program processing daemon[122G[ OK ]
 * Starting automatic crash report generation[122G[ OK ]
 * Starting ACPI daemon[122G[ OK ]
 * Starting HTTP proxy-cache[122G[ OK ]
To enable c-icap, edit /etc/default/c-icap and set START=yes
 * Starting OpenSSH server[122G[ OK ]
 * Starting CPU interrupts balancing daemon[122G[ OK ]
 * Starting MySQL Server[122G[ OK ]
 * Starting ClamAV daemon clamd       [128G 
[122G[ OK ]
 * Starting ClamAV virus database updater freshclam       [128G 
[122G[ OK ]
 * Starting DansGuardian dansguardian       [128G 
[122G[ OK ]
 * Starting ftp server proftpd       [128G 
[122G[ OK ]
 * Restoring resolver state...       [128G 
[122G[ OK ]
 * 
   Shorewall is already running
Starting "Shorewall firewall": done.
 * Stopping System V runlevel compatibility[122G[ OK ]
```

---

