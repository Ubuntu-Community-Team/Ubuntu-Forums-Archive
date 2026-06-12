---
title: "OpenSSH Public Key Authentication"
date: 2009-04-14
forum: Server Platforms
---

### Post by adri_ht_ on 2009-04-14
I swear to god that I got this working before, but somehow this time I'm stuck. I'm trying to set up RSA public key authentication w/o password in OpenSSH server. 

My RSA key is used currently in multiple locations so I don't think that's the problem. This is how my configuration file looks:



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
AuthorizedKeysFile "%h/.ssh/authorized_keys"

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

UsePAM yesMy rsa_id.pub is located in "/home/adm1n/.ssh/".
```
When I try to establish a session:


```
root# ssh adm1n@192.168.2.20
```

It fails (public key). The client has the private key (rsa_id) which works with other servers that I have running an ssh deamon.

Thanks

---

### Post by spiderbatdad on 2009-04-14
if you have physical access to the server, temporarily enable paswword login. Restart ssh.
Then from the client run the command ```
ssh-copy-id -i ~/.ssh/id_rsa.pub adm1n@192.168.2.20
```You should be asked for password by the server, then the key should be uploaded, and you will be logged in. Disable password auth and restart ssh. This is the method i use. I'm sure there are other ways.

---

### Post by Stupendoussteve on 2009-04-14
I see your problem, methinks...

> PermitRootLogin no


If you don't allow root to login, you can't login as root. ;)

EDIT: Never mind. Read root in the wrong part! I would go with the above post, it's possible your key is not installed.

That is a question though. Are you sure you have your private key installed in the root account on your local machine (not a normal user)? I don't think it's very common.

---

### Post by Yashiro on 2009-04-14
You have added your id_rsa to the authorized_keys file, right?

---

### Post by John Cheng on 2009-04-14
I am going to guess a small mistake was made somewhere, perhaps your private key is not set to "chmod 200" (not readable by anyone but the owner)? What is the output of?

```
ls -l /home/adm1n/.ssh/rsa_id.pub 
```

If my guess is off, then it is off the the DebugMobile

```
ssh -vv adm1n@192.168.2.20
```

A successful public key authentication attempt looks something like:

```
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/foo/.ssh/identity
debug1: Trying private key: /home/foo/.ssh/id_rsa
debug1: Offering public key: /home/foo/.ssh/id_dsa
debug1: Server accepts key: pkalg ssh-dss blen 434
debug1: read PEM private key done: type DSA
debug1: Authentication succeeded (publickey).

```

What is your output?

---

### Post by adri_ht_ on 2009-04-15
> **John Cheng said:**
> I am going to guess a small mistake was made somewhere, perhaps your private key is not set to "chmod 200" (not readable by anyone but the owner)? What is the output of?

```
ls -l /home/adm1n/.ssh/rsa_id.pub 
```

If my guess is off, then it is off the the DebugMobile

```
ssh -vv adm1n@192.168.2.20
```

A successful public key authentication attempt looks something like:

```
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/foo/.ssh/identity
debug1: Trying private key: /home/foo/.ssh/id_rsa
debug1: Offering public key: /home/foo/.ssh/id_dsa
debug1: Server accepts key: pkalg ssh-dss blen 434
debug1: read PEM private key done: type DSA
debug1: Authentication succeeded (publickey).

```

What is your output?

Thanks for your debugging approach. I think that somehow when I copied the public key to the server before something when wrong. I did it now through samba, and now I'm getting authenticated without problems.

Thanks to all!

---

