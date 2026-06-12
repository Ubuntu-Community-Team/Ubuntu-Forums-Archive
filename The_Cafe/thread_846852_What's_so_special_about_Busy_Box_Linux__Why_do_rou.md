---
title: "What's so special about Busy Box Linux?  Why do routers often use this OS?"
date: 2008-07-01
forum: The Cafe
---

### Post by kevdog on 2008-07-01
Just trying to figure out why a lot of smaller appliances running linux run the Busy Box OS variant -- many routers for example use this as their OS.  Are there other competitors?  I never see Busy Box listed on Distro Watch.

---

### Post by LaRoza on 2008-07-01
> **kevdog said:**
> Just trying to figure out why a lot of smaller appliances running linux run the Busy Box OS variant -- many routers for example use this as their OS.  Are there other competitors?  I never see Busy Box listed on Distro Watch.

It is basically just a set of tools, like the GNU Core Utilities, but smaller.

---

### Post by Lostincyberspace on 2008-07-01
Busy box is in everything Linux (even Ubuntu trust me I am having problems with it right now.) I believe it is part of the kernel.

---

### Post by kevdog on 2008-07-01
Is there a specific busy box distro -- or somewhere I could simply download this set of tools?  What is it?  a stripped down kernel?

---

### Post by LaRoza on 2008-07-01
> **kevdog said:**
> Is there a specific busy box distro -- or somewhere I could simply download this set of tools?  What is it?  a stripped down kernel?

[http://busybox.net/FAQ.html](http://busybox.net/FAQ.html)

---

### Post by macogw on 2008-07-02
Busy box is just a shell that runs on top of the kernel, like korn, bash, sh, tcsh, zsh, etc. except extremely basic.

---

### Post by p_quarles on 2008-07-02
It's built into most distros. The help message on my box:
```
BusyBox v1.9.2 (Debian 1:1.9.2-3) multi-call binary
Copyright (C) 1998-2007 Erik Andersen, Rob Landley, Denys Vlasenko
and others. Licensed under GPLv2.
See source distribution for full notice.

Usage: busybox [function] [arguments]...
   or: function [arguments]...

	BusyBox is a multi-call binary that combines many common Unix
	utilities into a single executable.  Most people will create a
	link to busybox for each function they wish to use and BusyBox
	will act like whatever it was invoked as!

Currently defined functions:
	[, [[, adjtimex, arping, ash, awk, basename, bunzip2, bzcat, bzip2, cal, cat, chgrp,
	chmod, chown, chroot, chvt, clear, cmp, cp, cpio, cut, date, dc, dd, deallocvt, df, dirname,
	dmesg, dos2unix, du, dumpkmap, echo, egrep, env, expr, false, fgrep, find, fold, free,
	ftpget, ftpput, getopt, grep, gunzip, gzip, head, hexdump, hostid, hostname, httpd, id,
	ifconfig, ip, ipcalc, kill, killall, klogd, last, length, ln, loadfont, loadkmap, logger,
	logname, logread, losetup, ls, lzmacat, md5sum, mkdir, mkfifo, mknod, mktemp, more, mount,
	mt, mv, nameif, nc, netstat, nslookup, od, openvt, patch, pidof, ping, ping6, printf,
	ps, pwd, rdate, readlink, realpath, renice, reset, rm, rmdir, route, rpm, rpm2cpio, run-parts,
	sed, setkeycodes, sh, sha1sum, sleep, sort, start-stop-daemon, strings, stty, swapoff,
	swapon, sync, sysctl, syslogd, tail, tar, tee, telnet, test, tftp, time, top, touch,
	tr, traceroute, true, tty, umount, uname, uncompress, uniq, unix2dos, unlzma, unzip,
	uptime, usleep, uudecode, uuencode, vi, watch, watchdog, wc, wget, which, who, whoami,
	xargs, yes, zcat
```

---

