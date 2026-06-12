---
title: "Tunnel problems after reboot, please help"
date: 2019-12-26
forum: Ubuntu/Debian BASED
---

### Post by johantonissen on 2019-12-26
[FONT=Helvetica]Hi there,[/FONT]
[FONT=Helvetica]I’d like to ask a question regarding a problem i’m having. Last two days i’ve been setting up my rockpi 4 with armbian bionic 18 as a replacement server. I had everything configured correctly and working. I left the rock on over night and discovered this morning that i couldn’ t connect over vnc/rdp anymore.[/FONT]
[FONT=Helvetica]After a reboot i could connect to ssh but not over rdp or vnc. My vnc/RDP app jump desktop gives the following error: Could not create SSH tunnel. Please make sure tcp forwarding is enabled on the server. Details: Chanel open failure (connection failed).[/FONT]
[FONT=Helvetica]The weird thing is, i have not changed anything since the last time, it just doesn’t work anymore now so i dont know where to look to solve the issue.[/FONT]
[FONT=Helvetica]I have the following jump desktop settings:[/FONT]
[FONT=Helvetica]address: 127.0.0.1:3389 (port is forwared in the router and open in ufw)[/FONT]
[FONT=Helvetica]ssh tunnel: username@ip_address with private key (also tried username@local ip 192.168.2.150 with key. no effect)[/FONT]
[FONT=Helvetica](ssh is working so the keys or the adresses should not be the problem, tried the exact same keys and both ip as local ip for ssh)[/FONT]
[FONT=Helvetica]My sshd_config file is in the attatchment. note that i have set allowtcp forwarding to ‘yes’ as was requested in the error log of jump desktop.[/FONT]
[FONT=Helvetica]I’ve also tried re-enabling rdp in the armbian-config no effect[/FONT]
[FONT=Helvetica]I’ve also tried running vncserver mo effect[/FONT]
[FONT=Helvetica]I’ve hooked up the system to a monitor and it just normally boots to desktop as expected.[/FONT]
[FONT=Helvetica]Does anyone have some tips where i should start looking for this problem ? I have a hard time doing this since it happened without me interfering. I think i have to debug the tunnel since there the problem is occurring? But how should i do that?[/FONT]
[FONT=Helvetica]Thank you in advance.

```
[FONT=Verdana]sudo cat /etc/ssh/sshd_config[/FONT]
```[/FONT]```

#       $OpenBSD: sshd_config,v 1.101 2017/03/14 07:19:07 djm Exp $


# This is the sshd server system-wide configuration file.  See
# sshd_config(5) for more information.


# This sshd was compiled with PATH=/usr/bin:/bin:/usr/sbin:/sbin


# The strategy used for options in the default sshd_config shipped with
# OpenSSH is to specify options with their default value where
# possible, but leave them commented.  Uncommented options override the
# default value.


#Port 22
#AddressFamily any
#ListenAddress 0.0.0.0
#ListenAddress ::


#HostKey /etc/ssh/ssh_host_rsa_key
#HostKey /etc/ssh/ssh_host_ecdsa_key
#HostKey /etc/ssh/ssh_host_ed25519_key


# Ciphers and keying
#RekeyLimit default none


# Logging
#SyslogFacility AUTH
#LogLevel INFO


# Authentication:


#LoginGraceTime 2m
PermitRootLogin no
#StrictModes yes
#MaxAuthTries 6
#MaxSessions 10


PubkeyAuthentication yes


# Expect .ssh/authorized_keys2 to be disregarded by default in future.
AuthorizedKeysFile      .ssh/authorized_keys .ssh/authorized_keys2


#AuthorizedPrincipalsFile none


#AuthorizedKeysCommand none
#AuthorizedKeysCommandUser nobody


# For this to work you will also need host keys in /etc/ssh/ssh_known_hosts
#HostbasedAuthentication no
# Change to yes if you don't trust ~/.ssh/known_hosts for
# HostbasedAuthentication
#IgnoreUserKnownHosts no
# Don't read the user's ~/.rhosts and ~/.shosts files
#IgnoreRhosts yes


# To disable tunneled clear text passwords, change to no here!
PasswordAuthentication no
#PermitEmptyPasswords no


# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no


# Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes
#KerberosGetAFSToken no


# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes
#GSSAPIStrictAcceptorCheck yes
#GSSAPIKeyExchange no


# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin yes
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
AuthenticationMethods publickey keyboard-interactive 
UsePAM yes


#AllowAgentForwarding yes
AllowTcpForwarding yes
#GatewayPorts no
X11Forwarding yes
#X11DisplayOffset 10
#X11UseLocalhost yes
#PermitTTY yes
PrintMotd no
#PrintLastLog yes
#TCPKeepAlive yes
#UseLogin no
#PermitUserEnvironment no
#Compression delayed
#ClientAliveInterval 0
#ClientAliveCountMax 3
#UseDNS no
#PidFile /var/run/sshd.pid
#MaxStartups 10:30:100
#PermitTunnel yes
#ChrootDirectory none
#VersionAddendum none


# no default banner path
#Banner none


# Allow client to pass locale environment variables
AcceptEnv LANG LC_*


# override default of no subsystems
Subsystem       sftp    /usr/lib/openssh/sftp-server


# Example of overriding settings on a per-user basis
#Match User anoncvs
#       X11Forwarding no
#       AllowTcpForwarding no
#       PermitTTY no
[FONT=Helvetica][FONT=Verdana]#       ForceCommand cvs server[/FONT][/FONT]
```[FONT=Helvetica]
[/FONT]

---

### Post by howefield on 2019-12-26
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

