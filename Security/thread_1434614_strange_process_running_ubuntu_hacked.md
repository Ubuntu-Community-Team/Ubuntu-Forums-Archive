---
title: "strange process running: ubuntu hacked?"
date: 2010-03-20
forum: Security
---

### Post by krantix on 2010-03-20
I have a strange "find" process running on my machine.

If I move my mouse over it looks something like


/usr/bin/find / -ignore_readdir_race ( -fstype NFS -o -fstype nfs .... -type d -regex \(^/tmp$\) ..... (^alex$\) ..... )) -prune -o -print0

See image attached.

There is no user "alex" on my system...

---

### Post by cariboo on 2010-03-20
What happens if you kill the process?

---

### Post by krantix on 2010-03-20
I just gave it a reboot and it wasn't there anymore... (I may have tried kill but maybe it didn't work).

---

### Post by DaithiF on 2010-03-20
its a cron job which updates the locatedb database.   for more info man locate  and man updatedb

---

### Post by krantix on 2010-03-20
> **DaithiF said:**
> its a cron job which updates the locatedb database.   for more info man locate  and man updatedb

thanks Daithi, so nothing to worry about? (it's just strange that "alex$" string is in there...)

---

### Post by FuturePilot on 2010-03-20
> **DaithiF said:**
> its a cron job which updates the locatedb database.   for more info man locate  and man updatedb

I see no such cron job on my system. :confused:

---

### Post by krantix on 2010-03-21
> **FuturePilot said:**
> I see no such cron job on my system. :confused:

futurepilot, the diagnosis is correct, the confusing cron job on Ubuntu 9.10 is located under:

/etc/cron.daily/locate

and these are actually its contents:

------------------------------------------

#! /bin/sh

set -e

# cron script to update the `locatedb' database.
#
# Written by Ian A. Murdock <imurdock@debian.org> and 
#            Kevin Dalley <kevin@aimnet.com>

# Please consult updatedb(1) and /usr/share/doc/locate/README.Debian

[ -e /usr/bin/updatedb.findutils ] || exit 0

if [ "$(id -u)" != "0" ]; then
	echo "You must be root."
	exit 1
fi
 
# Global options for invocations of find(1)
FINDOPTIONS='-ignore_readdir_race'
# filesystems which are pruned from updatedb database
PRUNEFS="NFS nfs nfs4 afs binfmt_misc proc smbfs autofs iso9660 ncpfs coda devpts ftpfs devfs mfs shfs sysfs cifs lustre_lite tmpfs usbfs udf ocfs2"
# paths which are pruned from updatedb database
PRUNEPATHS="/tmp /usr/tmp /var/tmp /afs /amd /alex /var/spool /sfs /media /var/lib/schroot/mount"
# netpaths which are added
NETPATHS=""
# run find as this user
LOCALUSER="nobody"
# cron.daily/find: run at this priority -- higher number means lower priority
# (this is relative to the default which cron sets, which is usually +5)
NICE=10

# I/O priority
# 1 for real time, 2 for best-effort, 3 for idle ("3" only allowed for root)
IONICE_CLASS=3
# 0-7 (only valid for IONICE_CLASS 1 and 2), 0=highest, 7=lowest 
IONICE_PRIORITY=7

# allow keeping local customizations in a separate file
if [ -r /etc/updatedb.findutils.cron.local ] ; then
	. /etc/updatedb.findutils.cron.local
fi
export FINDOPTIONS PRUNEFS PRUNEPATHS NETPATHS LOCALUSER

# Set the task to run with desired I/O priority if possible
# Linux supports io scheduling priorities and classes since
# 2.6.13 with the CFQ io scheduler
if [ -x /usr/bin/ionice ] && [ "${UPDATDB_NO_IONICE}" = "" ]; then
	# don't run ionice if kernel version < 2.6.13
	KVER=$(uname -r)
	case "$KVER" in
		2.[012345]*) ;;
		2.6.[0-9]) ;;
		2.6.[0-9].*) ;;
		2.6.1[012]*) ;;
		*)
		# Avoid providing "-n" when IONICE_CLASS isn't 1 or 2
		case "$IONICE_CLASS" in
			1|2) priority="-n ${IONICE_PRIORITY:-7}" ;;
			*) priority="" ;;
		esac
		ionice -c $IONICE_CLASS $priority -p $$ > /dev/null 2>&1 || true
		;;
	esac
fi

if getent passwd $LOCALUSER > /dev/null ; then
  cd / && nice -n ${NICE:-10} updatedb.findutils 2>/dev/null
else
  echo "User $LOCALUSER does not exist."
  exit 1
fi

---

### Post by 2hot6ft2 on 2010-03-21
Could this be alex?
> Alex is a tool for generating lexical analysers in Haskell, given a
description of the tokens to be recognised in the form of regular
expressions. It is similar to the tool lex or flex for C/C++.
From Synaptic

---

### Post by FuturePilot on 2010-03-21
> **krantix said:**
> futurepilot, the diagnosis is correct, the confusing cron job on Ubuntu 9.10 is located under:

/etc/cron.daily/locate

and these are actually its contents:

------------------------------------------

#! /bin/sh

set -e

# cron script to update the `locatedb' database.
#
# Written by Ian A. Murdock <imurdock@debian.org> and 
#            Kevin Dalley <kevin@aimnet.com>

# Please consult updatedb(1) and /usr/share/doc/locate/README.Debian

[ -e /usr/bin/updatedb.findutils ] || exit 0

if [ "$(id -u)" != "0" ]; then
	echo "You must be root."
	exit 1
fi
 
# Global options for invocations of find(1)
FINDOPTIONS='-ignore_readdir_race'
# filesystems which are pruned from updatedb database
PRUNEFS="NFS nfs nfs4 afs binfmt_misc proc smbfs autofs iso9660 ncpfs coda devpts ftpfs devfs mfs shfs sysfs cifs lustre_lite tmpfs usbfs udf ocfs2"
# paths which are pruned from updatedb database
PRUNEPATHS="/tmp /usr/tmp /var/tmp /afs /amd /alex /var/spool /sfs /media /var/lib/schroot/mount"
# netpaths which are added
NETPATHS=""
# run find as this user
LOCALUSER="nobody"
# cron.daily/find: run at this priority -- higher number means lower priority
# (this is relative to the default which cron sets, which is usually +5)
NICE=10

# I/O priority
# 1 for real time, 2 for best-effort, 3 for idle ("3" only allowed for root)
IONICE_CLASS=3
# 0-7 (only valid for IONICE_CLASS 1 and 2), 0=highest, 7=lowest 
IONICE_PRIORITY=7

# allow keeping local customizations in a separate file
if [ -r /etc/updatedb.findutils.cron.local ] ; then
	. /etc/updatedb.findutils.cron.local
fi
export FINDOPTIONS PRUNEFS PRUNEPATHS NETPATHS LOCALUSER

# Set the task to run with desired I/O priority if possible
# Linux supports io scheduling priorities and classes since
# 2.6.13 with the CFQ io scheduler
if [ -x /usr/bin/ionice ] && [ "${UPDATDB_NO_IONICE}" = "" ]; then
	# don't run ionice if kernel version < 2.6.13
	KVER=$(uname -r)
	case "$KVER" in
		2.[012345]*) ;;
		2.6.[0-9]) ;;
		2.6.[0-9].*) ;;
		2.6.1[012]*) ;;
		*)
		# Avoid providing "-n" when IONICE_CLASS isn't 1 or 2
		case "$IONICE_CLASS" in
			1|2) priority="-n ${IONICE_PRIORITY:-7}" ;;
			*) priority="" ;;
		esac
		ionice -c $IONICE_CLASS $priority -p $$ > /dev/null 2>&1 || true
		;;
	esac
fi

if getent passwd $LOCALUSER > /dev/null ; then
  cd / && nice -n ${NICE:-10} updatedb.findutils 2>/dev/null
else
  echo "User $LOCALUSER does not exist."
  exit 1
fi

Odd. That does not exist on my system.
Edit: apparently it belongs to the "locate" package which is not installed.

---

