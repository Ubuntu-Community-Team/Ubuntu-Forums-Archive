---
title: "ssh login problem"
date: 2006-10-09
forum: Server Platforms
---

### Post by mwerlberger on 2006-10-09
Hi!

I have a strange problem with ssh logins. I have a dedicated hetzner server and got the root account. Changed the password, added a user and restricted root logins via ssh. Everything still working great. Now i wanted to add an additional user, set a password and wanted to login via ssh but the server restricted my login. With the first Account it is still possible to login. Can you give me a hint where i can search for changes or sth like that, that more users can login.

There is no AllowUsers in my sshd_config that restricts user logins from other users then the first one created.

Thanks for advice.
Rgds,
 Manuel

---

### Post by wieman01 on 2006-10-09
Have you created a user account on your server in the first place? That done you need to update "sshd_config" accordingly.

---

### Post by mwerlberger on 2006-10-10
I'm sorry but i don't really unterstand what you mean. The first user account was created the same way as the second one. For the first one ssh login works, for the second it don't.

My /etc/ssh/sshd_config:
> 
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
#AuthorizedKeysFile     %h/.ssh/authorized_keys

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
KeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes


Regards,
 Manuel

---

### Post by wieman01 on 2006-10-10
So you created a second user on your Linux server on which SSH is running, right? What's the output when you try to log in with the mentioned user? Any error message?

---

### Post by mwerlberger on 2006-10-10
Ok i finally got the problem. There was a mistake in my /etc/pam.d/common-password in combination with cracklib...

thx for the help,
 manuel

---

### Post by Scrappy_D on 2006-10-10
Yes, using the same password for each user is not recommended ;)

---

### Post by mwerlberger on 2006-10-10
no i just forgot (?) to uncomment a line so that cracklib was working correct. so setting the password was ok but logging in with it wasn't.

---

