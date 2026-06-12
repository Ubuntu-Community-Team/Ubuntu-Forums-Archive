---
title: "passwordless ssh login as root"
date: 2016-02-22
forum: Security
---

### Post by chah on 2016-02-22
I'm trying to manage an array of Ubuntu 12.04 (for legacy reasons) machines and I want to perform the same setup on each one. For this I want to ssh to each machine as root, copy some files/directories and run some commands to setup each machine.

I'm following commands from here:[http://unix.stackexchange.com/questions/92123/rsync-all-files-of-remote-machine-over-ssh-without-root-user](http://unix.stackexchange.com/questions/92123/rsync-all-files-of-remote-machine-over-ssh-without-root-user)

I've also followed instructions here: [http://askubuntu.com/questions/115151/how-to-setup-passwordless-ssh-access-for-root-user](http://askubuntu.com/questions/115151/how-to-setup-passwordless-ssh-access-for-root-user)

Instructions on both sites are more or less similar,  but so far no success.

here is /etc/ssh/sshd_config:
```
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
PermitRootLogin without-password
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
#Match User root PasswordAuthentication no
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
```

I've created a key pair with ssh-keygen on the client and I've copied the public key to /root/.ssh/authorized_keys on the server. (In fact I've copied the entire /root/.ssh directory from the ssh-client to the ssh-server. My ssh-client is my master server from which I'm going to copy the settings to the other servers)

When I try to login to the ssh-server I get the following:
```

root:~ # ssh -v root@10.218.27.154
OpenSSH_5.9p1 Debian-5ubuntu1.8, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to 10.218.27.154 [10.218.27.154] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /root/.ssh/id_rsa-cert type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: identity file /root/.ssh/id_dsa-cert type -1
debug1: identity file /root/.ssh/id_ecdsa type -1
debug1: identity file /root/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.9p1 Debian-5ubuntu1.8
debug1: match: OpenSSH_5.9p1 Debian-5ubuntu1.8 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.8
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA f1:ce:57:96:45:d3:8f:da:83:1a:a2:d3:18:a7:3f:74
debug1: Host '10.218.27.154' is known and matches the ECDSA host key.
debug1: Found key in /root/.ssh/known_hosts:2
debug1: ssh_ecdsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /root/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /root/.ssh/id_dsa
debug1: Trying private key: /root/.ssh/id_ecdsa
debug1: Next authentication method: password
root@10.218.27.154's password: 

```

Can anybody interpret why it's not allowing  a passwordless login to the server?

---

### Post by chah on 2016-02-22
Found the problem which I'd like to document here for future reference.
Since I could not scp or rsync the .ssh directory from the client to the server using the root account, I did it using a user account, then copied it from the user account to the root account. 
However, I forgot to chown -R root:root /root/.ssh so the directory and files were still owned by user. 

I initially thought this should not have consequences, because root can read any file. But apparently the directory/files  needs to be owned by root for this to work.
After running the chown command, I can now passwordless ssh login.

Also for reference, the URL that caught me onto this  cause is:[http://www.linuxquestions.org/questions/linux-software-2/passwordless-ssh-setup-not-working-any-ideas-559628/](http://www.linuxquestions.org/questions/linux-software-2/passwordless-ssh-setup-not-working-any-ideas-559628/)

Half a day lost because of incorrect ownership. Hope others can be saved the time.

---

