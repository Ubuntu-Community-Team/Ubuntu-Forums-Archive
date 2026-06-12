---
title: "ssh configuration problem"
date: 2012-01-10
forum: Server Platforms
---

### Post by tpi on 2012-01-10
Hi everybody, I have same problems whit ssh on my server...
I cannot start the ssh service, in fact if I run services --status-all I recieve [ - ]  ssh
If I run /etc/init.d/ssh start (or restart) I don't get any message and I don't know where to look to debug the problem, any suggestion? :confused:
I coudn't try the re-install of openssh and I hope you can help me find the configuration problem!

This is the messages I recieve if I run the command: ssh -v localhost
```
debug:SshAppCommon/sshappcommon.c:154/ssh_app_get_global_regex_context: Allocating global SshRegex context.
debug: SshConfig/sshconfig.c:2184/ssh2_parse_config: Unable to open /root/.ssh2/ssh2_config
debug: Connecting to localhost, port 22...
debug: Ssh2/ssh2.c:1956/main: Entering event loop.
ssh: FATAL: Connecting to localhost failed: Connection Refused

```

This is the messages I recieve if I run the command: /usr/bin/ssh -v localhost
```
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to localhost [::1] port 22.
debug1: connect to address ::1 port 22: Connection refused
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: connect to address 127.0.0.1 port 22: Connection refused
ssh: connect to host localhost port 22: Connection refused

```
I don't know from which package ssh2 comes from... :(

I hope you can help me debug where the problem is because I cannot understand why the service cannot strart!
Thank you in advance, Federica.

---

### Post by HugoSerrano on 2012-01-10
Hello.

Can you show us your sshd_config file?

Best Regards! :-)

---

### Post by SlugSlug on 2012-01-10
It maybe due to havind root logins disabled in sshd.conf




Unable to open /root/.ssh2/ssh2_config

---

### Post by tpi on 2012-01-10
Thank you for the answers.
I tried connecting using also the username, so ssh -v user@localhost but I keep on recieving the same identical messages as above :(

This is my /etc/ssh/sshd_config
```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes
```

Hope this helps,
thanks.
Federica

---

### Post by SlugSlug on 2012-01-10
I cnt see a fault in that 

whats in 
```
sudo iptales -L
``` 


have you tried reinstall?

sudo aptitude reinstall ssh

---

### Post by tpi on 2012-01-10
Thank you, this is the result of the command sudo iptables -L

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  dns.interbusiness.it  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  dns.interbusiness.it  anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             172.20.255.255      
DROP       all  --  base-address.mcast.net/8  anywhere            
DROP       all  --  anywhere             base-address.mcast.net/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  172.20.20.244        dns.interbusiness.it tcp dpt:domain 
ACCEPT     udp  --  172.20.20.244        dns.interbusiness.it udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  base-address.mcast.net/8  anywhere            
DROP       all  --  anywhere             base-address.mcast.net/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  net-MY-REMOTE-ADDRESS  anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:ftp-data:ftp 
ACCEPT     udp  --  anywhere             anywhere            udp dpts:20:fsp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:http-alt 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:http-alt 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:8765 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:8765 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:9090 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:9090 
ACCEPT     tcp  --  net-MY-REMOTE-ADDRESS  anywhere            tcp dpt:postgresql 
ACCEPT     udp  --  net-MY-REMOTE-ADDRESS  anywhere            udp dpt:postgresql 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere      
```

I tried to reinstall but I get some errors because the server runs Ubuntu 9, which is no more supported, so the package isn't found :(
Do you have any suggestion to re-try the installation?

I keep on not understanding why the service is never started...

---

### Post by SlugSlug on 2012-01-10
Sorry I don't know, are you unable to upgrade to 10.04?

---

### Post by HugoSerrano on 2012-01-10
You can always access to EOL repos.

> ## EOL upgrade sources.list 
# Required 
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME main restricted universe multiverse 
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-updates main restricted universe multiverse 
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-security main restricted universe multiverse 

# Optional #
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-backports main restricted universe multivers


---

### Post by tpi on 2012-01-10
Thank you so much!!! I didn't know there was this possibility, I added the repositories and run
```
sudo aptitude updated 
```
After that the packages could be found.
I cannot yet install the package because I have another problem with installation I couldn't solve before #-o 

I hope you can help me, because I see that everyone is suggesting me reinstallation...
The problem is I recieve this messages when running:
sudo aptitude reinstall ssh

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REINSTALLED:
  ssh 
The following partially installed packages will be configured:
  gadmin-proftpd install-info proftpd-basic 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 384 not upgraded.
Need to get 0B/1252B of archives. After unpacking 0B will be used.
Writing extended state information... Done
(Reading database ... 139145 files and directories currently installed.)
Preparing to replace ssh 1:5.1p1-6ubuntu2 (using .../ssh_1%3a5.1p1-6ubuntu2_all.deb) ...
Unpacking replacement ssh ...
Setting up install-info (4.13a.dfsg.1-4ubuntu1) ...
/usr/sbin/update-info-dir: line 23: 15881 Illegal instruction     cp $INFODIR/dir $INFODIR/dir.old
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 132
Setting up proftpd-basic (1.3.2-3) ...
Illegal instruction
dpkg: error processing proftpd-basic (--configure):
 subprocess installed post-installation script returned error exit status 132
dpkg: dependency problems prevent configuration of gadmin-proftpd:
 gadmin-proftpd depends on proftpd-basic; however:
  Package proftpd-basic is not configured yet.
dpkg: error processing gadmin-proftpd (--configure):
 dependency problems - leaving unconfigured
Setting up ssh (1:5.1p1-6ubuntu2) ...
No apport report written because the error message indicates its a followup error from a previous failure.

Errors were encountered while processing:
 install-info
 proftpd-basic
 gadmin-proftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up install-info (4.13a.dfsg.1-4ubuntu1) ...
/usr/sbin/update-info-dir: line 23: 15900 Illegal instruction     cp $INFODIR/dir $INFODIR/dir.old
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 132
Setting up proftpd-basic (1.3.2-3) ...
Illegal instruction
dpkg: error processing proftpd-basic (--configure):
 subprocess installed post-installation script returned error exit status 132
dpkg: dependency problems prevent configuration of gadmin-proftpd:
 gadmin-proftpd depends on proftpd-basic; however:
  Package proftpd-basic is not configured yet.
dpkg: error processing gadmin-proftpd (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 install-info
 proftpd-basic
 gadmin-proftpd
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
```

In fact I have proftpd installed but to me it results up and running...](*,)](*,)](*,)

---

### Post by tpi on 2012-01-11
I tried some other commands to solve the problem with installations:
sudo apt-get -f install
sudo dpkg --configure -a

Then I also tried
sudo apt-get build-dep proftpd-basic

But I always get this message
```
Illegal instruction
dpkg: error processing proftpd-basic (--configure):
 subprocess installed post-installation script returned error exit status 132
```:(
Is there a way to understand what '**exit status 132**' represents? I have no idea of what I can try... 

These are the lines about proftpd-basic package in my /var/lib/dpkg/status file:
```
Package: proftpd-basic
Status: install ok half-configured
Priority: optional
Section: net
Installed-Size: 2008
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Source: proftpd-dfsg
Version: 1.3.2-3
Replaces: proftpd (<< 1.3.2), proftpd-common
Provides: ftp-server, proftpd
Depends: netbase (>= 4.13), libacl1 (>= 2.2.11-1), libattr1 (>= 2.4.41-1), libc6 (>= 2.7), libcap2 (>= 2.10), libncurses5 (>= 5.6+20071006-3), libpam0g (>= 0.99.7.1), libssl0.9.8 (>= 0.9.8f-5), libwrap0 (>= 7.6-4~), debconf (>= 0.5.00), adduser, ucf (>= 0.30), debianutils (>= 1.21.0), libpam-runtime (>= 0.76-13.1), sed (>= 4.1.5), openbsd-inetd | inet-superserver
Suggests: proftpd-doc, openssl, proftpd-mod-mysql, proftpd-mod-pgsql, proftpd-mod-ldap, proftpd-mod-odbc, proftpd-mod-sqlite
Conflicts: ftp-server, proftpd (<< 1.3.2), proftpd-common
Conffiles:
 /etc/init.d/proftpd 199fa35e373fc85b3ca799add1c61304
 /etc/cron.monthly/proftpd-basic 1dd568ea4d5b91ec508ac8bd855981fa
 /etc/default/proftpd c4ecf33e946d6459aa1d8d768e120b74
 /etc/pam.d/proftpd cf7ad13f603c0e7a7026c95075fc2840
 /etc/logrotate.d/proftpd-basic 444cc59b6d0775dcf25248dbfd7c5c37
 /etc/ftpusers 839f3157aad792bafbbdcd932a95a345
Description: Versatile, virtual-hosting FTP daemon - binaries
 ProFTPd is a powerful replacement for wu-ftpd. This File Transfer Protocol
 daemon supports hidden directories, virtual hosts, and per-directory
 ".ftpaccess" files. It uses a single main configuration file, with a
 syntax similar to Apache.
 .
 Because of the advanced design, anonymous-FTP directories can have
 an arbitrary internal structure (bin, lib, etc, and special files are
 not needed). Advanced features such as multiple password files and
 upload/download ratios are also supported.
 .
 This package contains the daemon and all main modules used for
 common configurations. If you need database-centric authentication
 install the suitable proftpd-mod suggested package.
Original-Maintainer: Francesco Paolo Lovergine <frankie@debian.org>
Homepage: http://www.proftpd.org/
```It isn't the only package with 'Conflicts' paragraph; could it be that the problem is linked to this?


```
Package: install-info
Status: install ok half-configured
Priority: important
Section: doc
Installed-Size: 252
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: texinfo
Version: 4.13a.dfsg.1-4ubuntu1
Config-Version: 4.13a.dfsg.1-4ubuntu1
Replaces: texinfo (<< 4.13a.dfsg.1-2)
Depends: libc6 (>= 2.4)
Conflicts: texinfo (<< 4.13a.dfsg.1-2)
Description: Manage installed documentation in info format
 The install-info utility creates the index of all installed documentation
 in info format and makes it available to info readers.
Original-Maintainer: Debian TeX maintainers <debian-tex-maint@lists.debian.org>
```
This above is the install-info package part...
Please help needed!!

Federica

---

### Post by HugoSerrano on 2012-01-11
Humm... don't know!

You saying that the ftp server it's running?
Try to do > dpkg-reconfigure <package>  in the bad packages.

---

### Post by tpi on 2012-01-11
Thank you for the answer...
I confirm you that ftp is up and running.

This are the result I get if I run dpkg-reconfigure command:

dpkg-reconfigure proftpd-basic
/usr/sbin/dpkg-reconfigure: proftpd-basic is broken or not fully installed

dpkg-reconfigure install-info
/usr/sbin/dpkg-reconfigure: install-info is broken or not fully installed


I tried to remove proftpd-basic and reinstall it:

```
sudo apt-get remove proftpd-basic 
sudo apt-get install proftpd-basic 
```

and everything keeps on working :confused::confused::confused:

So it seemed to me that these messages weren't so important; finally I tried:
```
sudo apt-get reinstall openssh-server
```
I'm quite sure I have tried it before, but not completely... #-o 

But finally now it works sshd is up and running and I can connect to the server :D

Of course I keep on getting the previous messages every time I use aptitude...

Thank you all!!!
Federica

---

### Post by HugoSerrano on 2012-01-11
Glad it's working :-)


Best regards!

---

