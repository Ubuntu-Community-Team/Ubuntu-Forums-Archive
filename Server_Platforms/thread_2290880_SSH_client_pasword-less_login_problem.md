---
title: "SSH client pasword-less login problem"
date: 2015-08-16
forum: Server Platforms
---

### Post by daniel294 on 2015-08-16
I have a Windows server (windows 7)
That is the backup server and runs cwRsyncServer (a Windows implementation for rsync and OpenSSH ver OpenSSH_5.2)
User: danny
 
I have a Linux client (Ubuntu 12.04).
User: daniel
 
I need to be able to back up my Linux on a Windows server.
I want to use Cron for daily backups and therefor I need to be able to connect to the Windows server without password (using only key authentication)
The problem is, that no matter what I do, I'm being prompt for the password.
 
 
Here is what I did:
 
On Ubuntu (rsync client):
---------------------------
1.   ssh-keygen -t rsa
      Generated pass phrase 12345
2.   ssh-copy-id -i ~/.ssh/id_rsa.pub danny@192.168.0.7
3.   Logged in to danny@192.168.0.7 using a password and verified the public key was copied from the Ubuntu client to the windows server
 
 
 
On windows (rsync server):
--------------------------
Edited the sshd_conf:
 
1. Uncommented these 2 lines:
   RSAAuthentication yes
   PubkeyAuthentication yes
 
2. Uncommented and changed
   #PasswordAuthentication yes to PasswordAuthentication no
 
3. Restart open ssh service.
 
 
Form ubuntu client tried to login with:
ssh -vvv -i ~/.ssh/id_rsa   danny@192.168.0.7
 
I got:



```
OpenSSH_5.9p1 Debian-5ubuntu1.6, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.0.7 [192.168.0.7] port 22.
debug1: Connection established.
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/daniel/.ssh/id_rsa" as a RSA1 public key
debug1: identity file /home/daniel/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/daniel/.ssh/id_rsa-cert type -1
debug1: Remote protocol version 1.99, remote software version OpenSSH_5.2
debug1: match: OpenSSH_5.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.6
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "192.168.0.7" from file "/home/daniel/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /home/daniel/.ssh/known_hosts:2
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: [email]ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com[/email],ssh-rsa
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: [email]ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa,ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-dss-cert-v00@openssh.com[/email],ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
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
debug2: dh_gen_key: priv key bits set: 129/256
debug2: bits set: 537/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Server host key: RSA 7b:18:02:e2:01:b2:42:88:4b:61:ce:c4:0c:d7:8e:bf
debug3: load_hostkeys: loading entries for host "192.168.0.7" from file "/home/daniel/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /home/daniel/.ssh/known_hosts:2
debug3: load_hostkeys: loaded 1 keys
debug1: Host '192.168.0.7' is known and matches the RSA host key.
debug1: Found key in /home/daniel/.ssh/known_hosts:2
debug2: bits set: 524/1024
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
debug2: key: /home/daniel/.ssh/id_rsa (0x7f46110d64e0)
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug3: start over, passed a different list publickey,password,keyboard-interactive
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/daniel/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug2: we did not send a packet, disable method
debug3: authmethod_lookup keyboard-interactive
debug3: remaining preferred: password
debug3: authmethod_is_enabled keyboard-interactive
debug1: Next authentication method: keyboard-interactive
debug2: userauth_kbdint
debug2: we sent a keyboard-interactive packet, wait for reply
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug3: userauth_kbdint: disable: no info_req_seen
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred:
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
danny@192.168.0.7's password:
```

---

### Post by nerdtron on 2015-08-16
Try to generate ssh keys without a passphrase. Delete the uploaded pub keys on the rsync server and then run ssh-copy-id again.

---

### Post by daniel294 on 2015-08-17
That didn't help. it looks like the problem is in the exchange procedure...(maybe different OpenSSH versions or protocols)

Here are my sshd_config (on the server) and ssh_config (client) files:

sshd_config
-------------

```
#	$OpenBSD: sshd_config,v 1.74 2006/07/19 13:07:10 dtucker Exp $


# This is the sshd server system-wide configuration file.  See
# sshd_config(5) for more information.


# This sshd was compiled with PATH=/bin:/usr/sbin:/sbin:/usr/bin


# The strategy used for options in the default sshd_config shipped with
# OpenSSH is to specify options with their default value where
# possible, but leave them commented.  Uncommented options change a
# default value.


#Port 22
#Protocol 2,1
#AddressFamily any
#ListenAddress 0.0.0.0
#ListenAddress ::


# HostKey for protocol version 1
#HostKey /etc/ssh_host_key
# HostKeys for protocol version 2
#HostKey /etc/ssh_host_rsa_key
#HostKey /etc/ssh_host_dsa_key


# Lifetime and size of ephemeral version 1 server key
#KeyRegenerationInterval 1h
#ServerKeyBits 768


# Logging
# obsoletes QuietMode and FascistLogging
SyslogFacility AUTH
LogLevel INFO


# Authentication:


#LoginGraceTime 2m
#PermitRootLogin yes
#StrictModes yes
#MaxAuthTries 6


RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	.ssh/authorized_keys


# For this to work you will also need host keys in /etc/ssh_known_hosts
#RhostsRSAAuthentication no
# similar for protocol version 2
#HostbasedAuthentication no
# Change to yes if you don't trust ~/.ssh/known_hosts for
# RhostsRSAAuthentication and HostbasedAuthentication
#IgnoreUserKnownHosts no
# Don't read the user's ~/.rhosts and ~/.shosts files
#IgnoreRhosts yes


# To disable tunneled clear text passwords, change to no here!
#PasswordAuthentication yes
#PermitEmptyPasswords no


# Change to no to disable s/key passwords
#ChallengeResponseAuthentication yes


# Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes
#KerberosGetAFSToken no


# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes


# Set this to 'yes' to enable PAM authentication, account processing, 
# and session processing. If this is enabled, PAM authentication will 
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
#UsePAM no


#AllowTcpForwarding yes
#GatewayPorts no
#X11Forwarding no
#X11DisplayOffset 10
#X11UseLocalhost yes
#PrintMotd yes
#PrintLastLog yes
#TCPKeepAlive yes
#UseLogin no
#UsePrivilegeSeparation yes
#PermitUserEnvironment no
#Compression delayed
#ClientAliveInterval 0
#ClientAliveCountMax 3
#UseDNS yes
#PidFile /var/run/sshd.pid
#MaxStartups 10
#PermitTunnel no


# no default banner path
#Banner /some/path


# override default of no subsystems
Subsystem	sftp	/bin/sftp-server


# Example of overriding settings on a per-user basis
#Match User anoncvs
#	X11Forwarding no
#	AllowTcpForwarding no
#	ForceCommand cvs server



```

```
shh_config
------------

# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.


# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.


# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.


Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
#   ProxyCommand ssh -q -W %h:%p gateway.example.com
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no
```

---

### Post by daniel294 on 2015-08-17
The problem was wrong permissions.

SSH does not allow group write permissions on ~/.ssh directory
so, it must be changed to 700
authorized_keys permissions should be 600
Another way is to uncomment the strictModes and set it to no (less secure but works)

---

