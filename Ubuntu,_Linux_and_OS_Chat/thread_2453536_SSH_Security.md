---
title: "SSH Security"
date: 2020-11-12
forum: Ubuntu, Linux and OS Chat
---

### Post by Quarkrad on 2020-11-12
I've posted here as this is more of an advice question rather than specific - I might be wrong.  For the first time I've delved in the remote external SSH world, after some testing locally using a kvm machine.  I've installed openssh / x2go on my own and neighbours machines (both running 20.04) and because their ip changes daily set up a noip host address - all appears ok.  Now I'm having doubts about the security of the whole thing and if, through my naivety, my own pc and well as theirs, are compromised due to opening ports and/or not shutting down config  scripts.  Perhaps this is bit too far for me, there is a whole world of things to read and learn, which is great, but where to start?  It seems to me I should use another port rather than 22 and at the moment I've turned everything off in terms of our firewalls.  I'm reading things like config changes in sshd_config but at the same time I have basic/newbie questions such as proving to myself that I'm actually using the ssh keys on both machines to get the connection and if I've opened a barn door at the same time.  It is all there and appears to work but I'm nervous about opening the firewalls.  My purpose is to be able to have a remote Desktop connect to a number of machines (never simultaneously) to help people whose machines I've install ubuntu on.  (Been using Teamviewer to date). Any advice on whether this is too much for me or further reading matter would be appreciated.

---

### Post by TheFu on 2020-11-12
[https://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](https://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) is a little old, but I still follow it.

---

### Post by Quarkrad on 2020-11-14
Thank you. I have read your blog and will follow your advice.  As a beginner some of the sshd_config statements are confusing - e.g. PermitRootLogin prohibit-password  that has been changed from the yes/no option.  I have made what I think are the appropriate changes to sshd_config to reflect your advice - is it possible you could check for me please?  I have highlighted my changes, mainly unchecking, in blue.

```
#	$OpenBSD: sshd_config,v 1.103 2018/04/09 20:41:22 tj Exp $

# This is the sshd server system-wide configuration file.  See
# sshd_config(5) for more information.

# This sshd was compiled with PATH=/usr/bin:/bin:/usr/sbin:/sbin

# The strategy used for options in the default sshd_config shipped with
# OpenSSH is to specify options with their default value where
# possible, but leave them commented.  Uncommented options override the
# default value.

Include /etc/ssh/sshd_config.d/*.conf

[COLOR="#0000FF"]Port 53486[/COLOR]
#AddressFamily any
#ListenAddress 0.0.0.0
#ListenAddress ::

#HostKey /etc/ssh/ssh_host_rsa_key
#HostKey /etc/ssh/ssh_host_ecdsa_key
[COLOR="#0000FF"]HostKey /etc/ssh/ssh_host_ed25519_key[/COLOR]

# Ciphers and keying
#RekeyLimit default none

# Logging
#SyslogFacility AUTH
#LogLevel INFO

# Authentication:

#LoginGraceTime 2m
[COLOR="#0000FF"]PermitRootLogin prohibit-password[/COLOR]
#StrictModes yes
#MaxAuthTries 6
#MaxSessions 10

[COLOR="#0000FF"]PubkeyAuthentication yes[/COLOR]

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
[COLOR="#0000FF"]PasswordAuthentication no[/COLOR]
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
#PermitUserEnvironment no
#Compression delayed
#ClientAliveInterval 0
#ClientAliveCountMax 3
#UseDNS no
#PidFile /var/run/sshd.pid
#MaxStartups 10:30:100
```

Should the #LoginGraceTime 2m line be changed to something shorter?

---

### Post by ajgreeny on 2020-11-14
I personally have the logingracetime reduced to 20s I think but I'm not on that machine at the moment so can't be completely sure.

If it takes more than 20s to login something is definitely wrong!

---

### Post by TheFu on 2020-11-14
I would have the router handle the different port, but if the machine is at a VPS and has a public IP directly only, then you don't have much choice.

The PasswordAuthentication settings only allow ssh using a key regardless of the subnet. As long as you have console access easily available, that's fine.  But you may want to allow password logins from a few specific subnets so if there is an issue with an ssh-key/cert, you can get in remotely.  Use the **Match Address** sshd_config option for that. Make something like this the **last lines** in the file:
```
  Match Address 192.168.22.0/24,172.21.22.0/24,172.22.22.0/24,10.0.0.0/8
      PasswordAuthentication yes
```

If you don't actually use X11 forwarding, don't enable it.  I do, but most people don't.

I didn't look up all the settings. Sorry.

---

### Post by Quarkrad on 2020-11-14
@ajgreeny and @TheFu.  Thank you both for your help - I have it all working now. I use x2go so have X11 forwarding enabled and also in  x2go I have the **Try auto login(via SSH agent or default SSH key** option ticked. Out of interest: a pure ssh connect via the terminal connects me straight in with asking for a password, as expected.  When using the x2go client, and hopefully using the ssh connect with the key, the x2go client makes the connection but asks me the remote password.

---

### Post by TheFu on 2020-11-14
Does x2go need network X11 forwarding to work?
I haven't seen x2go ask for a password in years.  Is your ~/.ssh/config file setup for the remote system, userid, and port?

---

### Post by Quarkrad on 2020-11-15
I do not appear to have a config file in my ~/ssh folder:

```
dad@dadubuntu:~$ cd .ssh
dad@dadubuntu:~/.ssh$ ls
id_ed25519  id_ed25519.pub  known_hosts
dad@dadubuntu:~/.ssh$ 

```

There is reference to X11 forwarding in /etc/ssh/ssh_config and /etc/ssh/sshd_config.  I have editied sshd_config but not ssh_config

**ssh_config**
```

# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

In my sshd_config there seems to be a contradiction on lines 91 and 120 - is this saying I want X11 on and off?.  I'm not sure what lines 22 and 23 mean - is it that X11 is off but on when connect is made via keys (i.e. trusted)?   

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Include /etc/ssh/ssh_config.d/*.conf

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   IdentityFile ~/.ssh/id_ecdsa
#   IdentityFile ~/.ssh/id_ed25519
#   Port 22
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com
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
```

**sshd_config**

```
#	$OpenBSD: sshd_config,v 1.103 2018/04/09 20:41:22 tj Exp $

# This is the sshd server system-wide configuration file.  See
# sshd_config(5) for more information.

# This sshd was compiled with PATH=/usr/bin:/bin:/usr/sbin:/sbin

# The strategy used for options in the default sshd_config shipped with
# OpenSSH is to specify options with their default value where
# possible, but leave them commented.  Uncommented options override the
# default value.

Include /etc/ssh/sshd_config.d/*.conf

Port 53486
#AddressFamily any
#ListenAddress 0.0.0.0
#ListenAddress ::

#HostKey /etc/ssh/ssh_host_rsa_key
#HostKey /etc/ssh/ssh_host_ecdsa_key
HostKey /etc/ssh/ssh_host_ed25519_key

# Ciphers and keying
#RekeyLimit default none

# Logging
#SyslogFacility AUTH
#LogLevel INFO

# Authentication:

LoginGraceTime 20s
PermitRootLogin prohibit-password
#StrictModes yes
#MaxAuthTries 6
#MaxSessions 10

PubkeyAuthentication yes

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

I have just discovered (!!!!!!!) that ssh_config is for the Client and sshd_config is for the Server - in my scenario where I am always connecting to the remote hosts they are the Servers and I am the Client so I'm thinking ssh_config is my main concern.   Lines 23 and 24 might be contradictory - unless ForwardX!!Trusted is when a connection is made using keys.

---

