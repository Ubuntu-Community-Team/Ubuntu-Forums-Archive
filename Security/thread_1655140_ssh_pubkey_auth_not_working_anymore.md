---
title: "ssh pubkey auth not working anymore"
date: 2010-12-29
forum: Security
---

### Post by friendlypenguin on 2010-12-29
Hello Everybody
I come to you with a quite strange problem. Some weeks ago, I set up an SSH-server on my Synology NAS and 
configured it so that only publickey authentication was allowed. Everything worked fine, but one fine day, 
I wasn't able anymore to connect to the server with publickey auth. (Note that the login worked when I switched 
to password login.) This happened from both my laptops.
I recreated the Key-Pair on my laptops with ```
ssh-keygen -t rsa -b 4096
``` and put the new keys in the file /home/user/.ssh/authorized_keys on the server.
This file looks like this:
```
sshserver> cat /home/sshuser/.ssh/authorized_keys
ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAgEAwF3tbjd4i0YD5E/6j5KlhjIDLHQLXYP3beETW9ZUSsyho80HfkMpsztpEvc/YPui5zw8MVQDYFr7dfCpel7KJoEtZeqwH5rAcV/yX9XgPZcb8qoeiX2Du5nI/yoEGCgeh29aPUXhT2/zYjvERGPSjJHlT0/FhGghxKNAsZWSeI+7L21IpLQoqdlAhBQ9C3bn4Yh+/Xqioe7vSdHlOhV6s2w4bGPJoNB3vewK38GCV38xg+ur5wDeNl4Bs+GVQgwr5PlNFHAP1RO3PT7n6YcgW3RcB8Dye4sh+SFPjZDIDUhsGS7m+r7IMTk5AoFoKKGkrvAAO79JX+Xnka3WLXkiyLhEfMyaa1IjN8U/0VhkGplu6qro1i9tfTDxW0b9ZSMGXe3mWNGbSQRhskZelDEY9bc1MG+nszNs5QFanRNFNQmTq3U8zkCJmehy0zkAGQAQlYMf6AJzrLdRZxnqlfiZfC7vrZBCml011wcPqCS/T2QAnYSOiEetz2oAVqy8mQMyxuXrqer7CJtoDlbha4ke6awz+hJWM7spgR2b/R9nmOz/17i5z5mGWFx5XpDvJzEzzr+fYV8XgGXPVdAmZaYVlEdAX5YxCGf5QlOUjO2O5RUTFhUny8qWkYdzK6phlwFJUFKoourvA5zMBsp4BMKIxV2J3dDcg6hx3Xo+AeGuJy8= user@sshclient
sshserver>

```
The configfile on the server is the following:
```

sshserver> cat /etc/ssh/sshd_config
# $OpenBSD: sshd_config,v 1.80 2008/07/02 02:24:18 djm Exp $
# This is the sshd server system-wide configuration file. See
# sshd_config(5) for more information.
# This sshd was compiled with PATH=/usr/bin:/bin:/usr/sbin:/sbin
# The strategy used for options in the default sshd_config shipped with
# OpenSSH is to specify options with their default value where
# possible, but leave them commented. Uncommented options change a
# default value.
Port 1111
#AddressFamily any
#ListenAddress 0.0.0.0
#ListenAddress ::
# Disable legacy (protocol version 1) support in the server for new
# installations. In future the default will change to require explicit
# activation of protocol 1
Protocol 2
# HostKey for protocol version 1
#HostKey /etc/ssh/ssh_host_key
# HostKeys for protocol version 2
#HostKey /etc/ssh/ssh_host_rsa_key
#HostKey /etc/ssh/ssh_host_dsa_key
# Lifetime and size of ephemeral version 1 server key
#KeyRegenerationInterval 1h
#ServerKeyBits 1024
# Logging
# obsoletes QuietMode and FascistLogging
#SyslogFacility AUTH
#LogLevel INFO
# Authentication:
#LoginGraceTime 2m
PermitRootLogin no
#StrictModes yes
MaxAuthTries 3
MaxSessions 3
#RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile .ssh/authorized_keys
#now ssh is only used by rsync ==> auth by passwd file of rsync server
#AuthPassFile /etc/rsyncd.secrets
# For this to work you will also need host keys in /etc/ssh/ssh_known_hosts
#RhostsRSAAuthentication no
# similar for protocol version 2
#HostbasedAuthentication no
# Change to yes if you don't trust ~/.ssh/known_hosts for
# RhostsRSAAuthentication and HostbasedAuthentication
#IgnoreUserKnownHosts no
# Don't read the user's ~/.rhosts and ~/.shosts files
#IgnoreRhosts yes
# To disable tunneled clear text passwords, change to no here!
PasswordAuthentication no
#PermitEmptyPasswords no
# Change to no to disable s/key passwords
ChallengeResponseAuthentication no
# Kerberos options
#KerberosAuthentication no
KerberosOrLocalPasswd no
KerberosTicketCleanup no
#KerberosGetAFSToken no
# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials no
# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication. Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
#UsePAM no
#AllowAgentForwarding yes
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
#ChrootDirectory none
DenyUsers root,admin
# no default banner path
Banner /root/sshbanner
# override default of no subsystems
Subsystem sftp /usr/libexec/sftp-server
# Example of overriding settings on a per-user basis
#Match User anoncvs
# X11Forwarding no
# AllowTcpForwarding no
# ForceCommand cvs server
sshserver>
UserEnvironment no
#Compression delayed
#ClientAliveInterval 0
#ClientAliveCountMax 3
#UseDN

```
Good so far. When I now try to connect to the sshserver from my laptop, the following output is generated:
```

user@sshclient:~$ ssh -vvv -p 1111 sshuser@192.168.1.20
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.20 [192.168.1.20] port 1111.
debug1: Connection established.
debug1: identity file /home/user/.ssh/identity type -1
debug3: Not a RSA1 key file /home/user/.ssh/id_rsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'DEK-Info:'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/user/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-4096
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-4096
debug1: identity file /home/user/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.2
debug1: match: OpenSSH_5.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug3: Wrote 792 bytes for a total of 831
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
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
debug3: Wrote 24 bytes for a total of 855
debug2: dh_gen_key: priv key bits set: 134/256
debug2: bits set: 1015/2048
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: Wrote 272 bytes for a total of 1127
debug3: put_host_port: [192.168.1.20]:1111
debug3: put_host_port: [192.168.1.20]:1111
debug3: check_host_in_hostfile: filename /home/user/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug3: check_host_in_hostfile: filename /home/user/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug1: Host '[192.168.1.20]:1111' is known and matches the RSA host key.
debug1: Found key in /home/user/.ssh/known_hosts:1
debug2: bits set: 1003/2048
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug3: Wrote 16 bytes for a total of 1143
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug3: Wrote 48 bytes for a total of 1191
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/user/.ssh/id_rsa (0x218fc358)
debug2: key: /home/user/.ssh/identity ((nil))
debug2: key: /home/user/.ssh/id_dsa ((nil))
debug3: Wrote 64 bytes for a total of 1255
debug3: input_userauth_banner
+++++++++++++++++++++++++++++++++++++++++++++++
ssh-banner
+++++++++++++++++++++++++++++++++++++++++++++++
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/user/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug3: Wrote 624 bytes for a total of 1879
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/user/.ssh/identity
debug3: no such identity: /home/user/.ssh/identity
debug1: Trying private key: /home/user/.ssh/id_dsa
debug3: no such identity: /home/user/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).
user@sshclient:~$

```
What seems really strange to me is the problem at the beginning: 
```

debug1: Connecting to 192.168.1.20 [192.168.1.20] port 1111.
debug1: Connection established.
debug1: identity file /home/user/.ssh/identity type -1
debug3: Not a RSA1 key file /home/user/.ssh/id_rsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'DEK-Info:'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace

```
After the TCP-connection is set, my client reads the private key but should read the publickey... what the heck is this?
When do substitute the privkey and pubkey with each other, this problem seems to disappear: (surely this is NO solution, just a test the see if my client really messes up something...)
```
user@sshclient:~/.ssh$ ssh -vvv -p 1111 sshuser@192.168.1.20
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.20 [192.168.1.20] port 1111.
debug1: Connection established.
debug1: identity file /home/user/.ssh/identity type -1
debug3: Not a RSA1 key file /home/user/.ssh/id_rsa.
debug1: identity file /home/user/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-4096
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-4096
debug1: identity file /home/user/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.2
debug1: match: OpenSSH_5.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug3: Wrote 792 bytes for a total of 831
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
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
debug3: Wrote 24 bytes for a total of 855
debug2: dh_gen_key: priv key bits set: 119/256
debug2: bits set: 1001/2048
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: Wrote 272 bytes for a total of 1127
debug3: put_host_port: [192.168.1.20]:1111
debug3: put_host_port: [192.168.1.20]:1111
debug3: check_host_in_hostfile: filename /home/user/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug3: check_host_in_hostfile: filename /home/user/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug1: Host '[192.168.1.20]:1111' is known and matches the RSA host key.
debug1: Found key in /home/user/.ssh/known_hosts:1
debug2: bits set: 1078/2048
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug3: Wrote 16 bytes for a total of 1143
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug3: Wrote 48 bytes for a total of 1191
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/user/.ssh/identity ((nil))
debug2: key: /home/user/.ssh/id_rsa (0x21583358)
debug2: key: /home/user/.ssh/id_dsa ((nil))
debug3: Wrote 64 bytes for a total of 1255
debug3: input_userauth_banner
+++++++++++++++++++++++++++++++++++++++++++++++
ssh-banner
+++++++++++++++++++++++++++++++++++++++++++++++
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/user/.ssh/identity
debug3: no such identity: /home/user/.ssh/identity
debug1: Offering public key: /home/user/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug3: Wrote 624 bytes for a total of 1879
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/user/.ssh/id_dsa
debug3: no such identity: /home/user/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).
user@sshclient:~/.ssh$

```
Now it seems that my client can read the publickey:
```

debug1: identity file /home/user/.ssh/id_rsa type 1

```
Anyway. After the ssh-banner is sent my client tries to authenticate with pubkey but does not succed and go on with other methods (even they are not enabled on the server as you can see in the config...)
I read that in strictmode, one have to check for the permissions of the files in /home/user/.ssh/. I checked this, and everthing seems to be correct:
```

user@sshclient:/$ ls -la / | grep home
drwxr-xr-x 5 root root 4096 2010-11-16 14:34 home
user@sshclient:/$ ls -la /home/
total 40
drwxr-xr-x 5 root root 4096 2010-11-16 14:34 .
drwxr-xr-x 22 root root 4096 2010-11-28 16:52 ..
drwxr-xr-x 3 root root 4096 2010-11-16 14:34 .ecryptfs
drwx------ 2 root root 16384 2010-11-16 14:09 lost+found
drwx------ 39 user user 12288 2010-12-29 10:55 user
user@sshclient:/$ 
 
user@sshclient:/home$ ls -la /home/user/.ssh
total 52
drwx------ 2 user user 4096 2010-12-26 13:52 .
drwx------ 39 user user 12288 2010-12-29 10:55 ..
-rw------- 1 user user 3326 2010-12-26 13:47 id_rsa
-rw-r--r-- 1 user user 741 2010-12-26 13:47 id_rsa.pub
-rw-r--r-- 1 user user 442 2010-12-26 13:52 known_hosts
user@sshclient:/home$

```
Before the problem occured I did NOT change anything on the server for a couple of weeks. Neither did I changed something on the clients, but since they are ubuntuclients with automatic updates turned on, I wonder if the ssh-packet updated with this strange results...
Does anyone of you guys have clue about this?
Thank you very much for helping
Philippe

---

### Post by cariboo on 2010-12-29
Check your permissions, ~/.ssh on my system is set to 700, and /etc/ssh/sshd_config is set to 644.

---

