---
title: "concerned about tiger security check output"
date: 2007-11-12
forum: Server Platforms
---

### Post by genbuntu on 2007-11-12
Hi
I downloaded the tiger security tool and ran ```
sudo tiger -H
``` which gave me some 'WARN' and 'FAIL' results.  Being new to linux, I cannot make much sense of these and/or how to rectify the problem.

Could someone pls. have a look and let me know of any serious security issues my system may be having? Thx. 
(In case this helps -> I have a dual-boot with winXP). 
Here is the output:
```

Tiger security scripts *** 3.2.1, 2003.10.10.18.00 ***
HTML Generator developed by the Advanced Research Corporation (R)
Mon Nov 12 16:10:32 PST 2007
16:10> Beginning security report for zis (i686 Linux 2.6.20-16-generic).

# Performing check of passwd files...
# Checking entries from /etc/passwd.

# WARN [pass014w]Login (backup) is disabled, but has a valid shell.

# WARN [pass014w]Login (bin) is disabled, but has a valid shell.

# WARN [pass014w]Login (daemon) is disabled, but has a valid shell.

# WARN [pass014w]Login (games) is disabled, but has a valid shell.

# WARN [pass014w]Login (gnats) is disabled, but has a valid shell.

# WARN [pass014w]Login (irc) is disabled, but has a valid shell.

# WARN [pass014w]Login (list) is disabled, but has a valid shell.

# WARN [pass014w]Login (lp) is disabled, but has a valid shell.

# WARN [pass014w]Login (mail) is disabled, but has a valid shell.

# WARN [pass014w]Login (man) is disabled, but has a valid shell.

# WARN [pass014w]Login (news) is disabled, but has a valid shell.

# WARN [pass014w]Login (nobody) is disabled, but has a valid shell.

# WARN [pass014w]Login (proxy) is disabled, but has a valid shell.

# WARN [pass014w]Login (root) is disabled, but has a valid shell.

# WARN [pass015w]Login ID sync does not have a valid shell (/bin/sync).

# WARN [pass014w]Login (sys) is disabled, but has a valid shell.

# WARN [pass014w]Login (uucp) is disabled, but has a valid shell.

# WARN [pass014w]Login (www-data) is disabled, but has a valid shell.

# WARN [pass012w]Home directory /nonexistent exists multiple times (2) in /etc/passwd.

# WARN [pass006w]Integrity of password files questionable (/usr/sbin/pwck -r).

# Performing check of group files...

# Performing check of user accounts...
# Checking accounts from /etc/passwd.

# WARN [acc021w]Login ID avahi-autoipd appears to be a dormant account.

# WARN [acc006w]Login ID gdm's home directory (/var/lib/gdm) has group `gdm' write access.

# WARN [acc022w]Login ID nobody home directory (/nonexistent) is not accessible.

# Performing check of /etc/hosts.equiv and .rhosts files...

# Checking accounts from /etc/passwd...

# Performing check of .netrc files...

# Checking accounts from /etc/passwd...

# Performing common access checks for root (in /etc/default/login, /securetty, and /etc/ttytab...

# WARN [root003w]Root user has message capability turned on.

# Performing check of PATH components...

# WARN [path009w]/etc/profile does not export an initial setting for PATH.

# Only checking user 'root'

# Performing check of anonymous FTP...

# Performing checks of mail aliases...
# Checking aliases from /etc/aliases.

# Performing check of `cron' entries...

# WARN [cron004w]Root crontab does not exist

# WARN [cron005w]Use of cron is not restricted

# Performing check of 'inetd'...
# Checking inetd entries from /etc/inetd.conf

# Performing check of services with tcp wrappers...

# FAIL [inet021f]Tcp wrappers does not seem to be installed in this system.

# FAIL [inet022f]The hosts.allow file used by Tcp wrappers does not seem to be present in this system

# FAIL [inet022f]The hosts.deny file used by Tcp wrappers does not seem to be present in this system

# Analysing inetd entries from /etc/inetd.conf

# Performing check of 'services' ...
# Checking services from /etc/services.

# WARN [inet003w]The port for service postgres is also assigned to service postgresql.

# WARN [inet003w]The port for service postgres is also assigned to service postgresql.

# WARN [inet003w]The port for service sane is also assigned to service sane-port.

# Performing NFS exports check...

# Performing check of system file permissions...

# Checking for known intrusion signs...
# Testing for promiscuous interfaces with /bin/ip
# Testing for backdoors in inetd.conf

# Performing check of files in system mail spool...

# Performing check for rookits...
# Running chkrootkit (/usr/sbin/chkrootkit) to perform further checks...

# Performing system specific checks...
# Performing checks for Linux/2...

# Checking for single user-mode password...

# Checking boot loader file permissions...

# WARN [boot02]The configuration file /boot/grub/menu.lst has group permissions. Should be 0600

# FAIL [boot02]The configuration file /boot/grub/menu.lst has world permissions. Should be 0600

# WARN [boot06]The Grub bootloader does not have a password configured.

# Checking for vulnerabilities in inittab configuration...

# Checking for correct umask settings for init scripts...

# WARN [misc021w]There are no umask entries in /etc/init.d/rcS

# Checking Logins not used on the system ...

# Checking network configuration

# WARN [lin012w]The system accepts ICMP redirection messages

# FAIL [lin013f]The system is not protected against Syn flooding attacks

# FAIL [lin014f]The system permits the transmission of IP packets with invalid addresses

# FAIL [lin016f]The system permits source routing from incoming packets

# WARN [lin017w]The system is not configured to log suspicious (martian) packets

# FAIL [lin019f]The system does not have any local firewall rules configured

# Verifying system specific password checks...

# Checking OS release...

# Checking installed packages vs Debian Security Advisories...

# Checking md5sums of installed files

# Checking installed files against packages...

# WARN [lin001w]File `/lib/modules/2.6.20-16-generic/volatile/nvidia_new.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.20-16-generic/volatile/nvidia_legacy.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.20-16-generic/volatile/nvidia.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.20-16-generic/volatile/fxusb.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.20-16-generic/volatile/fglrx.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.20-16-generic/volatile/fcusb.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.20-16-generic/volatile/fcpci.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.20-16-generic/volatile/fcdslusba.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.20-16-generic/volatile/fcdslusb2.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.20-16-generic/volatile/fcdslusb.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.20-16-generic/volatile/fcdslslusb.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.20-16-generic/volatile/fcdslsl.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.20-16-generic/volatile/fcdsl2.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.20-16-generic/volatile/fcdsl.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.20-16-generic/volatile/ath_hal.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.20-16-generic/volatile/.mounted' does not belong to any package.

# WARN [lin001w]File `/usr/sbin/startupmanager' does not belong to any package.

# Performing check of root directory...

# Checking device permissions...

# WARN [dev003w]The directory /dev/bus resides in a device directory.

# WARN [dev003w]The directory /dev/disk resides in a device directory.

# WARN [dev003w]The directory /dev/dri resides in a device directory.

# FAIL [dev002f]/dev/log has world permissions

# WARN [dev003w]The directory /dev/snd resides in a device directory.

# WARN [dev003w]File /dev/sndstat is a regular file in a device directory.

# Checking for existence of log files...

# FAIL [logf005f]Log file /var/log/btmp permission should be 660

# Checking for correct umask settings...

# Checking listening processes

# WARN [lin003w]The process `dhclient' is listening on socket 68 (UDP on every interface) is run by dhcp.

# WARN [lin003w]The process `dhclient3' is listening on socket 68 (UDP on every interface) is run by dhcp.

# WARN [lin002i]The process `nmbd' is listening on socket 137 (UDP) on every interface.

# WARN [lin002i]The process `nmbd' is listening on socket 138 (UDP) on every interface.

# WARN [lin003w]The process `portmap' is listening on socket 111 (TCP on every interface) is run by daemon.

# WARN [lin003w]The process `portmap' is listening on socket 111 (UDP on every interface) is run by daemon.

# WARN [lin002i]The process `rpc.mountd' is listening on socket 868 (TCP) on every interface.

# WARN [lin002i]The process `rpc.mountd' is listening on socket 865 (UDP) on every interface.

# WARN [lin003w]The process `rpc.statd' is listening on socket 60047 (TCP on every interface) is run by statd.

# WARN [lin003w]The process `rpc.statd' is listening on socket 32770 (UDP on every interface) is run by statd.

# WARN [lin003w]The process `rpc.statd' is listening on socket 981 (UDP on every interface) is run by statd.

# WARN [lin002i]The process `smbd' is listening on socket 139 (TCP) on every interface.

# WARN [lin002i]The process `smbd' is listening on socket 445 (TCP) on every interface.

# Checking sshd_config configuration files...

# FAIL [ssh005w]Cannot find a configuration file for SSH.

# Checking printer configuration files...

# Performing common access checks for root...

# FAIL [netw020f]There is no /etc/ftpusers file.

# Checking ntpd configuration...

# Checking unusual file names...

# Looking for unusual device files...

# ALERT [fsys006a]Unexpected device files found:

crw------- 1 root root 5, 1 Apr 15  2007 /lib/udev/devices/console
crw-r----- 1 root kmem 1, 2 Apr 15  2007 /lib/udev/devices/kmem
brw------- 1 root root 7, 0 Apr 15  2007 /lib/udev/devices/loop0
crw------- 1 root root 10, 200 Apr 15  2007 /lib/udev/devices/net/tun
crw------- 1 root root 1, 3 Apr 15  2007 /lib/udev/devices/null
crw------- 1 root root 108, 0 Apr 15  2007 /lib/udev/devices/ppp
lrwxrwxrwx 1 root root 15 Jul 22 17:08 /lib/udev/devices/stderr -> /proc/self/fd/2


# Checking symbolic links...

# Performing check of embedded pathnames...

# WARN [embed002w]Path `/usr/lib/cups/daemon/cups-check-pam-auth' is not owned by root (owned by cupsys).

Embedded references in: /usr/sbin/cupsd->/etc/init.d/cupsys
```

---

### Post by doanut on 2007-11-13
Most of the WARN errors are safe to ignore.
You really want to be looking at the FAIL errors

It basically tells you what needs to be done in the output.

> FAIL [netw020f]There is no /etc/ftpusers file.

If you have ftp running touch a file and google 'ftpusers file' and read up on it. Otherwise you can ignore it.

---

