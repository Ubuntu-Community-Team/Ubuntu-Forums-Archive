---
title: "Can't SSH into server remotely"
date: 2018-08-24
forum: Server Platforms
---

### Post by alanrodriguez on 2018-08-24
Hey everyone,

I just installed Ubuntu Server 18.04 LTS on a machine, and I'm able to SSH into it locally just fine. I set it up with DuckDNS, and I got an 'OK' message back, meaning it's working. I also forwarded port 22 on my routers.

However, when I try to SSH into my server remotely, either through my DuckDNS address or my external IP, the connection times out. I'm new to managing my own server, but I've worked with them plenty as a webdev. 

Here's what my sshd_config looks like: ```

#	$OpenBSD: sshd_config,v 1.101 2017/03/14 07:19:07 djm Exp $


# This is the sshd server system-wide configuration file.  See
# sshd_config(5) for more information.


# This sshd was compiled with PATH=/usr/bin:/bin:/usr/sbin:/sbin


# The strategy used for options in the default sshd_config shipped with
# OpenSSH is to specify options with their default value where
# possible, but leave them commented.  Uncommented options override the
# default value.


Port 22
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
#PermitRootLogin prohibit-password
#StrictModes yes
#MaxAuthTries 6
#MaxSessions 10


#PubkeyAuthentication yes


# Expect .ssh/authorized_keys2 to be disregarded by default in future.
#AuthorizedKeysFile	.ssh/authorized_keys .ssh/authorized_keys2


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
#PasswordAuthentication yes
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
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes


#AllowAgentForwarding yes
#AllowTcpForwarding yes
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
#PermitTunnel no
#ChrootDirectory none
#VersionAddendum none


# no default banner path
#Banner none


# Allow client to pass locale environment variables
AcceptEnv LANG LC_*


# override default of no subsystems
Subsystem	sftp	/usr/lib/openssh/sftp-server


# Example of overriding settings on a per-user basis
#Match User anoncvs
#	X11Forwarding no
#	AllowTcpForwarding no
#	PermitTTY no
#	ForceCommand cvs server



```

---

### Post by darkod on 2018-08-24
1. Does forwarding on your router automatically allow the traffic? Sometimes allowing port 22 in the router FW and port forwarding 22 are two separate things. Check out your router in case you need a FW rule too.

2. There is slight possibility that your ISP is blocking incoming port 22. Rare, but it might happen.

---

### Post by alanrodriguez on 2018-08-24
I've checked on [https://www.yougetsignal.com/tools/open-ports/](https://www.yougetsignal.com/tools/open-ports/) and it says port 22 is open.  

I'll try a different port number and see if it works.

---

### Post by alanrodriguez on 2018-08-24
I tried a different port number and forwarded them in my routers. I checked that site and it says that port number is open , but no luck accessing it from the DuckDNS address or public IP.

I don't think my routers need a rule, because the port for my media server is accessible remotely. &#129335;*&#9794;&#65039;

---

### Post by SeijiSensei on 2018-08-25
Do you see any entries in /var/log/syslog on the server?

Use "ssh -v user@host" to enable debugging on the client side.  You can use multiple v's to get more grungy details.

---

### Post by alanrodriguez on 2018-08-25
I tried logging in remotely a few times, but no entries in syslog. The DuckDNS script looks like it's working though. Here's the most recent page of syslog:

```

Aug 25 19:27:07 blackstar systemd[21900]: Listening on GnuPG cryptographic agent and passphrase cache (restricted).
Aug 25 19:27:07 blackstar systemd[21900]: Listening on GnuPG network certificate management daemon.
Aug 25 19:27:07 blackstar systemd[21900]: Listening on GnuPG cryptographic agent and passphrase cache (access for web b$Aug 25 19:27:07 blackstar systemd[21900]: Listening on GnuPG cryptographic agent and passphrase cache.
Aug 25 19:27:07 blackstar systemd[21900]: Listening on GnuPG cryptographic agent (ssh-agent emulation).
Aug 25 19:27:07 blackstar systemd[21900]: Reached target Paths.
Aug 25 19:27:07 blackstar systemd[21900]: Reached target Sockets.
Aug 25 19:27:07 blackstar systemd[21900]: Reached target Basic System.
Aug 25 19:27:07 blackstar systemd[21900]: Reached target Default.
Aug 25 19:27:07 blackstar systemd[21900]: Startup finished in 13ms.
Aug 25 19:27:07 blackstar systemd[1]: Started User Manager for UID 1000.
Aug 25 19:28:34 blackstar systemd[1]: Started Session 226 of user alan.
Aug 25 19:30:01 blackstar CRON[22011]: (alan) CMD (~/duckdns/duck.sh >/dev/null 2>&1)
Aug 25 19:35:01 blackstar CRON[22021]: (alan) CMD (~/duckdns/duck.sh >/dev/null 2>&1)

```


Here's what I see when I add -vvv:
```

OpenSSH_for_Windows_7.6p1, LibreSSL 2.6.4
debug3: Failed to open file:C:\\Users\\Alan/.ssh/config error:2
debug3: Failed to open file:C:\\ProgramData\\ssh/ssh_config error:2
debug2: resolving "username.duckdns.org" port 187
debug2: ssh_connect_direct: needpriv 0
debug1: Connecting to username.duckdns.org [IP.IP.IP.IP] port 187.
debug3: finish_connect - ERROR: async io completed with error: 10060, io:000001C6A7722260
debug1: connect to address IP.IP.IP.IP port 187: Connection timed out
ssh: connect to host username.duckdns.org port 187: Connection timed out

```

---

### Post by SeijiSensei on 2018-08-26
> debug3: Failed to open file:C:\\Users\\Alan/.ssh/config error:2
debug3: Failed to open file:C:\\ProgramData\\ssh/ssh_config error:2


Those are Windows file paths.  On Linux you probably want /home/Alan/.ssh.

This is a Linux server and a Linux client?  Or are you using Putty on a Windows machine as the client?

---

