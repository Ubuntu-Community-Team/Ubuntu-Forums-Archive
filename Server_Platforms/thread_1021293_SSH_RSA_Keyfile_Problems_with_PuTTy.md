---
title: "SSH RSA Keyfile Problems with PuTTy"
date: 2008-12-25
forum: Server Platforms
---

### Post by crazedfred on 2008-12-25
Hello! I am trying to make the switch to hosting a server on Ubuntu, and I've hit a snag. I've read up on the [suggested SSH settings]("https://help.ubuntu.com/community/AdvancedOpenSSH") and I'm trying to set up a SSH with RSA keyfiles, following those directions.

I've hit the same problem as [this guy]("http://ubuntuforums.org/showthread.php?t=887277"), I get the error "Server refused our key" when I try to use PuTTy with my keyfile.

Steps I took:
1) Used "ssh-keygen -t rsa" to create the keyfiles
2) Copied the "/home/USER/.ssh/id_rsa" file over to Windows
3) Used the tool puttygen.exe to convert the private key to the proper format
4) Ran these commands as suggested:
```
$ chmod go-w ~/
$ chmod 700 ~/.ssh
$ chmod 600 ~/.ssh/authorized_keys
```
**HOWEVER, that last command fails because /.ssh/authorized_keys folder does not exist**! I'm guessing this is why I can't use the dang key, but I havn't used Ubuntu enough to be sure.
5) Used [these instructions]("http://www.electrictoolbox.com/putty-rsa-dsa-keys/") to SSH with the keyfile I converted
6) Fails with "Server refused our key"

Here is my /etc/sshd_config file:
```
# Package generated configuration file
# See the sshd(8) manpage for details

#CHANGES I HAVE MADE TO THIS FILE
#BASED ON RECOMMENDATIONS FROM https://help.ubuntu.com/community/StricterDefaults
#AND https://help.ubuntu.com/community/AdvancedOpenSSH
#Changed PermitRootLogin from yes to no
#Changed LoginGraceTime from 120 to 30
#Uncommented "Banner /etc/issue.net" and customized that banner file
#Changed LogLevel from INFO to VERBOSE
#Turned off passwords, turned on keyfiles

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
LogLevel VERBOSE

# Authentication:
LoginGraceTime 30
PermitRootLogin no
StrictModes yes

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

UsePAM yes
```

Please let me know if I haven't made my problem clear or if you need more information. Thanks in advance! :)

---

### Post by TestDummy! on 2008-12-25
The ~/.ssh folder and authorized_keys have to be manually created.
You already appear to have the folder. You still have to make the file yourself, and place your public key into it.

It won't accept your private key if it doesn't have the matching public key in ~/.ssh/authorized_keys

As the other thread recommends, don't forget to reload your SSH configuration after doing this: **sudo /etc/init.d/ssh reload**

---

