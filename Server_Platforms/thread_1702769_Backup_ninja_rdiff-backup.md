---
title: "Backup ninja rdiff-backup"
date: 2011-03-08
forum: Server Platforms
---

### Post by tabasko on 2011-03-08
Howdy,

I have problem with Backup Ninja version 0.9.3-5. It already does nicely mysqldump every night from our server, but there is something odd with rdiff-backup. We have 4 servers, one Ubuntu LTS and two Opensolaris 2009.6 based and one with Debian sarge. One Opensolaris server acts as backup storage here.

Im using ninjahelper for configuring; choosing rdiff backup -> choosing source and destination, all good. Then ninjahelper connects to opensolaris server, generates ssh keys and checks that remote folder exists and our backup-user has access to it, nice. Everything go smootlhy until it checks rdiff-backup compatibly to remote server. It gives this:

[IMG]http://tabasko.kapsi.fi/kuvat/incompatible.png[/IMG]

First I tried to change different rdiff-backup versions from opensolaris repos, and in the end installed one from source. Both rdiff-backup at ubuntu server and opensolaris server are version 1.2.8
Even running ```
rdiff-backup --test-server hostname.net::/ignored
``` gives me OK. Also running rdiff-backups by hand works well.

Im pretty confused, I know our situation is bit exotic but why everything must be perfectly same version everywhere? Rsync is 3.0.6 on solaris, ubuntu 3.07 should I start messing with that too? :confused: We use solaris on storage servers because handy ZFS, Ubuntu runs our Intra, zabbix and other goods.

Backup ninja is really neat program, it could be handy for central controlling different backup actions like ldap, msql and rdiff-backups. Just if I could figure this problem first.
I have also checked out Bacula, but it looks like bit too overkill for our little system.

Thank you in advance :KS

---

