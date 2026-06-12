---
title: "SSH - Permission denied (publickey) - But same configuration"
date: 2007-10-16
forum: Server Platforms
---

### Post by daxumaming on 2007-10-16
Hi guys, here's my problem with SSH.

I only have one set of keys, both installed on my laptop and my desktop. I've had that key for 3 years now and I don't want to change them. Anyway, I copied my .ssh directory to my laptop then deleted the contents of known_hosts. I installed OpenSSH-server on both and copied /etc/ssh/sshd_config. The authorized_keys from the .ssh directory already has my public key on it (via cat id_rsa.pub >> .ssh/authorized_keys command). So, to be exact, everything  on my laptop's .ssh is a duplicate of my desktop's .ssh directory. And the /etc/ssh/sshd_config are also copied from my desktop to my laptop.

Now I can login from my desktop to my laptop via SSH, even with PasswordAuthentication and UsePAM set to no. However, I can't login from my laptop to my desktop via SSH with that same configuration. I keep on getting Permission denied (publickey,password) error. But I can login if I set PasswordAuthentication and UsePAM to yes. I don't have a firewall installed and sshd_config & .ssh files are duplicates (except, of course, the known_host file).

Is there something I need to do to make this work?

Here's my sshd_config:
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

UsePAM no


```

---

### Post by daxumaming on 2007-10-16
I finally got it working, it turned out, SSH is very particular about file permissions. I have to issue this command to get it working:

```
server$ chmod go-w ~/
server$ chmod 700 ~/.ssh
server$ chmod 600 ~/.ssh/authorized_keys
```

---

### Post by TheCowGod on 2008-03-23
Thanks so much, I have been trying to figure out why this wont work for 2 days!

---

