---
title: "mount.cifs with kinit - grant access to samba share for local account"
date: 2016-07-09
forum: Security
---

### Post by peridian on 2016-07-09
Hi,


How can I mount a Kerberised Samba share in such a manner that a local-only account can still navigate it, without compromising the permissions/(non-)guest access of the share?


I have a Kerberos5/OpenLDAP setup for centralised authentication. All my devices at home are able to use this via PAM (i.e. getent passwd/group works) for logins (either local or via SSH).


I have a Samba server sharing file shares also using this krb/ldap setup (i.e. permissions/owners are recognised on both server and client), which works fine when I mount folders like so:


```

kinit -k -t ~/.keytab myuser@DOMAIN
mount -t cifs -o sec=krb5 //samba.domain/share /mnt/share

```


I now have two dedicated servers (a.k.a Raspberry Pies) that need to mount these shares for local service purposes.



[LIST=1]
[*]Git repository, using the Samba share as the storage location, where access to the Git repo is also tied to the same krb5/ldap user base.
[*]Document store, using the Samba share as the storage location, for a service that does not integrate with Kerberos and runs only as a local root account.
[/LIST]


The first option may just be me not finding enough information on how to configure Git properly, but the second one is a bit of a pain. I went down the road of: can the local system perform a kinit using a supplied keytab where the issued ticket would apply across the whole system?


I thought the answers may lie in some of the options for the mount command, in particular:



[LIST]
[*]user - specifies the user to connect as, great! But the only two options to give a password are plain text and do not accept keytab files, which I would prefer.
[*]uid - most search results use this, but as far as I can tell this is like the server-side 'force user' option, but specified from the client; you still need to authenticate normally to begin with.
[*]cruid - reads as being exactly what I want, but I cannot find any examples of how I initialise the credentials cache for the user specified on the local machine upon system startup.
[/LIST]


Any pointers would be greatly appreciated.


Regards,
Rob.

---

### Post by peridian on 2016-07-11
Okay, got this all working in the end.  The answer was the cruid option with k5start.

Credits to Arthur de Jong who wrote the nslcd scripts that mine were lifted from.

> Caveat: I have only tested this with my Ubuntu/Debian systems, I do not know if this will work for anybody else.

Navigate to /etc/init.d
Create a new file called k5start-rjs
Paste into it the following:

```

#! /bin/sh


# /etc/init.d/k5start-rjs script for starting and stopping k5start
# Copyright (C) 2016 Rob Straughan
#
# Original script: /etc/init.d/nslcd
# Copyright (C) 2006 West Consulting
# Copyright (C) 2006, 2008, 2009, 2010, 2011, 2012, 2013 Arthur de Jong
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
#
# This library is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# Lesser General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public
# License along with this library; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA
# 02110-1301 USA


### BEGIN INIT INFO
# Provides:          k5start-rjs
# Required-Start:    $remote_fs $syslog $time
# Required-Stop:     $remote_fs $syslog
# Should-Start:      $named $network krb5-kdc heimdal-kdc heimdal-kcm shishi-kdc nscd nslcd
# Should-Stop:       $network
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: k5start daemon
# Description:       k5start can be used as a daemon to perform
#                    kinit and krenew commands to keep a set of credentials
#                    active on a system.  This script wraps the
#                    necessary commands to allow k5start to be managed
#                    through the service commands for /etc/init.d scripts.
### END INIT INFO


PATH=/bin:/usr/bin:/sbin:/usr/sbin


. /lib/lsb/init-functions


# default options for k5start
K5START_BIN=/usr/bin/k5start
K5START_DESTROY=/usr/bin/kdestroy
K5START_STATEDIR=/var/run/k5start
K5START_DESC="k5start from k5start.credentials"
K5START_PIDFILE=$K5START_STATEDIR/k5start.pid
K5START_MODE=600
K5START_CCREFRESH=60
K5START_CCLIST=/etc/k5start.credentials


[ -x "$K5START_BIN" ] || exit 0
[ -x "$K5START_DESTROY" ] || exit 0
[ -r "$K5START_CCLIST" ] || exit 0


k5start_start()
{
  while read -r keytab user; do
      log_daemon_msg "Starting $K5START_DESC keytab:$keytab (for user $user)" "k5start"
      start-stop-daemon --start \
                        --pidfile $K5START_PIDFILE \
                        --exec $K5START_BIN -- \
                        -b -p $K5START_PIDFILE \
                        -o $user \
                        -m $K5START_MODE \
                        -f $keytab \
                        -K $K5START_CCREFRESH \
                        -U
      log_end_msg $?
  done < $K5START_CCLIST
}


k5start_stop()
{
    log_daemon_msg "Stopping $K5START_DESC" "k5start"
    start-stop-daemon --stop --oknodo --pidfile $K5START_PIDFILE
    log_end_msg $?
    # remove any left behind files
    [ -n "$K5START_PIDFILE" ] && rm -f $K5START_PIDFILE
    $K5START_DESTROY
}


k5start_status()
{
    status_of_proc -p "$K5START_PIDFILE" "$K5START_BIN" "k5start"
}


case "$1" in
start)
  k5start_start
  ;;
stop)
  k5start_stop
  ;;
restart|force-reload)
  k5start_stop
  k5start_start
  ;;
status)
  k5start_status
  ;;
*)
  log_success_msg "Usage: $0 {start|stop|restart|force-reload|status}"
  exit 1
  ;;
esac



```

> Note: Although this was written with the idea of multiple credentials keytabs, I typically only use one on any given system so I haven't tested with multiple; I suspect this will fail due to the need to manage multiple PID files, which this doesn't do

> Note: autofs may solve this next part better if you can figure it out; skip the reboot-mnt file, and related commands, if you use autofs

Also create a new file called reboot-mnt
Paste into it the following:

```

#! /bin/sh


# /etc/init.d/reboot-mnt script for performing mounting/unmounting on reboot
# Copyright (C) 2016 Rob Straughan
#
# Original script: /etc/init.d/nslcd
# Copyright (C) 2006 West Consulting
# Copyright (C) 2006, 2008, 2009, 2010, 2011, 2012, 2013 Arthur de Jong
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
#
# This library is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# Lesser General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public
# License along with this library; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA
# 02110-1301 USA


### BEGIN INIT INFO
# Provides:          reboot-mnt
# Required-Start:    $remote_fs $syslog $time
# Required-Stop:     $remote_fs $syslog
# Should-Start:      $network k5start-rjs
# Should-Stop:       $network k5start-rjs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: mount reboot service
# Description:       Extension of the k5start-rjs script to perform
#                    a delayed mount of a share.  This is because
#                    fstab entries are mounted before init.d scripts
#                    are fired, rendering the ability to specify the cruid
#                    option in fstab infeasible due to the lack of the 
#                    nscd/nslcd services to retrieve the krb5/ldap usernames.
### END INIT INFO


PATH=/bin:/usr/bin:/sbin:/usr/sbin


. /lib/lsb/init-functions


MOUNT_BIN=/bin/mount
MOUNT_DESC="mount from fstab.delayed"
MOUNT_FSTAB=/etc/fstab.delayed
UMOUNT_BIN=/bin/umount


[ -x "$MOUNT_BIN" ] || exit 0
[ -x "$UMOUNT_BIN" ] || exit 0
[ -r "$MOUNT_FSTAB" ] || exit 0


mount_start()
{
  while read -r fssource fsmount fstype fsoptions; do
      log_daemon_msg "Starting $MOUNT_DESC : -t $fstype -o $fsoptions $fssource $fsmount" "mount"
      $MOUNT_BIN -t $fstype -o $fsoptions $fssource $fsmount
      log_end_msg $?
  done < $MOUNT_FSTAB
}


mount_stop()
{
  while read -r fssource fsmount fstype fsoptions; do
    log_daemon_msg "Stopping $MOUNT_DESC $fssource -> $fsmount" "k5start"
    $UMOUNT_BIN $fsmount
    log_end_msg $?
  done < $MOUNT_FSTAB
}


case "$1" in
start)
  mount_start
  ;;
stop)
  mount_stop
  ;;
restart|force-reload)
  mount_stop
  mount_start
  ;;
*)
  log_success_msg "Usage: $0 {start|stop|restart|force-reload}"
  exit 1
  ;;
esac



```

Execute the following commands:

> 
sudo chmod 755 /etc/init.d/k5start-rjs
sudo chmod 755 /etc/init.d/reboot-mnt
sudo chown root:root /etc/init.d/k5start-rjs
sudo chown root:root /etc/init.d/reboot-mnt


Navigate to /etc
Create a file called k5start.credentials
Populate it with the form of: [keytab location] [username for the cruid option]

E.g.

> /etc/krb_principal_for_cifs_auth.keytab   pam_username_for_cifs_access

> Note: the script uses the -U option which means it will use the first principal in the keytab file only, otherwise you'd have to specify the principal per keytab

> Note: remember to lock your keytabs down (i.e. chmod 400)

Also (if using reboot-mnt) create a file called fstab.delayed
Populate it with your equivalent line from fstab, minus the two numbers on the end: [source] [mount point] [fs type] [mount options]

E.g.

> 
//samba.domain/share   /mnt/share   cifs   sec=krb5,cruid=pam_username_for_cifs_access
//samba.domain/share   /mnt/share   cifs   ro,sec=krb5,cruid=pam_username_for_cifs_access,uid=local_account_username


> Note: the first option works if the system is running services running as the root user; the second option is what I use to give a local account (other than root) access, however note that I do also use the read-only (ro) option in this case, just to be sure that the local account cannot make changes to the target (this was just something specific to my use-case)

Execute the following commands:

> 
sudo chmod 644 /etc/fstab.delayed
sudo chmod 644 /etc/k5start.credentials
sudo chown root:root /etc/fstab.delayed
sudo chown root:root /etc/k5start.credentials


> Note: neither of these files contains sensitive information; you could 600 them, but I do not see the need

Install the services

E.g.

> 
sudo update-rc.d -f k5start-rjs defaults
sudo update-rc.d -f k5start-rjs enable
sudo update-rc.d -f reboot-mnt defaults
sudo update-rc.d -f reboot-mnt enable


> Note: these commands may differ on alternative distros

Reboot

> Note: these scripts may not be the most compatible in the world, and may not play nice if stopped and started while running, but they are good enough to take effect on startup/shutdown

Done.  The system should now correctly start up k5start with a targeted keytab file for a given recognised user account, and then follow up by performing mount.cifs using the established credentials file from the k5start process, the latter of which will keep the ticket valid while the system is running.  Because the scripts run as services, the access permissions belong to the root account, but anybody who can perform a sudo command should be able to interact with the mount as though they were the user in the keytab/credentials.

Hope this is helpful.

Regards,
Rob.

---

