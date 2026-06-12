---
title: "Ubuntu Server 15.10 issues with SSHFS connections - freezing"
date: 2015-12-29
forum: Server Platforms
---

### Post by Berduchwal on 2015-12-29
Hi 

My set up:
```
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily

```

```
top - 14:15:59 up 22:04,  2 users,  load average: 0.00, 0.01, 0.05
Tasks: 135 total,   1 running, 134 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.1 us,  0.0 sy,  0.0 ni, 99.9 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:  16222332 total,   907708 used, 15314624 free,    66308 buffers
KiB Swap: 16559612 total,        0 used, 16559612 free.   619296 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                    
    1 root      20   0   37700   5700   3872 S   0.0  0.0   0:03.33 systemd                                                                    
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd                                                                   
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.00 ksoftirqd/0                                                                
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0H                                                               
    7 root      20   0       0      0      0 S   0.0  0.0   0:05.90 rcu_sched                                                                  
    8 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh                                                                     
    9 root      20   0       0      0      0 S   0.0  0.0   0:04.45 rcuos/0                                                                    
   10 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/0                                                                    
   11 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 migration/0                                                                
   12 root      rt   0       0      0      0 S   0.0  0.0   0:00.41 watchdog/0                                                                 
   13 root      rt   0       0      0      0 S   0.0  0.0   0:00.41 watchdog/1                                                                 
   14 root      rt   0       0      0      0 S   0.0  0.0   0:00.07 migration/1                                                                
   15 root      20   0       0      0      0 S   0.0  0.0   0:00.00 ksoftirqd/1                                                                
   16 root      20   0       0      0      0 S   0.0  0.0   0:00.12 kworker/1:0                                                                
   17 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/1:0H                                                               
   18 root      20   0       0      0      0 S   0.0  0.0   0:00.87 rcuos/1                                                                    
   19 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/1                                                                    
   20 root      rt   0       0      0      0 S   0.0  0.0   0:00.41 watchdog/2                                                                 
   21 root      rt   0       0      0      0 S   0.0  0.0   0:00.07 migration/2                                                                
   22 root      20   0       0      0      0 S   0.0  0.0   0:00.02 ksoftirqd/2                                                                
   24 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/2:0H                                                               
   25 root      20   0       0      0      0 S   0.0  0.0   0:01.99 rcuos/2                                                                    
   26 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/2                                                                    
   27 root      rt   0       0      0      0 S   0.0  0.0   0:00.41 watchdog/3                                                                 
   28 root      rt   0       0      0      0 S   0.0  0.0   0:00.06 migration/3                                                                
   29 root      20   0       0      0      0 S   0.0  0.0   0:00.00 ksoftirqd/3                                                                
   31 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/3:0H                                                               
   32 root      20   0       0      0      0 S   0.0  0.0   0:00.91 rcuos/3                                                                    
   33 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/3                                                                    
   34 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 khelper                                                                    
   35 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kdevtmpfs                                                                  
   36 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 netns                                                                      
   37 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 perf                                                                       
   38 root      20   0       0      0      0 S   0.0  0.0   0:00.02 khungtaskd
```

Server Specification:
Lenovo ThinkServer TS140 Xeon E3-1226 v3 3.3GHz Tower Server RAM 16 Gb HDD 1 Tb

I am connecting from 3 LAN PC via:
```
/etc/fstab 
username@ip:/home/username/Common /media/Common fuse.sshfs _netdev,auto,delay_connect,noatime,allow_other,idmap=user,IdentityFile=link,gid=1004 0 0

```

Systems are running Ubuntu 15.10 Desktop.

Both server and desktops are fully updated.

Server SSH config:
```
cat sshd_config 
# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
HostKey /etc/ssh/ssh_host_ed25519_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 1024

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin without-password
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

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes

```

Client SSH setup:
```
cat ssh_config 

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
    ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
#   ProxyCommand ssh -q -W %h:%p gateway.example.com
#   RekeyLimit 1G 1h
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

```

The problem is that if working on a spreadsheet which is say 0.5Mb screen sometimes (once every 30min or so) goes grey. I can switch to another application and it is fine just the spreadsheet freezes. Sometimes when I am browsing directories it does the same thing.

Any suggestion on what I could do to fix it?

---

### Post by MAFoElffen on 2015-12-30
You said 3 users. I'm thinking it is a file locking / concurrency issue... sshfs does not do file locking and does not allow concurrency.
> 
[ sshfs wiki ]
[COLOR=#252525][FONT=sans-serif]For distributed remote file systems with multiple users, protocols such as [/FONT][/COLOR][Apple Filing Protocol]("https://en.wikipedia.org/wiki/Apple_Filing_Protocol")[COLOR=#252525][FONT=sans-serif], [/FONT][/COLOR][Network File System]("https://en.wikipedia.org/wiki/Network_File_System_(protocol)")[COLOR=#252525][FONT=sans-serif] and [/FONT][/COLOR][Server Message Block]("https://en.wikipedia.org/wiki/Server_Message_Block")[COLOR=#252525][FONT=sans-serif] are more often used. SSHFS is an alternative to those protocols only in situations where users are confident that files and directories will not be targeted for writing by another user, at the same time.[/FONT][/COLOR]

Which with Fuse Filesystems is a known bug: 
[Issue 86: utility and limitations of SSHFS as a file system]("https://code.google.com/p/macfusion/issues/detail?id=86")

This limitation is not just with spreadsheets, but also with "Word" like word processing app's. The issue comes to light when when the application checks for sole control of a file by checking that the application has a file lock on the current file ... and the file lock is not present.

IN reality, is may be a limitation, but is not going to be fixed. There are other, more robust ways to do the same that are built to do that... sshfs is just a lite, basic facilty to do limited things... and not meant to be a fully featured facility.

---

### Post by Berduchwal on 2015-12-30
Thank you for your response.

It is not possible. Each fill will only be used by a single user there will be no concurrent access problems.

However I will try NFS to see if this solves the problem.

---

