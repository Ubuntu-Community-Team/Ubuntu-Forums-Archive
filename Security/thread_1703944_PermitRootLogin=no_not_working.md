---
title: "PermitRootLogin=no not working"
date: 2011-03-09
forum: Security
---

### Post by xin85 on 2011-03-09
I'm trying to turn off SSH root login on Ubuntu 10.10. However, changing PermitRootLogin=no (/etc/ssh/sshd_config) do not work. Here is the sshd_config:
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
LoginGraceTime 120
PermitRootLogin no
StrictModes yes
MaxAuthTries 1

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile    /home/wenxinleong/.ssh/authorized_keys

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

```Any help will be grateful. Thanks.

---

### Post by skraps on 2011-03-10
Have you restarted the service? Sounds like a dumb question, but you'd be surprised.

---

### Post by prshah on 2011-03-10
> **xin85 said:**
> changing PermitRootLogin=no (/etc/ssh/sshd_config) do not work. 
```

PermitRootLogin no

PubkeyAuthentication yes
#AuthorizedKeysFile    /home/wenxinleong/.ssh/authorized_keys


```

"PermitRootLogin no" (no "=" sign) will work. However, if you have enabled public key authorization, and your /root/.ssh/authorized_key (or authorized_keys2) file contains a valid public key, then you will be able to login as root anyway.

If this is the case, remove the .ssh/authorized_key file from the /root and keep it in the (relevant) user's home directory.

Of course, any change the sshd_config file requires a restart of the ssh service for the changes to be recognized ```
sudo service ssh restart
```

---

### Post by wenxinleong on 2011-03-10
Thanks for the quick prompt.
I checked but there isnt file /root/.ssh/authorized_key. Anyhow, I cleared user/.ssh/authorized_key. Tried "PubkeyAuthentication no" All do not work, I'm still able to login root on remote device. Any clue? Thanks.

FYI: I reboot pc on every attempt:D

---

### Post by bodhi.zazen on 2011-03-10
> **wenxinleong said:**
> Thanks for the quick prompt.
I checked but there isnt file /root/.ssh/authorized_key. Anyhow, I cleared user/.ssh/authorized_key. Tried "PubkeyAuthentication no" All do not work, I'm still able to login root on remote device. Any clue? Thanks.

FYI: I reboot pc on every attempt:D

Post the command you are using to log in with with the -vv option.

```
ssh -vv root@server
```

---

### Post by wenxinleong on 2011-03-10
```

user@user-laptop:~$ ssh -vv user@xxx.xx.xxx.x
OpenSSH_5.5p1 Debian-4ubuntu5, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to xxx.xx.xxx.x [xxx.xx.xxx.x] port 22.
debug1: Connection established.
debug1: identity file /home/user/.ssh/id_rsa type -1
debug1: identity file /home/user/.ssh/id_rsa-cert type -1
debug1: identity file /home/user/.ssh/id_dsa type -1
debug1: identity file /home/user/.ssh/id_dsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.5p1 Debian-4ubuntu5
debug1: match: OpenSSH_5.5p1 Debian-4ubuntu5 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.5p1 Debian-4ubuntu5
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com,ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 139/256
debug2: bits set: 491/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'xxx.xx.xxx.x' is known and matches the RSA host key.
debug1: Found key in /home/user/.ssh/known_hosts:1
debug2: bits set: 538/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/user/.ssh/id_rsa ((nil))
debug2: key: /home/user/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/user/.ssh/id_rsa
debug1: Trying private key: /home/user/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
user@xxx.xx.xxx.x's password:
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 1
debug1: Sending environment.
debug1: Sending env LANG = en_GB.UTF-8
debug2: channel 0: request env confirm 0
debug2: channel 0: request shell confirm 1
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel_input_status_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_status_confirm: type 99 id 0
debug2: shell request accepted on channel 0
Linux user-laptop 2.6.35-27-generic-pae #48-Ubuntu SMP Tue Feb 22 21:46:58 UTC 2011 i686 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

Last login: Thu Mar 10 17:56:04 2011 from user-laptop
user@user-laptop:~$ sudo su
[sudo] password for user:
root@user-laptop:/home/user#

```The ip address and username are replaced for security reason. 
Thanks.

---

### Post by The Cog on 2011-03-10
That looks to me as though you are logging in as user, not as root. PermitRootLogin won't have any effect on that.

---

### Post by wenxinleong on 2011-03-10
isnt "sudo su" root login? I thought PermitRootLogin will prevent "sudo"? or am I wrong

---

### Post by bodhi.zazen on 2011-03-10
If you wish to prevent a user from becoming root, remove him or her from the admin group (configure sudo, not sshd).

---

### Post by wenxinleong on 2011-03-10
Oh I got it now, I confused myself with "sudo su" and "ssh [email]root@xxx.xxx.xxx.xxx[/email]" login. Thanks

---

### Post by matt_symes on 2011-03-10
\

---

### Post by bodhi.zazen on 2011-03-10
> **matt_symes said:**
> Hi

If you want the user to have sudo rights but not su

```
sudo su
```

edit your /etc/sudoers file _using_ visudo and change the sudoers group from 

```
%sudo ALL=(ALL) ALL
```

to

```
%sudo ALL=(ALL) ALL, !/bin/su
```

on the remote machine.



That "solution" is subotpimal, it does not prevent sudo -i , or using sudo via any number of bad behaviors to obtain root access. Obtaining a root shell would be trivial with that configuration (I can think of at least 5 methods).

If the user needs root (sudo) access to an application it is far better to list the applications allowed then try to generate a blacklisting.

See man sudo and man sudoers

Edit: I saw that ninja edit :twisted:

---

### Post by matt_symes on 2011-03-10
Hi

I realised that and that's is why is removed it. Not in time though.

Kind regards

---

### Post by bodhi.zazen on 2011-03-10
> **matt_symes said:**
> Hi

I realised that and that's is why is removed it. Not in time though.

Kind regards

Hahaha !! 

Fair enough.

---

