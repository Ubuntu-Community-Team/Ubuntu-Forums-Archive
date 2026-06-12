---
title: "SFTP Connects Without Key Pair?"
date: 2013-08-02
forum: Security
---

### Post by Michael_Woodruff on 2013-08-02
I have a remote server which I connect to via SSH.  I use putty and have my key files set (on client and server).  I can not connect without the correct key files.  

I recently decided I wanted to be able to use the SFTP feature.  So I looked in my sshd_config and it was enabled.  On my client, using FileZilla, I tried to connect without the key file.  I figured it would prompt me for it when it needed it.  However FileZilla connected without the keyfile.  How is this possible?

I tried this from my android phone using ES File, and it connected as well.  How do I stop this?  

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
#AuthorizedKeysFile     %h/.ssh/authorized_keys
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

---

### Post by newbie-user on 2013-08-02
In /etc/ssh/sshd_config uncomment the following line and change "yes" to "no":
```

#PasswordAuthentication yes

```
change to:
```

PasswordAuthentication no

```
Then restart ssh.

---

### Post by Michael_Woodruff on 2013-08-02
That worked!  Thanks.  But I still don't understand why putty had to have the keys to connect and filezilla didn't.  They are both using the ssh protocol, so should the connection be the same?  

I don't guess it really matters at his point, but just curious.

Thanks

---

### Post by CharlesA on 2013-08-02
Putty will use the keys if they exist and are the correct ones, before asking for the password.

---

