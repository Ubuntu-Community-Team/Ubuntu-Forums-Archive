---
title: "SSH Pub/private key not able to login-Any Help Appriciated"
date: 2010-04-21
forum: Server Platforms
---

### Post by raja70 on 2010-04-21
I have made it work before but due to some other issues:((encripted home folder and other issues) I did a fresh install and a upgrade to 9.10 but came back to square one:rolleyes:.
This is what I did.
I did install SSH server/client
then
mkdir ~/.ssh
chmod 700 ~/.ssh
ssh-keygen -t rsa
went to the ~.ssh directory
 
echo id_rsa.pub >> /home/jameen70/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys 
 
then copied the file to desktop. With puttygen converted to ppk key. When I tried to login the server is refusing my key.
 
Here is my sshd_config
 
# Package generated configuration file
# See the sshd( manpage for details
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
LogLevel DEBUG
# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes
RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile %h/.ssh/authorized_keys
# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
IgnoreUserKnownHosts yes
# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no
# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
PermitEmptyPasswords no
# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no
# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication no
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
AllowUsers raja70
UsePAM no
 
 
Here is the permission info for /.ssh
drwx------ 2 raja70 raja70 4096 2010-04-21 00:32 .
drwxr-xr-x 4 raja70 raja70 4096 2010-04-21 01:04 ..
-rw------- 1 raja70 raja70 62 2010-04-21 00:36 authorized_keys
-rw------- 1 raja70 raja70 1743 2010-04-21 00:35 id_rsa
-rw-r--r-- 1 raja70 raja70 400 2010-04-21 00:35 id_rsa.pub
 
Here is auth.log entry
 
Apr 21 00:51:37 del002 sshd[1674]: Connection from 192.168.1.45 port 3096
Apr 21 00:51:37 del002 sshd[1674]: debug1: Client protocol version 2.0; client software version PuTTY_Release_0.60
Apr 21 00:51:37 del002 sshd[1674]: debug1: no match: PuTTY_Release_0.60
Apr 21 00:51:37 del002 sshd[1674]: debug1: Enabling compatibility mode for protocol 2.0
Apr 21 00:51:37 del002 sshd[1674]: debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2
Apr 21 00:52:03 del002 sshd[1674]: debug1: PAM: initializing for "raja70"
Apr 21 00:52:03 del002 sshd[1674]: debug1: PAM: setting PAM_RHOST to "192.168.1.45"
Apr 21 00:52:03 del002 sshd[1674]: debug1: PAM: setting PAM_TTY to "ssh"
Apr 21 00:52:04 del002 sshd[1674]: debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
Apr 21 00:52:04 del002 sshd[1674]: debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
Apr 21 00:52:04 del002 sshd[1674]: debug1: temporarily_use_uid: 1000/1000 (e=0/0)
Apr 21 00:52:04 del002 sshd[1674]: debug1: trying public key file /home/raja70/.ssh/authorized_keys
Apr 21 00:52:04 del002 sshd[1674]: debug1: fd 4 clearing O_NONBLOCK
Apr 21 00:52:04 del002 sshd[1674]: debug1: restore_uid: 0/0
Apr 21 00:52:04 del002 sshd[1674]: debug1: temporarily_use_uid: 1000/1000 (e=0/0)
Apr 21 00:52:04 del002 sshd[1674]: debug1: trying public key file /home/raja70/.ssh/authorized_keys
Apr 21 00:52:04 del002 sshd[1674]: debug1: fd 4 clearing O_NONBLOCK
Apr 21 00:52:04 del002 sshd[1674]: debug1: restore_uid: 0/0
Apr 21 00:52:04 del002 sshd[1674]: Failed publickey for raja70 from 192.168.1.45 port 3096 ssh2
 
 
I am banging my head for a day still I could not figure this out:confused:.
 
Any help Appriciated.
 
Thanks,
-Raja

---

### Post by richardjh on 2010-04-21
Check that you did these commands as you have typed them here:

```
mkdir ~/.ssh
chmod 700 ~/.ssh
ssh-keygen -t rsa
went to the ~.ssh directory
 
echo id_rsa.pub >> /home/jameen70/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
```


If so, you did 

```
echo id_rsa.pub >> /home/jameen70/.ssh/authorized_keys
```

and you should have done

```
cat id_rsa.pub >> /home/jameen70/.ssh/authorized_keys
```

You should edit the authorized_keys file and remove the line that says "id_rsa.pub".

Post back if you still get problems.

---

### Post by raja70 on 2010-04-21
> **richardjh said:**
> Check that you did these commands as you have typed them here:

```
mkdir ~/.ssh
chmod 700 ~/.ssh
ssh-keygen -t rsa
went to the ~.ssh directory
 
echo id_rsa.pub >> /home/jameen70/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
```


If so, you did 

```
echo id_rsa.pub >> /home/jameen70/.ssh/authorized_keys
```

and you should have done

```
cat id_rsa.pub >> /home/jameen70/.ssh/authorized_keys
```

You should edit the authorized_keys file and remove the line that says "id_rsa.pub".

Post back if you still get problems.
Thank you very much! that solved my issue.
Now I can proceed with installing others.
Thank you again. Appriciated.

---

