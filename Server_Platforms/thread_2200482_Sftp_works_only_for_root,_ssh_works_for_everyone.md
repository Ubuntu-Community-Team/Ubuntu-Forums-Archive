---
title: "Sftp works only for root, ssh works for everyone"
date: 2014-01-19
forum: Server Platforms
---

### Post by artur4 on 2014-01-19
Like in topic, sftp works only for root, all old users or new ones cannot login. Ssh works ok for everyone.

Part of the winscp log:
```
! 2014-01-19 21:51:54.569 Using username "someusername".. 2014-01-19 21:51:54.631 Prompt (7, SSH password, , &Password: )
. 2014-01-19 21:51:54.631 Using stored password.
. 2014-01-19 21:51:54.679 Sent password
. 2014-01-19 21:51:54.730 Access granted
. 2014-01-19 21:51:54.988 Opened channel for session
. 2014-01-19 21:51:55.050 Started a shell/command
. 2014-01-19 21:51:55.050 Server sent command exit status 1
. 2014-01-19 21:51:55.050 Disconnected: All channels closed
* 2014-01-19 21:51:55.090 (EFatal) Connection has been unexpectedly closed. Server sent command exit status 1.
* 2014-01-19 21:51:55.090 Authentication log (see session log for details):
* 2014-01-19 21:51:55.090 Using username "someusername".
* 2014-01-19 21:51:55.090 
* 2014-01-19 21:51:55.090 Authentication failed.
```

My sshd_config:
```
# Package generated configuration file# See the sshd_config(5) manpage for details


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


RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile    %h/.ssh/authorized_keys


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
# PasswordAuthentication yes


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

part of auth.log(little modified, i change my ip ;)):
```
Jan 19 21:51:52 someservername sshd[13355]: Accepted password for someusername from 666.666.666.666 port 6459 ssh2
Jan 19 21:51:52 ubuntuzutec sshd[13355]: pam_unix(sshd:session): session opened for user zutecsftp by (uid=0)
Jan 19 21:51:53 ubuntuzutec sshd[13483]: subsystem request for sftp by user someusername
Jan 19 21:51:53 ubuntuzutec sshd[13355]: pam_unix(sshd:session): session closed for user someusername

```

Also when i log as not root to ssh, I got this msg:
-bash: /etc/profile: Brak dost&#281;pu - (Brak dost&#281;pu means: No access)
Not sure if it's relevant to the problem.

So any suggestions what I can try to fix it, so every user with shell access will be able to also use sftp?

---

### Post by sandyd on 2014-01-19
Sounds like the permissions of /etc/profile have issues - can you post the output of
```
ls -l /etc/profile
```

Should look something like this
```

[sandyd@TinaFey ~]$ ls -l /etc/profile
-rw-r--r-- 1 root root 541 May 31  2013 /etc/profile
[sandyd@TinaFey ~]$ 
```

---

### Post by artur4 on 2014-01-20
Here you go:
```
root@ubuntuzutec:~# ls -l /etc/profile
-rw-r--r-- 1 root root 665 sty 17 11:00 /etc/profile
root@ubuntuzutec:~#
```

Edit:
It was /etc/. I mean permission for it was broken, it was
-rwxr----

I fixed it and sftp works for everyone, thank you for suggesting it. I owe you big one. I spended so much time on it and it was so simple. Thank you one more time.

---

