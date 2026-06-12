---
title: "Minimal server Install"
date: 2008-11-20
forum: Server Platforms
---

### Post by Diubidone on 2008-11-20
Hello,

While I was installing my ubuntu 8.10 server I noticed there is an option "minimal install".

I thought that the server install by itself was already minimal. What does this option does more than the regular Server Installation. I tried to google it but I didn't find any specs about it. Anyone care to give me some light on the issue?

Cheers!

---

### Post by cdenley on 2008-11-20
It's probably the difference between the ubuntu-standard and ubuntu-minimal meta-packages.

```

$ dpkg-query -W -f='\n${Package}\n${Depends}\n${Recommends}\n' ubuntu-minimal ubuntu-standard

ubuntu-minimal
adduser, apt, apt-utils, bzip2, console-setup, debconf, dhcp3-client, eject, gnupg, ifupdown, initramfs-tools, iproute, iputils-ping, kbd, less, locales, lsb-release, makedev, mawk, module-init-tools, net-tools, netbase, netcat, ntpdate, passwd, procps, python, startup-tasks, sudo, sysklogd, system-services, tasksel, tzdata, ubuntu-keyring, udev, upstart, upstart-compat-sysv, upstart-logd, vim-tiny, whiptail


ubuntu-standard
aptitude, at, cpio, cron, dmidecode, dnsutils, dosfstools, ed, file, ftp, hdparm, info, iptables, logrotate, lshw, lsof, ltrace, man-db, memtest86+, mime-support, nano, parted, pciutils, popularity-contest, psmisc, rsync, strace, time, usbutils, w3m, wget
apparmor-utils, bash-completion, command-not-found, friendly-recovery, iputils-arping, iputils-tracepath, manpages, mlocate, mtr-tiny, ntfs-3g, openssh-client, ppp, pppconfig, pppoeconf, reiserfsprogs, tcpdump, telnet, ufw, update-manager-core, uuid-runtime

```

---

### Post by snowpine on 2008-11-20
The minimal install is very popular with people who like to build minimal Ubuntu with a lightweight windows manager (openbox, icewm, etc) and a few applications of their choice, and who don't have server-related needs.

---

### Post by Diubidone on 2008-11-21
But how come it's an option on the server install cd if it's not thinked for servers services?

---

### Post by cdenley on 2008-11-21
> **Diubidone said:**
> But how come it's an option on the server install cd if it's not thinked for servers services?

not thinked?

The minimal install just excludes tools that aren't necessary, but could be useful. For example: nano, dnsutils, and wget.

---

### Post by hictio on 2008-11-21
> **Diubidone said:**
> But how come it's an option on the server install cd if it's not thinked for servers services?

Because it is good, and it offers options, not all servers service the same services :D
You might setup a gateway/ firewall, for instance, and in that case, you'll want to have the least amount of "things" (not only running, but also installed) on the box (the more you have packages installed, the more time it will to take to update and patch (specially on older hardware), and the more risks that a bug in one of those packages might compromise the whole box)

---

