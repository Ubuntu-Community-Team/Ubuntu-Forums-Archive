---
title: "PAM Module &amp; SSH issue"
date: 2010-11-09
forum: Server Platforms
---

### Post by exiva on 2010-11-09
I'm trying to setup my new Yubikey to work on my Ubuntu server, bu first I'm testing on a VMWare image using Fusion.

I've been playing around with this for a few days now, and i can't figure out why the system kicks me off when I give it my regular unix login.

I've got the PAM module installed, and asking me for my yubikey ID. In the pam log it's passing the key off to the Yubico server, and marking it a success. 

```

[pam_yubico.c:parse_cfg(404)] called.
[pam_yubico.c:parse_cfg(405)] flags 1 argc 2
[pam_yubico.c:parse_cfg(407)] argv[0]=id=16
[pam_yubico.c:parse_cfg(407)] argv[1]=debug
[pam_yubico.c:parse_cfg(408)] id=16
[pam_yubico.c:parse_cfg(409)] key=(null)
[pam_yubico.c:parse_cfg(410)] debug=1
[pam_yubico.c:parse_cfg(411)] alwaysok=0
[pam_yubico.c:parse_cfg(412)] verbose_otp=0
[pam_yubico.c:parse_cfg(413)] try_first_pass=0
[pam_yubico.c:parse_cfg(414)] use_first_pass=0
[pam_yubico.c:parse_cfg(415)] authfile=(null)
[pam_yubico.c:parse_cfg(416)] ldapserver=(null)
[pam_yubico.c:parse_cfg(417)] ldap_uri=(null)
[pam_yubico.c:parse_cfg(418)] ldapdn=(null)
[pam_yubico.c:parse_cfg(419)] user_attr=(null)
[pam_yubico.c:parse_cfg(420)] yubi_attr=(null)
[pam_yubico.c:pam_sm_authenticate(452)] get user returned: exiva
[pam_yubico.c:pam_sm_authenticate(542)] conv returned: xyz
[pam_yubico.c:pam_sm_authenticate(558)] OTP: xyz ID: xyz
[pam_yubico.c:pam_sm_authenticate(583)] ykclient return value (0): Success
[pam_yubico.c:check_user_token(117)] Authorization line: exiva:xyz
[pam_yubico.c:check_user_token(121)] Matched user: exiva
[pam_yubico.c:check_user_token(125)] Authorization token: xyz
[pam_yubico.c:check_user_token(128)] Match user/token as exiva/xyz
[pam_yubico.c:pam_sm_authenticate(625)] done. [Success]
```

Once it asks me for my Yubikey ID, and says it's okay... it asks me for my regular unix password. This is where it goes downhill, I get thrown off the server and can't login.

```
Nov  7 06:18:18 ubuntu sshd[15762]: Accepted keyboard-interactive/pam for exiva from 192.168.1.35 port 54179 ssh2
Nov  7 06:18:18 ubuntu sshd[15762]: fatal: PAM: pam_setcred(): Authentication service cannot retrieve user credentials
```


I've edited the following files as such;

/etc/pam.d/sshd
```
# PAM configuration for the Secure Shell service

# YubiKey Configuration
auth   required   pam_yubico.so id=16 debug

# Read environment variables from /etc/environment and
# /etc/security/pam_env.conf.
auth       required     pam_env.so # [1]
# In Debian 4.0 (etch), locale-related environment variables were moved to
# /etc/default/locale, so read that as well.
auth       required     pam_env.so envfile=/etc/default/locale

# Standard Un*x authentication.
@include common-auth

# Disallow non-root logins when /etc/nologin exists.
account    required     pam_nologin.so

# Uncomment and edit /etc/security/access.conf if you need to set complex
# access limits that are hard to express in sshd_config.
# account  required     pam_access.so

# Standard Un*x authorization.
@include common-account

# Standard Un*x session setup and teardown.
@include common-session

# Print the message of the day upon successful login.
session    optional     pam_motd.so # [1]

# Print the status of the user's mailbox upon successful login.
session    optional     pam_mail.so standard noenv # [1]

# Set up user limits from /etc/security/limits.conf.
session    required     pam_limits.so

# Set up SELinux capabilities (need modified pam)
# session  required     pam_selinux.so multiple

# Standard Un*x password updating.
@include common-password
```

/etc/ssh/sshd_config
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
#AuthorizedKeysFile   %h/.ssh/authorized_keys

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
ChallengeResponseAuthentication yes

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

---

