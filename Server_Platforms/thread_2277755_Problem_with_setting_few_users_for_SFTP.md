---
title: "Problem with setting few users for SFTP"
date: 2015-05-11
forum: Server Platforms
---

### Post by mxdarvin on 2015-05-11
Hello guys,
I am trying to set up SFTP for multiple users using multiple accounts which are not root accounts. I want to use multiple public/private keys. Currently I am running Ubuntu Server 14.04 on AWS EC2 instance. I have created another user, in the home directory of that user I have created .ssh folder which is hidden and authorized_keys file to store a public key for that user. I did not change any setting in sshd_config file. When I am logging with my standard user which is: ubuntu - for AWS EC2 instance, the connection is accepted however when I am trying to connect to the server using other username with other private key for that user the connection is refused. I have modified the authorized_keys file to store a correct public key for that user. Do I have to somehow edit sshd_config file to allow multiple users with different .ppk to be able to connect? Also those other users have only access to the /var/ww directory and this will be their home directory, nothing else... Also those users will be in a group sftp, I have add those users to that group already...

Here is the configuration file sshd_config:
```
# Package generated configuration file
# See the sshd_config(5) manpage for details

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
HostKey /etc/ssh/ssh_host_ed25519_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 1024

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin without-password
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile    %h/.ssh/authorized_keys

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

#Subsystem sftp /usr/lib/openssh/sftp-server
Subsystem sftp internal-sftp

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
Match group sftp
    ChrootDirectory /var/www
    X11Forwarding no
    AllowTcpForwarding no
    ForceCommand internatl-sftp


```

---

### Post by darkod on 2015-05-11
SSH is very strict with file permissions but when the .ssh folder and authorized_keys are created they receive standard permissions which ssh might not like.

Login with the new user using the password and try this ( the login should open its home folder by default):
```
chmod 700 .ssh
cd .ssh
chmod 600 authorized_keys
```

Log out and try logging in using the key and see if it worked.

---

### Post by mxdarvin on 2015-05-11
I have done that already  when I was doing the set up ;) Still it is not working :/

---

### Post by darkod on 2015-05-11
The file is owned by the user, not root right?

If the permissions are correct double check the key. How did you paste it? Note that text files created in windows are different so if you only copy/upload the file linux might not like this. Open a session to the remote machine, open the file with nano and paste the key value. If you used puttygen make sure to paste the openssh value from the puttygen window.

---

### Post by mxdarvin on 2015-05-11
All that steps are done ;) The public key was copy from putty generator and paste into the terminal window with open remote session to the server. The files are owned by the user...

Edit@
When I am trying to connect I am receiving error "Server refused our key", I am trying to log in a new user not a standard one, which is: ubuntu...

---

### Post by darkod on 2015-05-11
Post the content of that users home:
```
ls -al /home/username
ls -l /home/username/.ssh
```

Server refused the key is standard message for using wrong key or the files linux permissions. You are sure you are using the correct ppk for that key right?

---

### Post by mxdarvin on 2015-05-11
Yea, I am sure I am using the correct .ppk file... 


```

drwxr-xr-x 3 usrdev usrdev 4096 May 11 09:44 .
drwxr-xr-x 4 root   root   4096 May 11 09:42 ..
-rw-r--r-- 1 usrdev usrdev  220 May 11 09:42 .bash_logout
-rw-r--r-- 1 usrdev usrdev 3637 May 11 09:42 .bashrc
-rw-r--r-- 1 usrdev usrdev  675 May 11 09:42 .profile
drwx------ 2 usrdev usrdev 4096 May 11 09:46 .ssh


```

```

drwx------ 2 usrdev usrdev 4096 May 11 09:46 .
drwxr-xr-x 3 usrdev usrdev 4096 May 11 09:44 ..
-rwx------ 1 usrdev usrdev  381 May 11 09:49 authorized_keys


```

---

### Post by Lars Noodén on 2015-05-11
There's a misspelling in the server's configuration "ForceCommand interna**t**l-sftp" should be "ForceCommand internal-sftp" if there was no mistake in pasting.

---

### Post by tgalati4 on 2015-05-11
I would set up a local Ubuntu server machine and test multiple users with sftp.  You want to separate the permissions/ssh issue with AWS.  It's possible that it will work with a local setup but not with the AWS environment.  It's more work, but that is the only way to decouple the problem.  You can also test your group access scheme to make sure that works before migrating to the cloud.

---

### Post by mxdarvin on 2015-05-11
How to tweak that sshd_config set up to use a password authentication instead of a private key?

Edit@
I know it might be tricky to make a correct set up on AWS...

Edit2@
I have set a PasswordAuthentication yes for sshd_config for only SFTP group, but when I will provide password I am receiving error:  Software Caused Connection Abort, Authentication Failed

Edit3@
Ok guys, I have manage to fix that by configuring sshd_config to accept Password Authentication for the user of group sftp. That user will only have an access to /var/www directory - which is owned by root - and nothing else...

---

