---
title: "Tiger Troubles??"
date: 2008-02-17
forum: Security Discussions
---

### Post by sTpny on 2008-02-17
Hi all, following advice I found here on the forums, I installed and ran Tiger, but I'm not sure if I should be worried about the results. The terminal output of the programs execution and the log file it generated follow.  Could someone please tell me if anything is wrong. Has my system been compramised, or are these warnings and failures normal for this program.


<START PASTE>

tony@tonys-pc:~$ sudo tiger
[sudo] password for tony:
Tiger UN*X security checking system
   Developed by Texas A&M University, 1994
   Updated by the Advanced Research Corporation, 1999-2002
   Further updated by Javier Fernandez-Sanguino, 2001-2005
   Covered by the GNU General Public License (GPL)

Configuring...
 
Will try to check using config for 'i686' running Linux 2.6.22-14-generic...
--CONFIG-- [con005c] Using configuration files for Linux 2.6.22-14-generic. Using
           configuration files for generic Linux 2.
Tiger security scripts *** 3.2.1, 2003.10.10.18.00 ***
12:26> Beginning security report for tonys-pc.
12:26> Starting file systems scans in background...
12:26> Checking password files...
12:26> Checking group files...
12:26> Checking user accounts...
12:26> Checking .rhosts files...
12:26> Checking .netrc files...
12:26> Checking ttytab, securetty, and login configuration files...
12:26> Checking PATH settings...
12:27> Checking anonymous ftp setup...
12:27> Checking mail aliases...
12:27> Checking cron entries...
12:27> Checking 'inetd' configuration...
12:27> Checking 'tcpd' configuration...
12:27> Checking 'services' configuration...
12:28> Checking NFS export entries...
12:28> Checking permissions and ownership of system files...
--CONFIG-- [con010c] Filesystem 'securityfs' used by 'securityfs' is not recognised as a local filesystem
12:28> Checking for indications of break-in...
--CONFIG-- [con010c] Filesystem 'securityfs' used by 'securityfs' is not recognised as a local filesystem
12:28> Performing rootkit checks...
12:29> Performing system specific checks...
12:57> Performing root directory checks...
12:57> Checking for secure backup devices...
12:57> Checking for the presence of log files...
12:57> Checking for the setting of user's umask...
12:57> Checking for listening processes...
12:57> Checking SSHD's configuration...
12:57> Checking the printers control file...
12:57> Checking ftpusers configuration...
12:57> Checking NTP configuration...
12:57> Waiting for filesystems scans to complete...
12:57> Filesystems scans completed...
12:57> Performing check of embedded pathnames...
13:00> Security report completed for tonys-pc.
Security report is in `/var/log/tiger/security.report.tonys-pc.080217-12:26'.
tony@tonys-pc:~$ cat /var/log/tiger/security.report.tonys-pc.080217-12:26
cat: /var/log/tiger/security.report.tonys-pc.080217-12:26: Permission denied
tony@tonys-pc:~$ sudo cat /var/log/tiger/security.report.tonys-pc.080217-12:26
[sudo] password for tony:
Security scripts *** 3.2.1, 2003.10.10.18.00 ***
Sun Feb 17 12:26:15 PST 2008
12:26> Beginning security report for tonys-pc (i686 Linux 2.6.22-14-generic).

# Performing check of passwd files...
# Checking entries from /etc/passwd.
--WARN-- [pass014w] Login (backup) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (bin) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (daemon) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (games) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (gnats) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (irc) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (kathy) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (list) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (lp) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (mail) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (man) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (news) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (nobody) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (proxy) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (root) is disabled, but has a valid shell. 
--WARN-- [pass015w] Login ID sync does not have a valid shell (/bin/sync). 
--WARN-- [pass014w] Login (sys) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (uucp) is disabled, but has a valid shell. 
--WARN-- [pass014w] Login (www-data) is disabled, but has a valid shell. 
--WARN-- [pass012w] Home directory /nonexistent exists multiple times (2) in 
         /etc/passwd. 
--WARN-- [pass006w] Integrity of password files questionable (/usr/sbin/pwck 
         -r). 

# Performing check of group files...

# Performing check of user accounts...
# Checking accounts from /etc/passwd.
--WARN-- [acc006w] Login ID gdm's home directory (/var/lib/gdm) has group 
         `gdm' write access. 
--WARN-- [acc022w] Login ID nobody home directory (/nonexistent) is not 
         accessible. 

# Performing check of /etc/hosts.equiv and .rhosts files...

# Checking accounts from /etc/passwd...

# Performing check of .netrc files...

# Checking accounts from /etc/passwd...

# Performing common access checks for root (in /etc/default/login, /securetty, and /etc/ttytab...
--WARN-- [root003w] Root user has message capability turned on. 

# Performing check of PATH components...
--WARN-- [path009w] /etc/profile does not export an initial setting for PATH. 
# Only checking user 'root'

# Performing check of anonymous FTP...

# Performing checks of mail aliases...
# Checking aliases from /etc/aliases.

# Performing check of `cron' entries...
--WARN-- [cron004w] Root crontab does not exist 
--WARN-- [cron005w] Use of cron is not restricted 

# Performing check of 'inetd'...
# Checking inetd entries from /etc/inetd.conf

# Performing check of services with tcp wrappers...
# Analysing inetd entries from /etc/inetd.conf

# Performing check of 'services' ...
# Checking services from /etc/services.
--WARN-- [inet003w] The port for service postgres is also assigned to service 
         postgresql. 
--WARN-- [inet003w] The port for service postgres is also assigned to service 
         postgresql. 
--WARN-- [inet003w] The port for service sane is also assigned to service 
         sane-port. 

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
--WARN-- [boot02] The configuration file /boot/grub/menu.lst has group 
         permissions. Should be 0600 
--FAIL-- [boot02] The configuration file /boot/grub/menu.lst has world 
         permissions. Should be 0600 
--WARN-- [boot06] The Grub bootloader does not have a password configured. 

# Checking for vulnerabilities in inittab configuration...

# Checking for correct umask settings for init scripts...
--WARN-- [misc021w] There are no umask entries in /etc/init.d/rcS 

# Checking Logins not used on the system ...

# Checking network configuration
--WARN-- [lin012w] The system accepts ICMP redirection messages 
--WARN-- [lin017w] The system is not configured to log suspicious (martian) 
         packets 
--FAIL-- [lin019f] The system does not have any local firewall rules 
         configured 

# Verifying system specific password checks...

# Checking OS release...
--WARN-- [osv004w] Unreleased Debian GNU/Linux version `lenny/sid' 

# Checking installed packages vs Debian Security Advisories...

# Checking md5sums of installed files
--FAIL-- [lin005f] Installed file 
         `/lib/modules/2.6.22-14-generic/modules.pcimap' checksum differs from 
         installed package 'linux-image-2.6.22-14-generic'. 
--FAIL-- [lin005f] Installed file `/lib/modules/2.6.22-14-generic/modules.dep' 
         checksum differs from installed package 
         'linux-image-2.6.22-14-generic'. 
--FAIL-- [lin005f] Installed file 
         `/lib/modules/2.6.22-14-generic/modules.usbmap' checksum differs from 
         installed package 'linux-image-2.6.22-14-generic'. 
--FAIL-- [lin005f] Installed file 
         `/lib/modules/2.6.22-14-generic/modules.isapnpmap' checksum differs 
         from installed package 'linux-image-2.6.22-14-generic'. 
--FAIL-- [lin005f] Installed file 
         `/lib/modules/2.6.22-14-generic/modules.seriomap' checksum differs 
         from installed package 'linux-image-2.6.22-14-generic'. 
--FAIL-- [lin005f] Installed file 
         `/lib/modules/2.6.22-14-generic/modules.alias' checksum differs from 
         installed package 'linux-image-2.6.22-14-generic'. 
--FAIL-- [lin005f] Installed file 
         `/lib/modules/2.6.22-14-generic/modules.symbols' checksum differs 
         from installed package 'linux-image-2.6.22-14-generic'. 

# Checking installed files against packages...
--WARN-- [lin001w] File 
         `/lib/modules/2.6.22-14-generic/volatile/nvidia_new.ko' does not 
         belong to any package. 
--WARN-- [lin001w] File 
         `/lib/modules/2.6.22-14-generic/volatile/nvidia_legacy.ko' does not 
         belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.22-14-generic/volatile/nvidia.ko' 
         does not belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.22-14-generic/volatile/fxusb.ko' 
         does not belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.22-14-generic/volatile/fwlanusb.ko' 
         does not belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.22-14-generic/volatile/fglrx.ko' 
         does not belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.22-14-generic/volatile/fcusb.ko' 
         does not belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.22-14-generic/volatile/fcpci.ko' 
         does not belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.22-14-generic/volatile/fcdslusba.ko' 
         does not belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.22-14-generic/volatile/fcdslusb2.ko' 
         does not belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.22-14-generic/volatile/fcdslusb.ko' 
         does not belong to any package. 
--WARN-- [lin001w] File 
         `/lib/modules/2.6.22-14-generic/volatile/fcdslslusb.ko' does not 
         belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.22-14-generic/volatile/fcdslsl.ko' 
         does not belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.22-14-generic/volatile/fcdsl2.ko' 
         does not belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.22-14-generic/volatile/fcdsl.ko' 
         does not belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.22-14-generic/volatile/ath_hal.ko' 
         does not belong to any package. 
--WARN-- [lin001w] File `/lib/modules/2.6.22-14-generic/volatile/.mounted' 
         does not belong to any package. 

# Performing check of root directory...

# Checking device permissions...
--FAIL-- [dev002f] /dev/log has world permissions 
--WARN-- [dev003w] File /dev/sndstat is a regular file in a device directory. 

# Checking for existence of log files...
--FAIL-- [logf005f] Log file /var/log/btmp permission should be 660 

# Checking for correct umask settings...

# Checking listening processes 
--WARN-- [lin003w] The process `avahi-daemon' is listening on socket 32772 
         (UDP on every interface) is run by avahi. 
--WARN-- [lin003w] The process `avahi-daemon' is listening on socket 5353 (UDP 
         on every interface) is run by avahi. 
--WARN-- [lin002i] The process `cupsd' is listening on socket 631 (TCP) on 
         every interface. 
--WARN-- [lin002i] The process `cupsd' is listening on socket 631 (UDP) on 
         every interface. 
--WARN-- [lin003w] The process `dhclient' is listening on socket 68 (UDP on 
         every interface) is run by dhcp. 
--WARN-- [lin002i] The process `nmbd' is listening on socket 137 (UDP) on 
         every interface. 
--WARN-- [lin002i] The process `nmbd' is listening on socket 138 (UDP) on 
         every interface. 
--WARN-- [lin003w] The process `portmap' is listening on socket 111 (TCP on 
         every interface) is run by daemon. 
--WARN-- [lin003w] The process `portmap' is listening on socket 111 (UDP on 
         every interface) is run by daemon. 
--WARN-- [lin002i] The process `rpc.mountd' is listening on socket 58568 (TCP) 
         on every interface. 
--WARN-- [lin002i] The process `rpc.mountd' is listening on socket 32771 (UDP) 
         on every interface. 
--WARN-- [lin003w] The process `rpc.statd' is listening on socket 39658 (TCP 
         on every interface) is run by statd. 
--WARN-- [lin003w] The process `rpc.statd' is listening on socket 32768 (UDP 
         on every interface) is run by statd. 
--WARN-- [lin003w] The process `rpc.statd' is listening on socket 964 (UDP on 
         every interface) is run by statd. 
--WARN-- [lin002i] The process `smbd' is listening on socket 139 (TCP) on 
         every interface. 
--WARN-- [lin002i] The process `smbd' is listening on socket 445 (TCP) on 
         every interface. 

# Checking sshd_config configuration files...
--FAIL-- [ssh005w] Cannot find a configuration file for SSH. 

# Performing common access checks for root...
--FAIL-- [netw020f] There is no /etc/ftpusers file. 

# Checking ntpd configuration...

# Checking unusual file names...

# Looking for unusual device files...
--ALERT-- [fsys006a] Unexpected device files found: 
crw------- 1 root root 5, 1 Oct 15 16:18 /lib/udev/devices/console
crw-r----- 1 root kmem 1, 2 Oct 15 16:18 /lib/udev/devices/kmem
brw------- 1 root root 7, 0 Oct 15 16:18 /lib/udev/devices/loop0
crw------- 1 root root 10, 200 Oct 15 16:18 /lib/udev/devices/net/tun
crw------- 1 root root 1, 3 Oct 15 16:18 /lib/udev/devices/null
crw------- 1 root root 108, 0 Oct 15 16:18 /lib/udev/devices/ppp
lrwxrwxrwx 1 root root 15 Jan 24 01:10 /lib/udev/devices/stderr -> /proc/self/fd/2


# Checking symbolic links...

# Performing check of embedded pathnames...
13:00> Security report completed for tonys-pc.


<END PASTE>

So, am I in any trouble here. Is there anything I should do?

---

### Post by bodhi.zazen on 2008-02-18
Tiger is a great learning tool. You need to invest time in security, it is not an automated process.

Run tiger from the command line with :
```
sudo tiger -H
```

The -H flag will produce a very nice HTML document.

The command tigexp can be used to explain the results.

For example :

> $ /usr/sbin/tigexp pass014w

The listed login ID is disabled in some manner ('*' in passwd field, etc),
but the login shell for the login ID is a valid shell (from /etc/shells
or the system equivalent).  A valid shell can potentially enable the
login ID to continue to be used.  The login shell should be changed to
something that doesn't exist, or to something like /bin/false.

If you are not willing to read / learn, probably just remove tiger.

Other then that, things look fine as long as you are running the servers listed in the output.

---

