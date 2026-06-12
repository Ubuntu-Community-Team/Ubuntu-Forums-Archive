---
title: "disabilitare openssh password"
date: 2010-10-11
forum: Server Platforms
---

### Post by ethan82 on 2010-10-11
Salve stavo seguendo questa guida

[http://blog.gns3.net/2009/10/olive-juniper/4/](http://blog.gns3.net/2009/10/olive-juniper/4/)

praticamente ho difficoltà a far passare un file da ubuntu a freebsd emulato in qemu perchè ho installato su ubuntu openssh ,

e quando vado a dare da freebsd emulato il comando :


scp [email]user@10.0.2.2:~/Desktop/jinstall-8.5R1.14-domestic-signed.tgz[/email] /var/tmp

mi chiede la password e pure ho disabilitato il login sul file di configurazione di openssh vi mostro il file sshd_config

# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2

#Privilege Separation is turned on for security
UsePrivilegeSeparation no

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

RSAAuthentication no
PubkeyAuthentication no
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
PermitEmptyPasswords yes

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication no

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd no
#KerberosTicketCleanup no

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

come posso fare per togliere quella maledetta autenticazione quando do il comando scp ?

---

### Post by aspiredfang on 2010-10-11
Going on the basis of your title alone, in order to disable regular passwords and use keys only, uncomment the following:

```
# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication no
```You want it as:

```
# Change to no to disable tunnelled clear text passwords
 PasswordAuthentication no
```

Then all you need to do is restart the SSH agent by using
```
sudo /etc/init.d/ssh restart
```

---

### Post by msandoy on 2010-10-11
Just remember, alot of us in here do not understand Spanish/Portugese/Italian. At least I don't.

---

