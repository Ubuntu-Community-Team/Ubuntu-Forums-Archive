---
title: "SFTP Server Help"
date: 2011-07-06
forum: Server Platforms
---

### Post by khenning on 2011-07-06
Hi, I'm new around here and pretty new to ubuntu and linux in general.  I need some help with an sftp server.  I set it up using openssh and it worked fine for a few months.  Then recently we experienced a power outage.  Now the server will boot fine, all users can login locally, but when they try to login remotely they enter their user info and then are denied with some generic network error.  Again, being a noob at this I tried to trouble shoot this a little bit but I'm not quite sure what to look for.  I believe the ssh service is running but I don't know what else to look for.  Any help you can provide is greatly appreciated.  Thanks!

---

### Post by khenning on 2011-07-06
Any ideas of anything I could check?  Again, any help is greatly appreciated.

---

### Post by perspectoff on 2011-07-06
Proftp or vsftp

---

### Post by rubylaser on 2011-07-06
What is the "generic network error" and what do the logs show?  Also what do you have in this file?
```
cat /etc/ssh/sshd_config
```

Is ssh running?
```
ps aux | grep ssh
```

If so, can you ssh on the localhost to itself and see if that works?

---

### Post by khenning on 2011-07-06
I can ssh on to the server from my windows desktop using secureCRT.  

Here are the contents of the /etc/ssh/sshd_config file:

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

Match group sftponly
ChrootDirectory /home/%u
X11Forwarding no
AllowTcpForwarding no
ForceCommand internal-sftp

---

### Post by khenning on 2011-07-06
And when trying to connect using Filezilla I get this error after it sends the user and password info:

Error:    Network error: Software caused connection abort
Error:    Could not connect to server

---

### Post by Lars Noodén on 2011-07-06
What about another SFTP client besides Filezilla?  Does it give the same error message?

---

### Post by perspectoff on 2011-07-06
sudo /etc/init.d/networking restart

(Power outages corrupt my Network Manager cache every time).

---

### Post by khenning on 2011-07-06
Here's the error from the ws_ftp client:


SSH-2.0-OpenSSH_5.5p1 Debian-4ubuntu5
  client -> 3des
  server -> 3des
  07:3b:f9:e1:b2:a5:35:1e:72:94:46:19:16:6d:ee:39
  ssh-rsa
  Sending password
  SFTP connection error
  Waiting 12 of 60 seconds for retry #1...
  

And sudo /etc/init.d/networking restart didn't work.

Keep the suggestions coming.  I appreciate them.

---

### Post by khenning on 2011-07-06
I added a new user and that user can connect.  So something must be corrupt with the old usernames?  I tried resetting the password on one of the users that can't connect and they still can't connect.  Any ideas of what I might try before actually deleting the current users and recreating them?  I'd like to avoid that if possible.  Thanks.

---

### Post by Cyked on 2011-07-06
What shows up in auth.log after you have the failed connection?

---

### Post by khenning on 2011-07-06
Jul  6 14:11:09 RBSFTP sshd[5906]: Accepted password for cgrmc from 192.168.1.119 port 1031 ssh2
Jul  6 14:11:09 RBSFTP sshd[5906]: pam_unix(sshd:session): session opened for user cgrmc by (uid=0)
Jul  6 14:11:09 RBSFTP sshd[5975]: fatal: bad ownership or modes for chroot directory "/home/cgrmc"
Jul  6 14:11:09 RBSFTP sshd[5906]: pam_unix(sshd:session): session closed for user cgrmc

---

### Post by Cyked on 2011-07-06
Did you set this up as a sftp jail?

Have you check permissions on that user's home directory?

---

### Post by khenning on 2011-07-06
> **Cyked said:**
> Did you set this up as a sftp jail?

Have you check permissions on that user's home directory?

I'm pretty sure I did not set this up as a sftp jail.  The permissions on that user's home directory look fine too.

---

### Post by khenning on 2011-07-06
I googled around and found that I need to have root as an owner on the home directory.  Once I did that the user was able to login.

---

### Post by Cyked on 2011-07-06
Good deal!

---

### Post by khenning on 2011-07-06
It allows them to login, but they can't transfer to or from their home directory because of lack of permissions.  If I give ownership back to the user, they can no longer login again.  I'll be back tomorrow to look into this more. Any suggestions are appreciated.

---

