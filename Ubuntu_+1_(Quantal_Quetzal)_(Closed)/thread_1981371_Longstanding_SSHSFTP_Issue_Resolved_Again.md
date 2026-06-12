---
title: "Longstanding SSH/SFTP Issue Resolved Again"
date: 2012-05-16
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by VinDSL on 2012-05-16
Really, this is a "Note To Self" post... but, it may help others.

I've had a longstanding issue connecting to remote servers via SSH/SFTP.  It just cropped up again in Ubu Quantal -- undoubtedly triggered by an OpenSSH upgrade.

The "fix" is simple, and works every time (for me) but it always takes me by surprise, when an upgrade, fresh install (or whatever) overwrites my OpenSSH daemon config file.  Then, I have to do a web search to refresh my memory. Soooo, let's give the search bots another post to chew on...  LoL!

**ERROR DIALOG**
```
"Error: ssh program unexpectedly exited"
```

**EDIT THE FOLLOWING**
```
sudo gedit /etc/ssh/sshd_config
```

**CHANGE "YES" TO "NO", ON THIS LINE, AND SAVE**
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
HostKey /etc/ssh/ssh_host_ecdsa_key
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

**[COLOR="DarkRed"]RSAAuthentication no[/COLOR]**
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

**PROBLEM SOLVED**

Thanks, for your indulgence.  Hope it helps others...

---

### Post by pressureman on 2012-05-16
I just want to add a couple that I've found to resolve frustrating issues in the past.

If you SSH to Solaris / OpenIndiana / SmartOS boxes, the following will avoid very long connect delays:

```

GSSAPIAuthentication no

```

And I recommend changing the following from its default 300 seconds if behind NAT gateways that may aggressively time out TCP sessions:

```

ServerAliveInterval 120

```

Note that you can specify these (and the changes mentioned in the original post) in ~/.ssh/config rather than editing the system-wide /etc/ssh/ssh_config.

And one final cool trick... if you use RSA/DSA/ECDSA keys to authenticate to boxes (eg. password-less login), and you want this to work when logging into a host behind a bastion host, add the following (shown here for a specific bastion host):

```

Host mybastion.example.com
  ForwardAgent yes

```

HTH.

---

