---
title: "allowing root key-only access to ssh"
date: 2009-04-02
forum: Security
---

### Post by adante on 2009-04-02
I'm trying to enable root access to ssh via a key for backup purposes. I understand this is a bad idea but if someone can offer an alternative method of being able to run a dirvish/rsync backup of remote host I'd like to hear it.

Anyway in my sshd_config I have set "PermitRootLogin without-password"

I verified my /etc/pam.d/ssh does not disable root login.

I generated keys and put them in appropriate places. 

Originally when I tried to ssh, it would say reverse lookup failed. I added an entry to my /etc/hosts to fix that.

I restarted sshd but now when I try to ssh root@myhost, my /var/log/auth.log says:

> Apr  3 09:52:50 myhost sshd[5377]: ROOT LOGIN REFUSED FROM 59.167.212.65

What else do I need to be doing?

ssh -v root@myhost
```

root@pmserv:~# ssh -v  -p 50022 root@myhost
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to myhost [] port 50022.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/identity type -1
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-3ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-3ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '[myhost]:22' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:8
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/identity
debug1: Trying private key: /root/.ssh/id_rsa
debug1: read PEM private key done: type RSA
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /root/.ssh/id_dsa
debug1: Next authentication method: password
root@myhost's password:

```




/etc/pam.d/sshd
```
# PAM configuration for the Secure Shell service

# Read environment variables from /etc/environment and
# /etc/security/pam_env.conf.
auth       required     pam_env.so # [1]
# In Debian 4.0 (etch), locale-related environment variables were moved to
# /etc/default/locale, so read that as well.
auth       required     pam_env.so envfile=/etc/default/locale

# Standard Un*x authentication.
@include common-auth

# Disallow non-root logins when /etc/nologin exists.
account    required     pam_nologin.so

# Uncomment and edit /etc/security/access.conf if you need to set complex
# access limits that are hard to express in sshd_config.
# account  required     pam_access.so

# Standard Un*x authorization.
@include common-account

# Standard Un*x session setup and teardown.
@include common-session

# Print the message of the day upon successful login.
session    optional     pam_motd.so # [1]

# Print the status of the user's mailbox upon successful login.
session    optional     pam_mail.so standard noenv # [1]

# Set up user limits from /etc/security/limits.conf.
session    required     pam_limits.so

# Set up SELinux capabilities (need modified pam)
# session  required     pam_selinux.so multiple

# Standard Un*x password updating.
@include common-password

```


/etc/ssh/sshd_config
```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 50022
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
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

PermitRootLogin without-password


```

---

### Post by bodhi.zazen on 2009-04-02
Your sshd_config still says 

> # Authentication:[FONT=monospace]
[/FONT]LoginGraceTime 120[FONT=monospace]
[/FONT]**[COLOR=red]PermitRootLogin no[/COLOR]**[FONT=monospace]
[/FONT]StrictModes yesyou need to change that to

```

# Authentication:[FONT=monospace]
[/FONT]LoginGraceTime 120[FONT=monospace]
[/FONT][color=blue]**PermitRootLogin without-password**[/color][FONT=monospace]
[/FONT]StrictModes yes
```And remove the last line "PermitRootLogin without-password"

You can also configure you key to run a single command rather then give a shell.

although not exact, see this blog : [http://blog.bodhizazen.net/linux/svnssh/](http://blog.bodhizazen.net/linux/svnssh/)

Scroll down to the "Magic section" and add in your back up command.

---

### Post by adante on 2009-04-02
> **bodhi.zazen said:**
> Your sshd_config still says 

you need to change that to

```

# Authentication:[FONT=monospace]
[/FONT]LoginGraceTime 120[FONT=monospace]
[/FONT][color=blue]**PermitRootLogin without-password**[/color][FONT=monospace]
[/FONT]StrictModes yes
```And remove the last line "PermitRootLogin without-password"

You can also configure you key to run a single command rather then give a shell.

although not exact, see this blog : [http://blog.bodhizazen.net/linux/svnssh/](http://blog.bodhizazen.net/linux/svnssh/)

Scroll down to the "Magic section" and add in your back up command.

wowee.. just started using vim, I blame case insensitive search :)

thanks!

---

### Post by Murz on 2009-09-22
> **adante said:**
> I understand this is a bad idea but if someone can offer an alternative method of being able to run a dirvish/rsync backup of remote host I'd like to hear it.

You can run an rsync on the host locally from root and sync all data read locally by root to remote backup server via not-priveleged user. I think this is more secure that authorizing by root via keys.

---

### Post by Agent ME on 2009-09-23
> **Murz said:**
> You can run an rsync on the host locally from root and sync all data read locally by root to remote backup server via not-priveleged user. I think this is more secure that authorizing by root via keys.

This sounds like the best idea, but if it is completely necessary to run as root from a remote site, then I believe you could change the sudo config to allow the remote user to be in the admin group and not need to enter in the password again.

---

### Post by Lars Noodén on 2009-09-24
> **Agent ME said:**
> you could change the sudo config to allow the remote user to be in the admin group and not need to enter in the password again.

If it is only for that specific program with specific options, otherwise it ends up granting full access to everything.

---

### Post by toupeiro on 2009-09-24
If you really want to be paranoid (and I always suggest being somewhat paranoid when you start sharing keys) is to put a from= in front of the root key you are sharing, and put in the ip address, or fully qualified name of the machine.  This way, if your **private** key is ever compromised, the person won't be able to cause total chaos. (unless he or she has already gotten a root shell on your trusted root host.)  In any regard, its a good safety practice.  Hopefully you are keeping your keys nice and secure.

---

### Post by msallee on 2009-10-08
Have you looked at using rsnapshot? There is a method of using a non-root user, granting it sudo rights to only do rsync.

Here are some links:

[http://blog.innerewut.de/2005/06/03/follow-up-on-remote-filesystem-snapshots-with-rsnapshot]("http://blog.innerewut.de/2005/06/03/follow-up-on-remote-filesystem-snapshots-with-rsnapshot")

[http://osdir.com/ml/sysutils.backup.rsnapshot.general/2005-11/msg00047.html]("http://osdir.com/ml/sysutils.backup.rsnapshot.general/2005-11/msg00047.html")

[http://troy.jdmz.net/rsync/#ref2](http://troy.jdmz.net/rsync/#ref2)

Let me know if these don't piece it together clearly enough and I'll add more instructions.

MS

---

