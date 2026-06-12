---
title: "UFW Error on fresh 13.04 x86"
date: 2013-11-03
forum: Server Platforms
---

### Post by anpalcactus on 2013-11-03
This is happening on the very fresh ubuntu 13.04 x86 (even reinstalled once to be sure) on OpenVZ VPS with 2Gb ram (if this matters); this happened earlier on 12.04LTS though.
> 
:~# apt-get install ufw
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  rsyslog
The following NEW packages will be installed:
  ufw
0 upgraded, 1 newly installed, 0 to remove and 56 not upgraded.
Need to get 157 kB of archives.
After this operation, 731 kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main ufw all 0.33-0ubuntu3 [157 kB]
Fetched 157 kB in 0s (269 kB/s)
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76, <> line 1.)
debconf: falling back to frontend: Readline
Preconfiguring packages ...
Selecting previously unselected package ufw.
(Reading database ... 23463 files and directories currently installed.)
Unpacking ufw (from .../ufw_0.33-0ubuntu3_all.deb) ...
Processing triggers for man-db ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76.)
debconf: falling back to frontend: Readline
Setting up ufw (0.33-0ubuntu3) ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76.)
debconf: falling back to frontend: Readline


Creating config file /etc/ufw/before.rules with new version


Creating config file /etc/ufw/before6.rules with new version


Creating config file /etc/ufw/after.rules with new version


Creating config file /etc/ufw/after6.rules with new version
root@anp:~# ufw allow ssh
Rules updated
Rules updated (v6)
root@anp:~# ufw allow http
Rules updated
Rules updated (v6)
root@anp:~# ufw logging off
Logging disabled
root@anp:~# ufw enable
Command may disrupt existing ssh connections. Proceed with operation (y|n)? y
ERROR: problem running ufw-init
libkmod: ERROR ../libkmod/libkmod.c:505 kmod_lookup_alias_from_builtin_file: could not open builtin file '/lib/modules/2.6.32-042stab081.3/modules.builtin.bin'
FATAL: Module nf_conntrack_ftp not found.
libkmod: ERROR ../libkmod/libkmod.c:505 kmod_lookup_alias_from_builtin_file: could not open builtin file '/lib/modules/2.6.32-042stab081.3/modules.builtin.bin'
FATAL: Module nf_nat_ftp not found.
libkmod: ERROR ../libkmod/libkmod.c:505 kmod_lookup_alias_from_builtin_file: could not open builtin file '/lib/modules/2.6.32-042stab081.3/modules.builtin.bin'
FATAL: Module nf_conntrack_netbios_ns not found.
iptables-restore: line 69 failed
iptables-restore: line 30 failed
ip6tables-restore: line 4 failed
ip6tables-restore: line 65 failed
sysctl: permission denied on key 'net.ipv4.tcp_sack'


Problem running '/etc/ufw/before.rules'
Problem running '/etc/ufw/after.rules'
Problem running '/etc/ufw/before6.rules'


root@anp:~#



After this, I add default rule to allow outgoing connections and ufw will run (not each time but still...) but won't allow them outgoing connections anyway:
> 
root@anp:~# ufw default allow outgoing
Default outgoing policy changed to 'allow'
(be sure to update your rules accordingly)
root@anp:~# ufw enable
Command may disrupt existing ssh connections. Proceed with operation (y|n)? y
Firewall is active and enabled on system startup
root@anp:~# wget google.com
--2013-11-03 16:48:33--  [http://google.com/](http://google.com/)
Resolving google.com (google.com)... failed: Connection timed out.
wget: unable to resolve host address 'google.com'
root@anp:~# ufw disable
Firewall stopped and disabled on system startup
root@anp:~# wget google.com
--2013-11-03 16:51:19--  [http://google.com/](http://google.com/)
Resolving google.com (google.com)... 74.125.229.192, 74.125.229.197, 74.125.229.194, ...
Connecting to google.com (google.com)|74.125.229.192|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.google.com/](http://www.google.com/) [following]
--2013-11-03 16:51:19--  [http://www.google.com/](http://www.google.com/)
Resolving [www.google.com]("http://www.google.com") ([www.google.com]("http://www.google.com"))... 74.125.229.212, 74.125.229.211, 74.125.229.209, ...
Connecting to [www.google.com]("http://www.google.com") ([www.google.com)|74.125.229.212|:80]("http://www.google.com)|74.125.229.212|:80")... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: 'index.html'


    [ <=>                                   ] 20,673      --.-K/s   in 0.007s


2013-11-03 16:51:19 (2.63 MB/s) - 'index.html' saved [20673]


root@anp:~#

---

### Post by WesleyWex on 2014-04-08
I'm having the same issue, did you ever fix this?

---

