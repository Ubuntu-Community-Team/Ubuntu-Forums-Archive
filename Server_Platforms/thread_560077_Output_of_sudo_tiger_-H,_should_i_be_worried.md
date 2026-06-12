---
title: "Output of sudo tiger -H, should i be worried?"
date: 2007-09-25
forum: Server Platforms
---

### Post by dynamethod on 2007-09-25
hey there, i just installed and ran tiger, the output has me sorta worried though, as im still trying to decrypt it, could someone please point anything in this log that i should perhaps really worry about and also maybe a solution?

thanks heaps
heres the log:

Tiger security scripts *** 3.2.1, 2003.10.10.18.00 ***
HTML Generator developed by the Advanced Research Corporation (R)
14:05> Beginning security report for xen (i686 Linux 2.6.22-12-generic).

# Performing check of passwd files...
# Checking entries from /etc/passwd.

# WARN [pass014w]Login (backup) is disabled, but has a valid shell.

# WARN [pass014w]Login (bin) is disabled, but has a valid shell.

# WARN [pass014w]Login (daemon) is disabled, but has a valid shell.

# WARN [pass014w]Login (debian-tor) is disabled, but has a valid shell.

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

# WARN [pass015w]Login ID sshd does not have a valid shell (/usr/sbin/nologin).

# WARN [pass015w]Login ID sync does not have a valid shell (/bin/sync).

# WARN [pass014w]Login (sys) is disabled, but has a valid shell.

# WARN [pass014w]Login (uucp) is disabled, but has a valid shell.

# WARN [pass014w]Login (www-data) is disabled, but has a valid shell.

# WARN [pass012w]Home directory /nonexistent exists multiple times (2) in /etc/passwd.

# WARN [pass006w]Integrity of password files questionable (/usr/sbin/pwck -r).

# Performing check of group files...

# Performing check of user accounts...
# Checking accounts from /etc/passwd.

# WARN [acc006w]Login ID gdm's home directory (/var/lib/gdm) has group `gdm' write access.

# WARN [acc022w]Login ID nobody home directory (/nonexistent) is not accessible.

# Performing check of /etc/hosts.equiv and .rhosts files...

# Checking accounts from /etc/passwd...

# Performing check of .netrc files...

# Checking accounts from /etc/passwd...

# Performing common access checks for root (in /etc/default/login, /securetty, and /etc/ttytab...

# WARN [root003w]Root user has message capability turned on.

# WARN [root001w]Remote root login allowed in /etc/ssh/sshd_config

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

# WARN [lin017w]The system is not configured to log suspicious (martian) packets

# Verifying system specific password checks...

# Checking OS release...

# Checking installed packages vs Debian Security Advisories...

# Checking md5sums of installed files

# FAIL [lin006f]Cannot check file "/usr/lib/fglrx/libGL.so.1.2.xlibmesa" provided by "libgl1-mesa-glx" since it does not exist

# Checking installed files against packages...

# WARN [lin001w]File `/lib/modules/fglrx/fglrx.2.6.20-16-generic.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/drm_proc.h' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/drmP.h' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/firegl_public.c' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/drm_compat.h' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/firegl_public.h' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/.fglrx.ko.cmd' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/firegl_public.o' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/.tmp_versions/fglrx.mod' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/Makefile' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC4.cmd' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/fglrx.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/.fglrx.mod.o.cmd' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/.firegl_public.o.cmd' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/.fglrx.o.cmd' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/Module.symvers' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/fglrx.o' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.c' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/drm.h' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/libfglrx_ip.a.GCC4' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/fglrxko_pci_ids.h' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/make.sh.log' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/drm_os_linux.h' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/libfglrx_ip.a.GCC3' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/patch/include/linux/highmem.h' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/make.sh' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/libfglrx_ip.a.GCC2' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/make.2.6.20-16-generic.log' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/make_install.sh' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/nvidia_new.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/nvidia_legacy.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/nvidia.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fxusb.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fglrx.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcusb.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcpci.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcdslusba.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcdslusb2.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcdslusb.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcdslslusb.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcdslsl.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcdsl2.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcdsl.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/ath_hal.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/.mounted' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.20-16-generic/kernel/drivers/char/drm/fglrx.ko' does not belong to any package.

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

# WARN [lin003w]The process `avahi-daemon' is listening on socket 32768 (UDP on every interface) is run by avahi.

# WARN [lin003w]The process `avahi-daemon' is listening on socket 5353 (UDP on every interface) is run by avahi.

# WARN [lin003w]The process `dhclient' is listening on socket 68 (UDP on every interface) is run by dhcp.

# Checking sshd_config configuration files...

# WARN [ssh004w]The PasswordAuthentication directive in /etc/ssh/sshd_config is set to the unapproved defult value: yes.

# Checking printer configuration files...
--ERROR-- [init006e] `/etc/printcap' does not exist (file src).
--ERROR-- [init006e] `/etc/printcap' does not exist (file infile).

# Performing common access checks for root...

# FAIL [netw020f]There is no /etc/ftpusers file.

# Checking ntpd configuration...

# Checking unusual file names...

# Looking for unusual device files...

# ALERT [fsys006a]Unexpected device files found:

crw------- 1 root root 5, 1 Apr 15 23:49 /lib/udev/devices/console
crw-r----- 1 root kmem 1, 2 Apr 15 23:49 /lib/udev/devices/kmem
brw------- 1 root root 7, 0 Apr 15 23:49 /lib/udev/devices/loop0
crw------- 1 root root 10, 200 Apr 15 23:49 /lib/udev/devices/net/tun
crw------- 1 root root 1, 3 Apr 15 23:49 /lib/udev/devices/null
crw------- 1 root root 108, 0 Apr 15 23:49 /lib/udev/devices/ppp
lrwxrwxrwx 1 root root 15 Sep 14 01:56 /lib/udev/devices/stderr -> /proc/self/fd/2


# Checking symbolic links...

# Performing check of embedded pathnames...

# WARN [embed002w]Path `/usr/lib/cups/daemon/cups-check-pam-auth' is not owned by root (owned by cupsys).

---

### Post by dynamethod on 2007-09-25
should i just ignore this?

---

### Post by dynamethod on 2007-09-25
hey there, i just installed and ran tiger, the output has me sorta worried though, as im still trying to decrypt it, could someone please point anything in this log that i should perhaps really worry about and also maybe a solution?

thanks heaps
heres the log:

Tiger security scripts *** 3.2.1, 2003.10.10.18.00 ***
HTML Generator developed by the Advanced Research Corporation (R)
14:05> Beginning security report for xen (i686 Linux 2.6.22-12-generic).

# Performing check of passwd files...
# Checking entries from /etc/passwd.

# WARN [pass014w]Login (backup) is disabled, but has a valid shell.

# WARN [pass014w]Login (bin) is disabled, but has a valid shell.

# WARN [pass014w]Login (daemon) is disabled, but has a valid shell.

# WARN [pass014w]Login (debian-tor) is disabled, but has a valid shell.

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

# WARN [pass015w]Login ID sshd does not have a valid shell (/usr/sbin/nologin).

# WARN [pass015w]Login ID sync does not have a valid shell (/bin/sync).

# WARN [pass014w]Login (sys) is disabled, but has a valid shell.

# WARN [pass014w]Login (uucp) is disabled, but has a valid shell.

# WARN [pass014w]Login (www-data) is disabled, but has a valid shell.

# WARN [pass012w]Home directory /nonexistent exists multiple times (2) in /etc/passwd.

# WARN [pass006w]Integrity of password files questionable (/usr/sbin/pwck -r).

# Performing check of group files...

# Performing check of user accounts...
# Checking accounts from /etc/passwd.

# WARN [acc006w]Login ID gdm's home directory (/var/lib/gdm) has group `gdm' write access.

# WARN [acc022w]Login ID nobody home directory (/nonexistent) is not accessible.

# Performing check of /etc/hosts.equiv and .rhosts files...

# Checking accounts from /etc/passwd...

# Performing check of .netrc files...

# Checking accounts from /etc/passwd...

# Performing common access checks for root (in /etc/default/login, /securetty, and /etc/ttytab...

# WARN [root003w]Root user has message capability turned on.

# WARN [root001w]Remote root login allowed in /etc/ssh/sshd_config

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

# WARN [lin017w]The system is not configured to log suspicious (martian) packets

# Verifying system specific password checks...

# Checking OS release...

# Checking installed packages vs Debian Security Advisories...

# Checking md5sums of installed files

# FAIL [lin006f]Cannot check file "/usr/lib/fglrx/libGL.so.1.2.xlibmesa" provided by "libgl1-mesa-glx" since it does not exist

# Checking installed files against packages...

# WARN [lin001w]File `/lib/modules/fglrx/fglrx.2.6.20-16-generic.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/drm_proc.h' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/drmP.h' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/firegl_public.c' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/drm_compat.h' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/firegl_public.h' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/.fglrx.ko.cmd' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/firegl_public. o' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/.tmp_versions/ fglrx.mod' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/Makefile' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a .GCC4.cmd' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/fglrx.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/.fglrx.mod.o.c md' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/.firegl_public .o.cmd' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/.fglrx.o.cmd' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/Module.symvers ' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/fglrx.o' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.c' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/drm.h' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/libfglrx_ip.a.GCC4' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/fglrxko_pci_ids.h' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/make.sh.log' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/drm_os_linux.h' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/libfglrx_ip.a.GCC3' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/patch/include/linux/ highmem.h' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/make.sh' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/libfglrx_ip.a.GCC2' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/make.2.6.20-16-generic.log' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/make_install.sh' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/nvidia_new.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/nvidia_legacy.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/nvidia.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fxusb.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fglrx.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcusb.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcpci.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcdslusba.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcdslusb2.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcdslusb.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcdslslusb.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcdslsl.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcdsl2.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcdsl.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/ath_hal.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/.mounted' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.20-16-generic/kernel/drivers/char/drm/fglrx.ko' does not belong to any package.

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

# WARN [lin003w]The process `avahi-daemon' is listening on socket 32768 (UDP on every interface) is run by avahi.

# WARN [lin003w]The process `avahi-daemon' is listening on socket 5353 (UDP on every interface) is run by avahi.

# WARN [lin003w]The process `dhclient' is listening on socket 68 (UDP on every interface) is run by dhcp.

# Checking sshd_config configuration files...

# WARN [ssh004w]The PasswordAuthentication directive in /etc/ssh/sshd_config is set to the unapproved defult value: yes.

# Checking printer configuration files...
--ERROR-- [init006e] `/etc/printcap' does not exist (file src).
--ERROR-- [init006e] `/etc/printcap' does not exist (file infile).

# Performing common access checks for root...

# FAIL [netw020f]There is no /etc/ftpusers file.

# Checking ntpd configuration...

# Checking unusual file names...

# Looking for unusual device files...

# ALERT [fsys006a]Unexpected device files found:

crw------- 1 root root 5, 1 Apr 15 23:49 /lib/udev/devices/console
crw-r----- 1 root kmem 1, 2 Apr 15 23:49 /lib/udev/devices/kmem
brw------- 1 root root 7, 0 Apr 15 23:49 /lib/udev/devices/loop0
crw------- 1 root root 10, 200 Apr 15 23:49 /lib/udev/devices/net/tun
crw------- 1 root root 1, 3 Apr 15 23:49 /lib/udev/devices/null
crw------- 1 root root 108, 0 Apr 15 23:49 /lib/udev/devices/ppp
lrwxrwxrwx 1 root root 15 Sep 14 01:56 /lib/udev/devices/stderr -> /proc/self/fd/2


# Checking symbolic links...

# Performing check of embedded pathnames...

# WARN [embed002w]Path `/usr/lib/cups/daemon/cups-check-pam-auth' is not owned by root (owned by cupsys).



<snip>

---

### Post by djchandler on 2007-09-25
Ho Ho Ho... yawn...zzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzz

---

### Post by lisati on 2007-09-25
> **dynamethod said:**
> hey there, i just installed and ran tiger, the output has me sorta worried though, as im still trying to decrypt it, could someone please point anything in this log that i should perhaps really worry about and also maybe a solution?

thanks heaps
heres the log:
```

Tiger security scripts *** 3.2.1, 2003.10.10.18.00 ***
HTML Generator developed by the Advanced Research Corporation (R)
14:05> Beginning security report for xen (i686 Linux 2.6.22-12-generic).

# Performing check of passwd files...
# Checking entries from /etc/passwd.

# WARN [pass014w]Login (backup) is disabled, but has a valid shell.

# WARN [pass014w]Login (bin) is disabled, but has a valid shell.

# WARN [pass014w]Login (daemon) is disabled, but has a valid shell.

# WARN [pass014w]Login (debian-tor) is disabled, but has a valid shell.

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

# WARN [pass015w]Login ID sshd does not have a valid shell (/usr/sbin/nologin).

# WARN [pass015w]Login ID sync does not have a valid shell (/bin/sync).

# WARN [pass014w]Login (sys) is disabled, but has a valid shell.

# WARN [pass014w]Login (uucp) is disabled, but has a valid shell.

# WARN [pass014w]Login (www-data) is disabled, but has a valid shell.

# WARN [pass012w]Home directory /nonexistent exists multiple times (2) in /etc/passwd.

# WARN [pass006w]Integrity of password files questionable (/usr/sbin/pwck -r).

# Performing check of group files...

# Performing check of user accounts...
# Checking accounts from /etc/passwd.

# WARN [acc006w]Login ID gdm's home directory (/var/lib/gdm) has group `gdm' write access.

# WARN [acc022w]Login ID nobody home directory (/nonexistent) is not accessible.

# Performing check of /etc/hosts.equiv and .rhosts files...

# Checking accounts from /etc/passwd...

# Performing check of .netrc files...

# Checking accounts from /etc/passwd...

# Performing common access checks for root (in /etc/default/login, /securetty, and /etc/ttytab...

# WARN [root003w]Root user has message capability turned on.

# WARN [root001w]Remote root login allowed in /etc/ssh/sshd_config

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

# WARN [lin017w]The system is not configured to log suspicious (martian) packets

# Verifying system specific password checks...

# Checking OS release...

# Checking installed packages vs Debian Security Advisories...

# Checking md5sums of installed files

# FAIL [lin006f]Cannot check file "/usr/lib/fglrx/libGL.so.1.2.xlibmesa" provided by "libgl1-mesa-glx" since it does not exist

# Checking installed files against packages...

# WARN [lin001w]File `/lib/modules/fglrx/fglrx.2.6.20-16-generic.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/drm_proc.h' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/drmP.h' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/firegl_public.c' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/drm_compat.h' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/firegl_public.h' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/.fglrx.ko.cmd' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/firegl_public. o' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/.tmp_versions/ fglrx.mod' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/Makefile' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a .GCC4.cmd' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/fglrx.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/.fglrx.mod.o.c md' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/.firegl_public .o.cmd' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/.fglrx.o.cmd' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/Module.symvers ' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/fglrx.o' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.c' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/drm.h' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/libfglrx_ip.a.GCC4' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/fglrxko_pci_ids.h' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/make.sh.log' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/drm_os_linux.h' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/libfglrx_ip.a.GCC3' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/patch/include/linux/ highmem.h' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/make.sh' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/build_mod/libfglrx_ip.a.GCC2' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/make.2.6.20-16-generic.log' does not belong to any package.

# WARN [lin001w]File `/lib/modules/fglrx/make_install.sh' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/nvidia_new.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/nvidia_legacy.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/nvidia.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fxusb.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fglrx.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcusb.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcpci.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcdslusba.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcdslusb2.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcdslusb.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcdslslusb.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcdslsl.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcdsl2.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/fcdsl.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/ath_hal.ko' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.22-12-generic/volatile/.mounted' does not belong to any package.

# WARN [lin001w]File `/lib/modules/2.6.20-16-generic/kernel/drivers/char/drm/fglrx.ko' does not belong to any package.

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

# WARN [lin003w]The process `avahi-daemon' is listening on socket 32768 (UDP on every interface) is run by avahi.

# WARN [lin003w]The process `avahi-daemon' is listening on socket 5353 (UDP on every interface) is run by avahi.

# WARN [lin003w]The process `dhclient' is listening on socket 68 (UDP on every interface) is run by dhcp.

# Checking sshd_config configuration files...

# WARN [ssh004w]The PasswordAuthentication directive in /etc/ssh/sshd_config is set to the unapproved defult value: yes.

# Checking printer configuration files...
--ERROR-- [init006e] `/etc/printcap' does not exist (file src).
--ERROR-- [init006e] `/etc/printcap' does not exist (file infile).

# Performing common access checks for root...

# FAIL [netw020f]There is no /etc/ftpusers file.

# Checking ntpd configuration...

# Checking unusual file names...

# Looking for unusual device files...

# ALERT [fsys006a]Unexpected device files found:

crw------- 1 root root 5, 1 Apr 15 23:49 /lib/udev/devices/console
crw-r----- 1 root kmem 1, 2 Apr 15 23:49 /lib/udev/devices/kmem
brw------- 1 root root 7, 0 Apr 15 23:49 /lib/udev/devices/loop0
crw------- 1 root root 10, 200 Apr 15 23:49 /lib/udev/devices/net/tun
crw------- 1 root root 1, 3 Apr 15 23:49 /lib/udev/devices/null
crw------- 1 root root 108, 0 Apr 15 23:49 /lib/udev/devices/ppp
lrwxrwxrwx 1 root root 15 Sep 14 01:56 /lib/udev/devices/stderr -> /proc/self/fd/2


# Checking symbolic links...

# Performing check of embedded pathnames...

# WARN [embed002w]Path `/usr/lib/cups/daemon/cups-check-pam-auth' is not owned by root (owned by cupsys).


```

<snip>

<snip>

---

### Post by dynamethod on 2007-09-25
lol, ok but seriously, is there anything i should be worried about?

---

### Post by bodhi.zazen on 2007-09-26
If you are interested, you should work through that output and decide for yourself what, if any, action to take.

You can :

```
sudo tiger -eH
```

-e = exlpain, this will give a more detailed explication of the warnings and possible solutions.
-H = Generates a nice report in HTML format (you can read through it with firefox)

Or :

```
/usr/sbin/tigexp xxx
```

* change xxx  to a warning code, like this :

> $ /usr/sbin/tigexp pass014w

The listed login ID is disabled in some manner ('*' in passwd field, etc),
but the login shell for the login ID is a valid shell (from /etc/shells
or the system equivalent). A valid shell can potentially enable the
login ID to continue to be used. The login shell should be changed to
something that doesn't exist, or to something like /bin/false.

Once you are done, you will understand a lot more.

If you do not have the time/interest I would not run tiger nor would I advise you follow the advice of others, security is something you need to learn for yourself, IMO at least.

---

### Post by dynamethod on 2007-09-26
ok ive fixed some of things from my sudo tiger -H

but now i got these entrys, which *i think* explains why im having trouble connecting to the net :S

# WARN [lin012w]The system accepts ICMP redirection messages

# FAIL [lin013f]The system is not protected against Syn flooding attacks

# FAIL [lin014f]The system permits the transmission of IP packets with invalid addresses

# FAIL [lin016f]The system permits source routing from incoming packets

# WARN [lin017w]The system is not configured to log suspicious (martian) packets

# FAIL [lin019f]The system does not have any local firewall rules configured

how could i go about fixing these problems?

thanks in advance :)

---

### Post by bodhi.zazen on 2007-09-26
dynamethod : I merged your 3 threads and after reviewing the content believe it is best in the Servers and Security section.

Please try not to start multiple threads on the same topic as it makes it difficult or confusing to help you with information spread across multiple threads. This makes it difficult to follow what advice has been given and what you have done ...

I do not see how those warnings would be related to your connectivity problem.

---

### Post by dynamethod on 2007-09-26
ok sorry bout that,

well the syn flood thing, well...  im getting alot of that lately, in my router logs too, ALOT of them :S

plus im just curious as to how i could change the settings

---

### Post by /etc/init.d/ on 2007-09-26
There is nothing in there that indicates any serious security vulnerability, except perhaps that root login is allowed in /etc/ssh/sshd_config.  You should turn that off, even though by default the root account is disabled.  Browse through that file and you'll see a line "PermitRootLogin"; change it to "no" if it's set to "yes".

---

