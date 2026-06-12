---
title: "avahi-daemon fails after upgrade from 18.04 to 20.04"
date: 2021-05-28
forum: Server Platforms
---

### Post by mikelhayes on 2021-05-28
temporary name server failure. i manually entered a nameserver in resolv.conf but we know that will revert. I have looked here and else where to figure this out.

[LIST]
[*]systemd-networkd-wait-online.service wont start either.
[/LIST]
? avahi-daemon.service - Avahi mDNS/DNS-SD Stack
     Loaded: loaded (/lib/systemd/system/avahi-daemon.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Fri 2021-05-28 14:42:47 PDT; 33min ago
TriggeredBy: ? avahi-daemon.socket
   Main PID: 11343 (code=exited, status=255/EXCEPTION)
     Status: "avahi-daemon 0.7 starting up."


May 28 14:42:47 server avahi-daemon[11343]: Successfully dropped root privileges.
May 28 14:42:47 server avahi-daemon[11343]: avahi-daemon 0.7 starting up.
May 28 14:42:47 server systemd[1]: Started Avahi mDNS/DNS-SD Stack.
May 28 14:42:47 server avahi-daemon[11343]: Successfully called chroot().
May 28 14:42:47 server avahi-daemon[11343]: Successfully dropped remaining capabilities.
May 28 14:42:47 server avahi-daemon[11343]: No service file found in /etc/avahi/services.
May 28 14:42:47 server avahi-daemon[11343]: Failed to create server: Invalid domain name
May 28 14:42:47 server avahi-daemon[11343]: avahi-daemon 0.7 exiting.
May 28 14:42:47 server systemd[1]: avahi-daemon.service: Main process exited, code=exited, status=255/EXCEPTION
May 28 14:42:47 server systemd[1]: avahi-daemon.service: Failed with result 'exit-code'.

---

### Post by TheFu on 2021-05-28
You don't need systemd-resolved or resolvconf if you don't want them.  Then you can manually edit the /etc/resolv.conf file to your liking and not worry it will be touched.  Just be certain to remove the symlink where it points **before** doing the modification.  

I would stop both systemd-resolved and resolvconf, then mask both services.  Then setup a new resolv.conf-new file with the settings I want. We need to remove the symlink and cp/mv the new file quickly, since sudo can ask to validate a hostname to allow a userid sudo privileges.

As for the avahi stuff, I don't know. I always purge that from my systems. It has a history of causing me problems and it just isn't needed on a well-run network.  But if you like to have IoT stuff and want them to "find" each other like magic, then avahi is the way.

---

