---
title: "Ftp mount after OpenVPN connection"
date: 2015-06-29
forum: Ubuntu/Debian BASED
---

### Post by mat25 on 2015-06-29
Hey I want to fix that my ftp mounts only after my OpenVPN connection is established.
I found this script for ubuntu: [http://linuxnotes.us/archives/66](http://linuxnotes.us/archives/66)


It's not working at the moment, maybe someone can help me?


Installation file
```
#!/bin/bash


DEFAULTS="/etc/default/openvpn"
SCRIPTS="openvpn-wait4active  openvpn-unmount"
FSTAB=/etc/fstab


echo "What are the VPN interfaces (ie:  tap0,  tun0)"
echo -n "Enter all the VPN interfaces separated by spaces: "
read ints
echo "interfaces=\"$ints\"" >> $DEFAULTS




cp $SCRIPTS /etc/init.d
sed -i "s/^mount/#mount/g" /etc/rc.local
sed -i "s./bin/mount.#/bin/mount.g" /etc/rc.local


update-rc.d -f openvpn remove
update-rc.d -f openvpn-wait4active remove
update-rc.d -f openvpn-unmount remove


update-rc.d openvpn start 40 S . stop 39 S .
update-rc.d openvpn-wait4active start 44 S . stop 43 S .




ln -s /etc/init.d/openvpn-unmount /etc/rc0.d/S19openvpn-unmount 
ln -s /etc/init.d/openvpn-unmount /etc/rc6.d/S19openvpn-unmount 
#update-rc.d openvpn-unmount  start 19 0 .
#update-rc.d openvpn-unmount  start 19 6 .




sed -i "s/dmask/dir_mode/g" $FSTAB
sed -i "s/fmask/file_mode/g" $FSTAB




exit 0

```


openvpn wait4active (I added ftp with in the grep command)
```
#!/bin/sh  


### BEGIN INIT INFO
# Provides:          Wait for vpn interfaces to come up
# Required-Start:    $network $local_fs openvpn
# Required-Stop:     $network $local_fs openvon
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Wait until Openvpn VPN service  is fully active
### END INIT INFO


PATH=/sbin:/bin
. /lib/init/vars.sh


. /lib/lsb/init-functions
. /lib/init/mount-functions.sh


if [ -r /etc/default/locale ]; then
	. /etc/default/locale
	export LANG
fi


MAX_TRIES=30


if test -e /etc/default/openvpn ; then
  . /etc/default/openvpn
else
  mount -a -t proc >/dev/null 2>&1  # Ignore error message due to /proc already being mounted
  ES_TO_REPORT=$?
  if [ 0 = "$ES_TO_REPORT" ]
  then
    log_action_end_msg 0
  else
    log_action_end_msg 1 "code $ES_TO_REPORT"
  fi
  exit 0
  interfaces="tap0 tun0"
fi


case "$1" in
start)
	for i in $interfaces; do
		cnt=0
		log_daemon_msg "Waiting for interface: $i                          "
		rc=1
		while [ $rc -ne 0 -a $cnt -lt $MAX_TRIES  ]; do
			cnt=$((cnt + 1))
			sleep 1
			ifconfig | grep -q $i
			rc=$?
		done
		log_action_end_msg $rc
	done
	sleep 15
	# Do the mountall again to mount any filesystems which were
	# unmountable due to the network not being up.
	a=`/bin/grep -v '^#' /etc/fstab | /bin/grep -E "ftp|nfs|nfs4|smbfs|cifs|ncp|ncpfs|coda|ocfs2|gfs" | /usr/bin/awk '{print $1}'`
	for i in $a; do
		log_daemon_msg "Mounting: $i                                 "
		mount $i
		ES_TO_REPORT=$?
		if [ 0 = "$ES_TO_REPORT" ]
		then
			log_action_end_msg 0
		else
			log_action_end_msg 1 "code $ES_TO_REPORT"
		fi
	done
esac

```


openvpn-unmount
```
#!/bin/sh 


#
# openvpn-unmount
#
# This script is designed to unmount the currently mounted
# networked filesystems BEFORE the network is brought down.
#


# Find all networked filesystems.  Currently looks for
# nfs and cifs mounted filesystems 


a=`/bin/df -PT | /bin/grep -E "nfs|nfs4|smbfs|cifs|ncp|ncpfs|coda|ocfs2|gfs" | /usr/bin/awk '{print $7}'`


/bin/umount $a


exit 0



```


installation log:
```
root@raspberrypi:/openvpn_fix# ./setup-openvpn-mounts.sh
What are the VPN interfaces (ie:  tap0,  tun0)
Enter all the VPN interfaces separated by spaces: tun0
update-rc.d: using dependency based boot sequencing
insserv: warning: script 'S19openvpn-unmount' missing LSB tags and overrides
insserv: warning: script 'openvpn-unmount' missing LSB tags and overrides
update-rc.d: using dependency based boot sequencing
insserv: warning: script 'S01openvpn-unmount' missing LSB tags and overrides
insserv: warning: script 'openvpn-unmount' missing LSB tags and overrides
update-rc.d: using dependency based boot sequencing
insserv: warning: script 'S01openvpn-unmount' missing LSB tags and overrides
insserv: warning: script 'openvpn-unmount' missing LSB tags and overrides
update-rc.d: using dependency based boot sequencing
update-rc.d: warning:  start runlevel arguments (S) do not match openvpn Default-Start values (2 3 4 5)
update-rc.d: warning:  stop runlevel arguments (S) do not match openvpn Default-Stop values (0 1 6)
insserv: warning: script 'openvpn-unmount' missing LSB tags and overrides
update-rc.d: using dependency based boot sequencing
update-rc.d: warning:  start runlevel arguments (S) do not match openvpn-wait4active Default-Start values (2 3 4 5)
update-rc.d: warning:  stop runlevel arguments (S) do not match openvpn-wait4active Default-Stop values (0 1 6)
insserv: warning: script 'openvpn-unmount' missing LSB tags and overrides

```


Thank you for your effort.

---

