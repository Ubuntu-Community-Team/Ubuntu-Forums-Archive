---
title: "SSH Error: Permission denied (publickey)"
date: 2010-08-10
forum: Server Platforms
---

### Post by Jason Cook on 2010-08-10
I want to use SSH to connect to my desktop. I have used Ubuntu 10.10's encryption to encrypt my home folder (thus encrypting my .ssh folder). This means that the OpenSSH doesn't have access to my .ssh folder. When I try to log into SSH before logging in on the local machine I get the following error:
```

jason@ONONWARA:~$ ssh jason@192.168.1.152
Ubuntu 10.04.1 LTS
NIHATI
Permission denied (publickey).

```

If I log onto the machine, then use SSH it works fine.

I want to use key based login, so pleased don't suggest using a password. One way to get around this error would be use a different authorized_keys file, but I don't know of a way to do this.

This is the contents of my sshd_config file:
```

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
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile /home/jason/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
#HostbasedAuthentication yes
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
PasswordAuthentication no

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
Banner /etc/issue.net

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
UsePAM no

#Allow "jason" to connect
AllowUsers jason

#Disallow "kids, root" to connect
DenyUsers kids root

```

---

### Post by cdenley on 2010-08-10
> **Jason Cook said:**
> 
One way to get around this error would be use a different authorized_keys file, but I don't know of a way to do this.


```

man sshd_config

```
> 
**AuthorizedKeysFile**
             Specifies the file that contains the public keys that can be used
             for user authentication.  AuthorizedKeysFile may contain tokens
             of the form %T which are substituted during connection setup.
             The following tokens are defined: %% is replaced by a literal
             '%', %h is replaced by the home directory of the user being
             authenticated, and %u is replaced by the username of that user.
             After expansion, AuthorizedKeysFile is taken to be an absolute
             path or one relative to the user's home directory.  The default
             is “.ssh/authorized_keys”.


You can create the directory /etc/ssh/authorized_keys, then create a file with authorized keys named the same name as each user in that directory.
```

AuthorizedKeysFile /etc/ssh/authorized_keys/%u

```

---

### Post by Jason Cook on 2010-08-10
Thanks. I have it working now.

---

