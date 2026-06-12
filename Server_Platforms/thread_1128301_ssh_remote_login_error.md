---
title: "ssh remote login error"
date: 2009-04-17
forum: Server Platforms
---

### Post by loskobosko on 2009-04-17
Hi everyone.
I've just deployed a standard Ubuntu 8.04 server virtual machine. I can ping and reach that machine.

The problem is with SSL.

As soon as standard install was done, I could ssh localhost and everything worked fine.

However, if I try to connect to ssh from a remote host, I get "access denied".

I turned on verbose logging for sshd, so I came up with this: 

```

pr 17 17:29:08 fntServer sshd[4992]: Connection from 127.0.0.1 port 36066
Apr 17 17:29:08 fntServer sshd[4992]: Failed none for davide from 127.0.0.1 port 36066 ssh2
Apr 17 17:29:14 fntServer sshd[4992]: pam_smbpass(sshd:auth): unrecognized option [missingok]
Apr 17 17:29:14 fntServer sshd[4992]: Accepted password for davide from 127.0.0.1 port 36066 ssh2
Apr 17 17:29:14 fntServer sshd[4994]: pam_unix(sshd:session): session opened for user davide by (uid=0)
Apr 17 17:29:17 fntServer sshd[4994]: Connection closed by 127.0.0.1
Apr 17 17:29:17 fntServer sshd[4994]: pam_unix(sshd:session): session closed for user davide
Apr 17 17:29:17 fntServer sshd[4994]: Closing connection to 127.0.0.1
Apr 17 17:30:42 fntServer sshd[5013]: Connection from 192.168.0.60 port 3169
Apr 17 17:30:47 fntServer sshd[5013]: Failed none for davide from 192.168.0.60 port 3169 ssh2
Apr 17 17:30:54 fntServer sshd[5013]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.0.60  user=davide
Apr 17 17:30:56 fntServer sshd[5013]: Failed password for davide from 192.168.0.60 port 3169 ssh2
Apr 17 17:39:01 fntServer CRON[5016]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 17 17:39:01 fntServer CRON[5016]: pam_unix(cron:session): session closed for user root
Apr 17 17:43:07 fntServer sshd[5023]: Connection from 192.168.0.60 port 3504
Apr 17 17:43:10 fntServer sshd[5023]: Failed none for davide from 192.168.0.60 port 3504 ssh2
Apr 17 17:43:12 fntServer sshd[5023]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.0.60  user=davide
Apr 17 17:43:14 fntServer sshd[5023]: Failed password for davide from 192.168.0.60 port 3504 ssh2
Apr 17 17:44:54 fntServer sudo: pam_smbpass(sudo:auth): unrecognized option [missingok]


```

I can connect via SSH and the password is right, but not from a remote host.

---

### Post by cdenley on 2009-04-17
What does /etc/ssh/sshd_config look like?

---

### Post by loskobosko on 2009-04-17
> **cdenley said:**
> What does /etc/ssh/sshd_config look like?

```

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
ListenAddress 0.0.0.0
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
LogLevel VERBOSE

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
#StrictModes yes

RSAAuthentication yes
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
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

AllowUsers davide


```

Looks like this.. (AllowUsers was added by me)

---

### Post by cdenley on 2009-04-17
Caps or num lock? Have you tried from a different remote host?

---

### Post by tcdyer on 2009-04-17
Have you tried removing "AllowUsers davide"?

My servers don't have an AllowUsers line. But I allow all users to connect via SSH...

Just my thoughts,
Tom

---

### Post by spiderbatdad on 2009-04-17
```
ListenAddress 0.0.0.0

```
```
#ListenAddress 0.0.0.0

```

```
PermitRootLogin yes
#StrictModes yes

``````
PermitRootLogin no
StrictModes yes

``````
AllowUsers <your users>
AllowGroups <your groups>
```

---

### Post by loskobosko on 2009-04-22
thank you everyone.. unfortunately the reccomendations for the sshd_config do not work.

I tried your advices, but they are bringing back the file to the default sshd_config I had before changing it a bit.

---

### Post by cdenley on 2009-04-22
> **loskobosko said:**
> thank you everyone.. unfortunately the reccomendations for the sshd_config do not work.

I tried your advices, but they are bringing back the file to the default sshd_config I had before changing it a bit.

And have you tried connecting from a different computer?

---

