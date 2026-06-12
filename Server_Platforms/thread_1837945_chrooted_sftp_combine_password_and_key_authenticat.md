---
title: "chrooted sftp combine password and key authentication"
date: 2011-09-02
forum: Server Platforms
---

### Post by Frozen Forest on 2011-09-02
Trying to setup a chrooted sftp server where those user that are in the group sftponly can use password authentication, while I as admin will use key based authentication. Is this even possible? using Ubuntu Server 10.04 as OS for the server.


Setup for sftponly group, not working make it impossible to login as admin
[php]
Match group sftponly 
ChrootDirectory /home/sftp 
X11Forwarding no 
AllowTcpForwarding no 
ForceCommand internal-sftp 
PasswordAuthentication yes
[/php]Basic setup
[php]
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
PasswordAuthentication no
[/php]

---

