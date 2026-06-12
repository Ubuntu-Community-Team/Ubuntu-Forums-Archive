---
title: "Permission denied (publickey)."
date: 2011-01-30
forum: Server Platforms
---

### Post by jiapei100 on 2011-01-30
Hi, all:

This seems to be an old problem. My OS: Ubuntu 10.10 .


```
ssh -v git@github.com
```
fails.

> jiapei@jiapei-laptop:~$ ssh -v [email]git@github.com[/email]
OpenSSH_5.5p1 Debian-4ubuntu4, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to github.com [207.97.227.239] port 22.
debug1: Connection established.
debug1: identity file /home/jiapei/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/jiapei/.ssh/id_rsa-cert type -1
debug1: identity file /home/jiapei/.ssh/id_dsa type -1
debug1: identity file /home/jiapei/.ssh/id_dsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-5github2
debug1: match: OpenSSH_5.1p1 Debian-5github2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.5p1 Debian-4ubuntu4
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'github.com' is known and matches the RSA host key.
debug1: Found key in /home/jiapei/.ssh/known_hosts:4
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/jiapei/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/jiapei/.ssh/id_dsa
debug1: No more authentication methods to try.
Permission denied (publickey).
jiapei@jiapei-laptop:~$ 


My > /etc/ssh/sshd_config :

> jiapei@jiapei-laptop:/etc/ssh$ cat sshd_config
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
PasswordAuthentication yes

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
jiapei@jiapei-laptop:/etc/ssh$



I tried one potential solution found on the Internet:
> chmod 600 ~/.ssh/id_rsa && chmod 600 ~/.ssh/id_rsa.pub

still not workable.


Looking forward to your earliest reply. Thank you...

Best Regards
JIA Pei

---

### Post by James78 on 2011-01-30
For it to use your public key you must tell it where it is located. Uncomment this..
```
#AuthorizedKeysFile %h/.ssh/authorized_keys
```
And then you can rename your id_rsa.pub to authorized_keys in the ~/.ssh folder.

---

### Post by jiapei100 on 2011-01-30
> **James78 said:**
> For it to use your public key you must tell it where it is located. Uncomment this..
```
#AuthorizedKeysFile %h/.ssh/authorized_keys
```
And then you can rename your id_rsa.pub to authorized_keys in the ~/.ssh folder.


Thank you so much !!!
Problem solved !!!

Really thank you !!!

What's more, if I would like to commit one file to two positions, say, two git repositories, what should I do?

```
AuthorizedKeysFile %h/.ssh/authorized_keys1
AuthorizedKeysFile %h/.ssh/authorized_keys2

```
and put both  authorized_keys1  and  authorized_keys2  under  /.ssh/  ???


Thanks again !!!
JIA Pei

---

### Post by James78 on 2011-01-30
I have never seen anyone use 2 AuthorizedKeysFile directives before. In about 2009, Debian (where Ubuntu gets their packages from) may have added support to OpenSSH for multiple blocks. So all I can say is, that it may or may not be supported; you'll have to try it out.

However, if what you're attempting to do is authenticate with more than 1 key, you can just add the new keys to the end of the original ~/.ssh/authorized_keys file and it'll work completely fine.

---

### Post by jiapei100 on 2011-01-30
I successfully commit my source to github already.
I'm trying to commit it to sourceforge now.
I'm trying to use two different directories to deal with these two git repositories.


I strictly follow the description at [https://sourceforge.net/apps/trac/sourceforge/wiki/Git](https://sourceforge.net/apps/trac/sourceforge/wiki/Git) 
but finally with a failure notification like:

> jiapei@jiapei-laptop:~/cmake/sf/vosm$ git push origin master
[email]jiapei@vosm.git.sourceforge.net[/email]'s password: 
Counting objects: 205, done.
Delta compression using up to 2 threads.
Compressing objects: 100% (200/200), done.
Writing objects: 100% (205/205), 282.70 KiB, done.
Total 205 (delta 103), reused 0 (delta 0)
fatal: Unable to create temporary file: Permission denied
error: unpack failed: index-pack abnormal exit
To ssh://jiapei@vosm.git.sourceforge.net/gitroot/vosm/vosm
 ! [remote rejected] master -> master (n/a (unpacker error))
error: failed to push some refs to 'ssh://jiapei@vosm.git.sourceforge.net/gitroot/vosm/vosm'


Do you know what's wrong I'm facing?

Best Regards
JIA

---

### Post by James78 on 2011-01-30
Not sure of what the problem would be there. I'm afraid that'd really be a question for a new topic anyways. Good luck. ;)

---

### Post by jiapei100 on 2011-01-30
> **James78 said:**
> Not sure of what the problem would be there. I'm afraid that'd really be a question for a new topic anyways. Good luck. ;)

Thank you for your suggestion.
I'll do it soon.

Cheers
JIA

---

