---
title: "SSH -- moving publickey folder question"
date: 2006-10-26
forum: Server Platforms
---

### Post by mj9980 on 2006-10-26
Hi Everyone,

I have publickey authentication setup for ssh with the publickey location being %h/.ssh/authorized_keys2.  This works fine and I can login in with Putty.

However, once I change the publickey location to somewhere else outside of the above location (like /etc/ssh/publickeys/) I get the following message "Server refused our key."  I thought this may have to do with strict modes so I turned that off, but still the same message.

Just wondering how I would go about moving the publickey location and not get this message.

sshd_config file:
```

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 2222
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
LogLevel DEBUG2

# Authentication:
LoginGraceTime 120
PermitRootLogin no 
StrictModes no

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys2
#AuthorizedKeysFile /usr/NX/home/nx/.ssh/authorized_keys2
AuthorizedKeysFile /etc/ssh/publickeys/authorized_keys2
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
PasswordAuthentication yes

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
KeepAlive yes
#UseLogin no
#MaxStartups 10:30:60
#Banner /etc/issue.net

AllowUsers nx mj0000

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*
#Subsystem sftp /usr/lib/openssh/sftp-server
#UsePAM yes

```

Thanks in advance for your time,

Mike

---

### Post by magicfab on 2006-10-27
symlink to the file instead ?

---

### Post by mj9980 on 2006-10-28
Thanks for the help! I will go this route when I get a chance to play with the computer again.

Thanks,
Mike

---

