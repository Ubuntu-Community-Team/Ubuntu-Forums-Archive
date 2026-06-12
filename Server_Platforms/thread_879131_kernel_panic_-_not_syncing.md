---
title: "kernel panic - not syncing ?"
date: 2008-08-03
forum: Server Platforms
---

### Post by samkon on 2008-08-03
hi,

I got this panic error today, and I am on a Live CD now..

I have fotmatted my hda5 partition manually and replace the uuid in fstab yesterday. Also I had an backup of fstab named "fstab.backup"..

When I got this error today I got in Live CD to replace old one.

But there was no fstab or fstab.backup file!

There is "fstab~" file but it is empty.

I tried to write fstab manually. But it didn't work. All /etc directory is empty in file manager. In console output of "ls -al" is here:

```
etc # ls -al
/bin/ls: terminfo: No such file or directory
/bin/ls: fdmount.conf: No such file or directory
/bin/ls: tidy: No such file or directory
/bin/ls: brltty: No such file or directory
/bin/ls: grub.d: No such file or directory
/bin/ls: logrotate.conf: No such file or directory
/bin/ls: environment: No such file or directory
/bin/ls: ODBCDataSources: No such file or directory
/bin/ls: resolv.conf]: No such file or directory
/bin/ls: power: No such file or directory
/bin/ls: belocs: No such file or directory
/bin/ls: gai.conf: No such file or directory
/bin/ls: mtab: No such file or directory
/bin/ls: hdparm.conf: No such file or directory
/bin/ls: bogofilter.cf: No such file or directory
/bin/ls: .java: No such file or directory
/bin/ls: fstab~: No such file or directory
/bin/ls: bluetooth: No such file or directory
/bin/ls: python2.4: No such file or directory
/bin/ls: hotplug: No such file or directory
/bin/ls: login.defs: No such file or directory
/bin/ls: dm: No such file or directory
/bin/ls: zsh_command_not_found: No such file or directory
/bin/ls: apparmor: No such file or directory
/bin/ls: shadow: No such file or directory
/bin/ls: sane.d: No such file or directory
/bin/ls: crypttab: No such file or directory
/bin/ls: motd: No such file or directory
/bin/ls: libgda-3.0: No such file or directory
/bin/ls: apm: No such file or directory
/bin/ls: rc4.d: No such file or directory
/bin/ls: scim: No such file or directory
/bin/ls: iftab: No such file or directory
/bin/ls: groff: No such file or directory
/bin/ls: e2fsck.conf: No such file or directory
/bin/ls: rc3.d: No such file or directory
/bin/ls: qt3: No such file or directory
/bin/ls: services: No such file or directory
/bin/ls: logcheck: No such file or directory
/bin/ls: bash.bashrc: No such file or directory
/bin/ls: network: No such file or directory
/bin/ls: papersize: No such file or directory
/bin/ls: tidy.conf: No such file or directory
/bin/ls: locale.alias: No such file or directory
/bin/ls: pulse: No such file or directory
/bin/ls: wgetrc: No such file or directory
/bin/ls: brlapi.key: No such file or directory
/bin/ls: gtk: No such file or directory
/bin/ls: bash_command_not_found: No such file or directory
/bin/ls: NetworkManager: No such file or directory
/bin/ls: cron.d: No such file or directory
/bin/ls: issue.net: No such file or directory
/bin/ls: fstab.backup: No such file or directory
/bin/ls: ffserver.conf: No such file or directory
/bin/ls: ucf.conf: No such file or directory
/bin/ls: debconf.conf: No such file or directory
/bin/ls: calendar: No such file or directory
/bin/ls: ca-certificates.conf.dpkg-old: No such file or directory
/bin/ls: apparmor.d: No such file or directory
/bin/ls: rcS.d: No such file or directory
/bin/ls: gnome-app-install: No such file or directory
/bin/ls: lastfmsubmitd.conf: No such file or directory
/bin/ls: crontab: No such file or directory
/bin/ls: bash_completion.d: No such file or directory
/bin/ls: resolvconf: No such file or directory
/bin/ls: usplash.conf: No such file or directory
/bin/ls: gconf: No such file or directory
/bin/ls: bindresvport.blacklist: No such file or directory
/bin/ls: python2.5: No such file or directory
/bin/ls: xinetd.d: No such file or directory
/bin/ls: libgda: No such file or directory
/bin/ls: cups: No such file or directory
/bin/ls: keys: No such file or directory
/bin/ls: xml: No such file or directory
/bin/ls: mailcap.order: No such file or directory
/bin/ls: console-tools: No such file or directory
/bin/ls: jvm: No such file or directory
/bin/ls: hostname: No such file or directory
/bin/ls: ldap: No such file or directory
/bin/ls: hp: No such file or directory
/bin/ls: iproute2: No such file or directory
/bin/ls: doc-base: No such file or directory
/bin/ls: ppp: No such file or directory
/bin/ls: updatedb.conf: No such file or directory
/bin/ls: ufw: No such file or directory
/bin/ls: libpaper.d: No such file or directory
/bin/ls: localtime: No such file or directory
/bin/ls: chatscripts: No such file or directory
/bin/ls: GeoIP.conf.default: No such file or directory
/bin/ls: inetd.conf: No such file or directory
/bin/ls: pcmcia: No such file or directory
/bin/ls: wvdial.conf: No such file or directory
/bin/ls: networks: No such file or directory
/bin/ls: python: No such file or directory
/bin/ls: magic.mime: No such file or directory
/bin/ls: discover.d: No such file or directory
/bin/ls: udev: No such file or directory
/bin/ls: ssl: No such file or directory
/bin/ls: phpmyadmin: No such file or directory
/bin/ls: dpkg: No such file or directory
/bin/ls: profile: No such file or directory
/bin/ls: esound: No such file or directory
/bin/ls: php5: No such file or directory
/bin/ls: motd.tail.old: No such file or directory
/bin/ls: rc6.d: No such file or directory
/bin/ls: gshadow: No such file or directory
/bin/ls: dhcp3: No such file or directory
/bin/ls: nanorc: No such file or directory
/bin/ls: hwtest.d: No such file or directory
/bin/ls: vnc.conf: No such file or directory
/bin/ls: vim: No such file or directory
/bin/ls: anacrontab: No such file or directory
/bin/ls: manpath.config: No such file or directory
/bin/ls: apt: No such file or directory
/bin/ls: foomatic: No such file or directory
/bin/ls: rc0.d: No such file or directory
/bin/ls: screenrc: No such file or directory
/bin/ls: subversion: No such file or directory
/bin/ls: gshadow-: No such file or directory
/bin/ls: rpc: No such file or directory
/bin/ls: openoffice: No such file or directory
/bin/ls: idmapd.conf: No such file or directory
/bin/ls: dictionaries-common: No such file or directory
/bin/ls: deluser.conf: No such file or directory
/bin/ls: bash_completion: No such file or directory
/bin/ls: sound: No such file or directory
/bin/ls: lftp.conf: No such file or directory
/bin/ls: cron.hourly: No such file or directory
/bin/ls: hosts: No such file or directory
/bin/ls: ld.so.conf.d: No such file or directory
/bin/ls: aliases: No such file or directory
/bin/ls: discover.conf-2.6: No such file or directory
/bin/ls: scrollkeeper.conf: No such file or directory
/bin/ls: update-manager: No such file or directory
/bin/ls: thunderbird: No such file or directory
/bin/ls: wodim.conf: No such file or directory
/bin/ls: pm: No such file or directory
/bin/ls: xdg: No such file or directory
/bin/ls: laptop-mode: No such file or directory
/bin/ls: resolv.conf.backup: No such file or directory
/bin/ls: purple: No such file or directory
/bin/ls: pam.d: No such file or directory
/bin/ls: hosts.deny: No such file or directory
/bin/ls: : No such file or directory
total 20
drwxr-xr-x 151 root root 12288 Aug  3 21:03 ./
drwxr-xr-x  21 root root  4096 Aug  3 19:50 ../
-rwxr-xr-x   1 root root   413 Aug  3 21:03 fstab*

```

last one is which I create manually. I've lots of things on my system as svn repositories, virtualbox o. systems ext...

I can backup the svn repositories by installing a new system to other partition I think, but I want to solve this problem without any damage. What can I do?

PS: On kernel booting ubuntu logo comes and in a little time stops moving. When I go to recovery mode, I got kernel panic attack...

---

