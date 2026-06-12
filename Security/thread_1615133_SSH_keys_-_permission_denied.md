---
title: "SSH keys - permission denied"
date: 2010-11-06
forum: Security
---

### Post by toypilot on 2010-11-06
After hours of going around in circles I have decided to post.

With loglevel set to DEBUG2, I get the following error.

```
Error: Could not open keyfile '/home/username/.ssh/authorized_keys/id_dsa.pub': Permission denied
```

I realize I probably shouldnt be specifying the actual file in the sshd_config, but without it I get the following error.

```
 User <username> authorized keys /home/<username>/.ssh/authorized_keys is not a regular file
```

I have tried 
```

chown -R <username>:<username> ~/.ssh
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys

```

And still recieve permission denied.

Basically I have generated the keys using sshkeygen and added the private key to puttygen to save in the putty format, before loading it into putty

The only thing that I can think of which might be affecting this is that I have played with the sshd_config file previously when doing some tests with postfix.

Here is the sshd_config as it stands. 

```

# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port <myport>
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
# LogLevel INFO
LogLevel DEBUG2

# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes
AllowUsers ttweb

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile      %h/.ssh/authorized_keys/id_dsa.pub

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
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes

```

And finally, here are the permissions on the directories

```
drwx------ 3 <username> <username> 4096 Nov  6 10:33 .ssh
drw------- 2 <username> <username> 4096 Nov  6 10:56 authorized_keys

and rw on the actual file..
```

All of this is running on ubuntu 10.4 btw

Help appreciated... thanks tp

---

### Post by holiday on 2010-11-06
Try again and then right away check the tail of /var/log/auth.log.

What's it say?

---

### Post by DirtyPC on 2010-11-06
try **sudo**

---

### Post by CharlesA on 2010-11-06
authorized_keys is just a file, not a directory, with the public key pasted into it.

It needs to be in ~/username/.ssh/

You should have a file named id_dsa.pub and id_dsa in ~/username/.ssh/

Also this:

```
AuthorizedKeysFile      %h/.ssh/authorized_keys/id_dsa.pub

```

Should say:

```
AuthorizedKeysFile      %h/.ssh/authorized_keys
```

---

### Post by toypilot on 2010-11-06
Thanks for your swift replies

CharlesA - thank you for taking the time to understand my issue, and leading me  straight to the solution! ;-)

much appreciated

---

### Post by CharlesA on 2010-11-06
If you got it working, don't forget to mark the thread as solved from the thread tools menu. :)

---

