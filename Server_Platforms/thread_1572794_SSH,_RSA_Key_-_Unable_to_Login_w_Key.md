---
title: "SSH, RSA Key - Unable to Login w/ Key"
date: 2010-09-11
forum: Server Platforms
---

### Post by RylosFan on 2010-09-11
Ok, I've looked up all the tutorials I could find on properly configuring OpenSSH for authentication with public keys.  Unless I'm thoroughly dense, I've followed every step to the letter and I still can't get this working.

My server is Karmic x64, desktop Lucid x64.

Here's my sshd_config file:

> 
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 2520
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

UsePAM no
RSAAuthentication yes


After trying it manually, I discovered a few people recommended copying the public key using ssh-copy-id, which to my understanding should ensure it's copied and permissions are set correctly (600) on authorized_keys.

Despite all this at every attempt to login I am confronted with:
> 
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /home/myuser/.ssh/config
debug1: Applying options for pandora
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to pandora [192.XXX.XX.XX] port 2520.
debug1: Connection established.
debug1: identity file /home/myuser/.ssh/identity type -1
debug1: identity file /home/myuser/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/myuser/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-6ubuntu2
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '[pandora]:2520' is known and matches the RSA host key.
debug1: Found key in /home/myuser/.ssh/known_hosts:3
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/myuser/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/myuser/.ssh/identity
debug1: Trying private key: /home/myuser/.ssh/id_dsa
debug1: No more authentication methods to try.
Permission denied (publickey).


So...it looks like the rsa key is used but somehow isn't accepted...?

I'm at a loss to understand why this doesn't work as I can run through the same process (generating key pair, sending to host, cat >> to authorized_keys, setting permissions, configured sshd for public keys) and it works perfectly from my server to my desktop!

Do I need to uncomment #AuthorizedKeysFile %h/.ssh/authorized_keys, isn't that the default anyway?

Any thoughts? :D

---

### Post by CharlesA on 2010-09-11
sshd_config looks ok.

Here's mine (keys only) for reference:

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
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 20
PermitRootLogin no
StrictModes yes

RSAAuthentication no
PubkeyAuthentication yes
#AuthorizedKeysFile     %h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
IgnoreUserKnownHosts no

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

# If specified, login is allowed only for user names that match one of
# the patterns.  Only user names are valid; a numerical user ID is
# not recognized.
#AllowUsers

# Specifies whether remote hosts are allowed to connect to ports
# forwarded for the client.
GatewayPorts no

# Specifies whether TCP forwarding is permitted.
AllowTcpForwarding yes

```

You can backup the current one and then use that one if you want.

What are the permissions for ~/.ssh/* ?

You could try recreating the keypair and using ssh-copy-id to put it on the server.

---

### Post by BkkBonanza on 2010-09-11
The default config should work fine for keys - so if you went and changed things then change them back until you have it working. Usually people have trouble with permissions so triple check that they are all ok. ssh-copy-id should check them as well and if it gave no errors when run then all should be ok for keys. It really should work ok after that. Can you still use a password to access successfully?

---

### Post by RylosFan on 2010-09-13
I can still login with a password.

I will restore the original config and post my results.

---

### Post by kevinthecomputerguy on 2010-09-13
Looks like you have got some awesome help already, only thing i can think of is to check and make sure the time and date right on both servers.
 
-Kev

---

### Post by RylosFan on 2010-09-13
> **BkkBonaza said:**
> The default config should work fine for keys - so if you went and changed things then change them back until you have it working. Usually people have trouble with permissions so triple check that they are all ok. ssh-copy-id should check them as well and if it gave no errors when run then all should be ok for keys. It really should work ok after that. Can you still use a password to access successfully?

I've restored the original config, only set the port and the result is the same as it was when I first started; I'm only prompted for the password.

I've also verified the time on both machines is correct.

Permissions on authorized_keys is set to 600.

---

### Post by RylosFan on 2010-09-13
By the way, I really appreciate everyone's help, I apologize for the gaps between posts, don't mean to leave you all hanging.

---

### Post by CharlesA on 2010-09-13
Next step is to recreate the keys.

```
ssh-keygen
```

---

### Post by RylosFan on 2010-09-13
Looks like the permissions for my home directory and the .ssh directory weren't set to OpenSSH requirements.

I set them with:
$ chmod go-w ~/
$ chmod 700 ~/.ssh

After that I was prompted to enter my passphrase and logged in!

Thanks again for all your help guys! :D

---

