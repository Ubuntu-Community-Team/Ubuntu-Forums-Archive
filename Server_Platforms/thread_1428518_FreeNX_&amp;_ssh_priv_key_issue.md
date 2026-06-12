---
title: "FreeNX &amp; ssh priv key issue"
date: 2010-03-12
forum: Server Platforms
---

### Post by gottijr on 2010-03-12
ubuntu server 9.10 with xubuntu gui

I've succeded in making both work
  ssh with private key login
  freenx connection

  my actual config:

  sshd_config
 
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
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile	%h/.ssh/authorized_keys

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
PasswordAuthentication no

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

AllowTcpForwarding yes
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
AllowUsers nx obama
UsePAM yes

```

and node.config

```


ENABLE_USERMODE_AUTHENTICATION="1"

# This adds the passdb to the possible authentication methods
ENABLE_PASSDB_AUTHENTICATION="0"


```

  but than when i enter in the Xubuntu gui and open a terminal i get this screen

 ```


 HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.3.0)
NX> 105

 
```

  instead of what it was supposed to be : "obama@serverip", and can't run any command line from there.

  pls advice

p.s. 
 !doesn't matter if freenx is running in no machine key, or new custom key.

 !!if i change  "PasswordAuthentication no" (in sshd_config) to "yes" it works normal but than i don't get the secure ssh!

---

### Post by 2hot6ft2 on 2010-03-12
You left out an important part of your setup that will be essential for those that respond.
That being the FreeNX client is on windows.

---

### Post by gottijr on 2010-03-12
> **2hot6ft2 said:**
> You left out an important part of your setup that will be essential for those that respond.
That being the FreeNX client is on windows.

  thank you 2hot6ft2 

  yes freenx client is running on windows:)

---

### Post by gottijr on 2010-03-15
Still no advice or suggestions?

  still hope for an answer on this one:)

---

