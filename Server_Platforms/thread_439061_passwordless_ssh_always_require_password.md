---
title: "passwordless ssh always require password"
date: 2007-05-10
forum: Server Platforms
---

### Post by erasmo.da.rotterdam on 2007-05-10
I am unsuccessfully trying to create a passwordless ssh connection.
I have one local computer that must connect on a remote server without Xwindows things.
Everything I need and can use is a shell.

On my local computer:

```
# pwd
```
/root/.ssh

I generate dsa and rsa keys with empty passwords

```
# ssh-keygen -t dsa
```
```
Generating public/private dsa key pair.
Enter file in which to save the key (/root/.ssh/id_dsa): test_dsa
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in test_dsa.
Your public key has been saved in test_dsa.pub.
The key fingerprint is:
3a:6d:5c:6d:ee:69:f8:71:15:01:b2:73:60:41:91:dc root@mypc
```

```
# ssh-keygen -t rsa
```
```
Generating public/private rsa key pair.
Enter file in which to save the key (/root/.ssh/id_rsa): test_rsa
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in test_rsa.
Your public key has been saved in test_rsa.pub.
The key fingerprint is:
a1:fd:9c:4c:33:49:46:6b:87:76:57:1c:a3:c8:57:f3 root@mypc
```

then I copy my test_dsa.pub and test_rsa.pub to a remote server

on the remote server:
inside /root/.ssh/

```
#cat test_rsa.pub >> authorized_keys
#cat test_dsa.pub >> authorized_keys
```

to be sure
```
#cp authorized_keys authorized_keys2
```

```
#more authorized_keys
ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAsKMpYJP1a0GHcdkawXLiWbWV5JyaaNeCr7gDGbb+hudXsj1uEujejRUeR3tF1fZP/szJQd6TaMrVrM/7bwW1wLad3GjLnRU3h5Er0
fSBI469FLevze+iazmmfgQLsncoMcap91llaUIbklLbIulDrratFvuqRV/QiYiSRQwCPR6D1bGMnngm3DWz7w/fQhHq310/TW0Tr0lDPs32KMgmTrP14eOyAeynm07RGqXiguBC
5tCgfMcxC/53HFx9YHh+2iQZpn1UseG9fzhQqFvy9D4iLtyGPrMasked4VhxsY2+DIOLuhLjLSmbpNFtz8GRc7LVoDEASuBVN2VhkQ== root@mypc
ssh-dss AAAAB3NzaC1kc3MAAAEBALbDaA6T35kRN3aRy5DB3EfGPhxA4ddy4mtJCJpvkJZnEFi9djkQYMrHH2icWH3lEavZv98UU2G4yOIpqFvblFH0p2u+FT1LrGndEmrGiz/Kj
HMbEyDq9NVYnEe5CdjBL9OHRfSQhjKIhvwrU7aL7iACEQofVHiTUiSyEZwxoKLWz2f65/ATT/p73LStICBtyP1D2ilnJ94wxmk+qvJrj6bQRbLhWWAVX4+lTeOjoSiaDRn4/Zgd
PZwf8K5mMupK3LSAGmgpJ66I8BaMvjd6BschislBv/26ncmG4NERry1JMeO1EKXqSU0vJsk4DTIu8lOHxX6X/bC3HV7GR48ykAAAAVAIHAs+LpZkO/sYqgc8hCBhrO24VRAAABAHI
OMUWeKw0IZWwBHySUlJO2wjAa83J5hDz8dT1GjzBbqetXP5vqXK4S2rsajrY41Q3gprdKuMd92pi27WO239yY04C4fWAAVX6+BpnLhsKChxDmeL5aSW+rMYL600R5Ok8IpIhSxTjZ
R4uhPfQijPqb1O2cPMM05OO3H3adjVY/FrycuqcuMp3q3glHr3qzdRy2Fo5QIxuhqPkr7LnhAqjbFRVYq9wo5ecS7JBoepusXcP7pC+Jcc9UOwAxpXReyIjfhZ3reaDFpwIdspS
CnlOEF2EtLM+K28TQK8HL6kww/wbTN+Cl8it+yJkwca6e43YFHVqUb8haOuDG/f9IoAAAEAJCe5cPdyNMHxZIv7ZVb89d0LE5ySEn7dhEiCEr/5SRojZM/hK4qnC1TxWoGrua6bJR
ukYmkRRu8EHDii4gEiz1o2exVUwJQlwGH3tXPwNZFshQyIqdI16JyZeptM/KYL3ONkP6oiRTMusKoqjjSkyGy+/gjj+Zwo1YfXCvaQ26bmvsJ8pztD3KokVqHfh8O1yzzp6ABkI
MIq40UQhUstkZA5n3rTSqIbpdo20JM7rLm5/RR112g0HBDXTJZPBHsUdcJJmkUwNJoHuQm3YOmH9wXXbtGvLZci1cJU1xG7+AAaur8aW/gymXEcCCNwT2N44sDqoR1rvKnNK9YrWe
kA== root@mypc
```

I cancelled some random chars

then, always on the remote server

```
#exec ssh-agent bash
#echo $SSH_AGENT_PID
31268
#ssh-add
```

At this point on my local computer I try to connect.
ssh [email]root@IP.IP.IP.IP[/email]
...
ENTER PASSWORD:confused: 

Please, help...

---

### Post by Matt Yun on 2007-05-10
On your remote server, did you edit **/etc/ssh/sshd_config** to disable **PasswordAuthentication** (either comment the line out, or change it to no)

---

### Post by rich.bradshaw on 2007-05-10
Good job you cancelled the characters... lol


If you are using ubuntu, there is no root user, so you won't be able to log in as root...

Try doing same thing but as your normal user to check it works.

---

### Post by erasmo.da.rotterdam on 2007-05-10
> "On your remote server, did you edit /etc/ssh/sshd_config to disable PasswordAuthentication (either comment the line out, or change it to no)"

Of course.. not!
I tried and restarted ssh but nothing change. :( 

> "If you are using ubuntu, there is no root user, so you won't be able to log in as root..."

on that particular server root account is enabled, however I'll try to log in passwordless with another user

P.S. what's the meaning of this always present lol?!

---

### Post by erasmo.da.rotterdam on 2007-05-10
maybe it's time for my sshdconfig file

```
[SIZE="1"]#       $OpenBSD: sshd_config,v 1.69 2004/05/23 23:59:53 dtucker Exp $

# This is the sshd server system-wide configuration file.  See
# sshd_config(5) for more information.

# This sshd was compiled with PATH=/usr/bin:/bin:/usr/sbin:/sbin

# The strategy used for options in the default sshd_config shipped with
# OpenSSH is to specify options with their default value where
# possible, but leave them commented.  Uncommented options change a
# default value.

#Port 22
Protocol 2
#ListenAddress 0.0.0.0
#ListenAddress ::

# HostKey for protocol version 1
#HostKey /etc/ssh/ssh_host_key
# HostKeys for protocol version 2
#HostKey /etc/ssh/ssh_host_rsa_key
#HostKey /etc/ssh/ssh_host_dsa_key

# Lifetime and size of ephemeral version 1 server key
#KeyRegenerationInterval 1h
#ServerKeyBits 768

# Logging
#obsoletes QuietMode and FascistLogging
#SyslogFacility AUTH
#LogLevel INFO

# Authentication:

#LoginGraceTime 2m
#PermitRootLogin yes
#StrictModes yes
#MaxAuthTries 6

[COLOR="Red"]#RSAAuthentication yes
#PubkeyAuthentication yes
#AuthorizedKeysFile      .ssh/authorized_keys[/COLOR]

# For this to work you will also need host keys in /etc/ssh/ssh_known_hosts
#RhostsRSAAuthentication no
# similar for protocol version 2
#HostbasedAuthentication no
# Change to yes if you don't trust ~/.ssh/known_hosts for
# RhostsRSAAuthentication and HostbasedAuthentication
#IgnoreUserKnownHosts no
# Don't read the user's ~/.rhosts and ~/.shosts files
#IgnoreRhosts yes

# To disable tunneled clear text passwords, change to no here!
[COLOR="Red"]##PasswordAuthentication no
#PermitEmptyPasswords no[/COLOR]

# Change to no to disable s/key passwords
#ChallengeResponseAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes
#KerberosGetAFSToken no

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

# Set this to 'yes' to enable PAM authentication, account processing, 
# and session processing. If this is enabled, PAM authentication will 
# be allowed through the ChallengeResponseAuthentication mechanism. 
# Depending on your PAM configuration, this may bypass the setting of 
# PasswordAuthentication, PermitEmptyPasswords, and 
# "PermitRootLogin without-password". If you just want the PAM account and 
# session checks to run without PAM authentication, then enable this but set 
# ChallengeResponseAuthentication=no
[COLOR="Red"]UsePAM yes[/COLOR]

#AllowTcpForwarding yes
#GatewayPorts no
#X11Forwarding no
#X11DisplayOffset 10
#X11UseLocalhost yes
#PrintMotd yes
#PrintLastLog yes
#TCPKeepAlive yes
#UseLogin no
#UsePrivilegeSeparation yes
#PermitUserEnvironment no
#Compression yes
#ClientAliveInterval 0
ClientAliveInterval 60
ClientAliveCountMax 3
#UseDNS yes
#PidFile /var/run/sshd.pid
#MaxStartups 10

# no default banner path
#Banner /some/path

# override default of no subsystems
Subsystem       sftp    /usr/lib/misc/sftp-server
[/SIZE]
```

can somebody tell me what's wrong? I tried to uncomment 

```
#RSAAuthentication yes
#PubkeyAuthentication yes
#AuthorizedKeysFile      .ssh/authorized_keys
```

but after restarting ssh nothing changes

---

### Post by Matt Yun on 2007-05-10
Here's my /etc/ssh/sshd_config
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
PermitRootLogin yes
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
#PasswordAuthentication yes


# To change Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#AFSTokenPassing no
#KerberosTicketCleanup no

# Kerberos TGT Passing does only work with the AFS kaserver
#KerberosTgtPassing yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
KeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes
```

---

### Post by psusi on 2007-05-10
> **rich.bradshaw said:**
> 
If you are using ubuntu, there is no root user, so you won't be able to log in as root...

Try doing same thing but as your normal user to check it works.

There is ALWAYS a root user, Ubuntu just doesn't give it a password, which prevents most things from allowing it to log in.  You can happily login as root on a tty.  

As for the OP, you run ssh-agent on your LOCAL computer, not the server.  The purpose of ssh-agent is for you to enter your password when you start it, so it can load your private key ( which SHOULD have a password ), and then you don't have to enter it again.  At that point you run ssh to connect and it gets your private key from the ssh-agent.

---

