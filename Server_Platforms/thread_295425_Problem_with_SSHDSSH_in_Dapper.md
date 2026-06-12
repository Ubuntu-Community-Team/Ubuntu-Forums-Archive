---
title: "Problem with SSHD/SSH in Dapper"
date: 2006-11-08
forum: Server Platforms
---

### Post by mjojor on 2006-11-08
I have installed the OpenSSH package and sshd is up and running, but every time I try to remotely log in to my Dapper box, I get "Permission denied" although username and password are all correct. Here is my sshd_config:

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
Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

```

And here is the remote login attempt for *user* to *host.domain.com* (the entered password is correct every time):

```
root@host:~# ssh -v user@host.domain.com
OpenSSH_4.2p1 Debian-7ubuntu3.1, OpenSSL 0.9.8a 11 Oct 2005
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to host.domain.com [84.231.176.194] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/identity type -1
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_3.6p1
debug1: match: OpenSSH_3.6p1 pat OpenSSH_3.*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.2p1 Debian-7ubuntu3.1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client 3des-cbc hmac-sha1 none
debug1: kex: client->server 3des-cbc hmac-sha1 none
debug1: sending SSH2_MSG_KEXDH_INIT
debug1: expecting SSH2_MSG_KEXDH_REPLY
debug1: Host 'host.domain.com' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:3
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
debug1: Trying private key: /root/.ssh/id_dsa
debug1: Next authentication method: password
user@host.domain.com's password:
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
user@host.domain.com's password:
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
user@host.domain.com's password:
debug1: Authentications that can continue: publickey,password
debug1: No more authentication methods to try.
Permission denied (publickey,password).
root@host:~#
```

I don't understand where the problem is. Something is missing from the configuration? Does anyone have any ideas? Thanks in advance.

---

### Post by Joe_CoT on 2006-11-08
notice
```
#PasswordAuthentication yes
```

By default, sshd is configured to not allow password authentication; this is because public key authentication is much more secure, and because it means there's no method of access until you set it up.

Please take a look at the [OpenSSH Wiki page](https://help.ubuntu.com/community/AdvancedOpenSSH)

---

### Post by MJN on 2006-11-08
That's not true (don't believe everything you read in a wiki ;))- see **man sshd_config**:

```
**PasswordAuthentication** Specifies whether password authentication is allowed. The default is "yes"
```Mathew

---

### Post by mjojor on 2006-11-13
So that PasswordAuthentication issue should be ok. But I don't understand what else there could be wrong. Does anyone have any ideas?

---

### Post by tturrisi on 2006-11-13
If your network is using a router then setup port forwarding for ssh & the ip of the server.  On my net, I setup sshd to listen on 3022 instead of the usual 22, and port fporward 3022 to the server ip.  (this way, the kiddie probes for standard ports don't reveal that sshd exists and thus won't reveal a server exists at all when doing common port scanning)

---

### Post by MJN on 2006-11-13
There appears to be no issue with ports (and the forwarding thereof) given the following snippet from his log:
 
```
debug1: Connecting to host.domain.com [84.231.176.194] port 22.
debug1: Connection established.
```
 
Mathew

---

