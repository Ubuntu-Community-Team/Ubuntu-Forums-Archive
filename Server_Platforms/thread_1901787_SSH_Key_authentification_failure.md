---
title: "SSH Key authentification failure"
date: 2011-12-29
forum: Server Platforms
---

### Post by SeaKing on 2011-12-29
If have problems with using public key to login to  my server.

What I've done on the client system:

$ ssh-keygen -t rsa -b 4096
*keep directory
*entered passphrase twice (about 150 characters)
$ Your identification has been saved in /home/client/.ssh/id_rsa (and so on everything seemed to be fine)

copied id_rsa.pub to server 

On the server (in the home directory):
$ mkdir .ssh (didn't already exists)
$ touch .ssh/authorized_keys
$  id_rsa.pub >>  .ssh/authorized_keys
$ chmod 700 .ssh/ && chmod 600 .ssh/*

Die sshd_config looks like this:

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

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile    %h/.ssh/authorized_keys

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

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM no
```if I want to connect I get this message:

Agent admitted failure to sign using the key.
Permission denied (publickey).

I tried 2 different keys.

---

### Post by jchung on 2011-12-29
Anything in the logs for the sshd ?

Have you tried running ssh with the -vvv option? e.g. ssh -vvv [email]john@doe.com[/email]

---

### Post by SeaKing on 2011-12-29
The log does not give ssh related infomations during login. 
The -vvv option? There is no such option. Command for conneting is $ssh user@host

---

### Post by jchung on 2011-12-29
> **SeaKing said:**
> The log does not give ssh related infomations during login. 
The -vvv option? There is no such option. Command for conneting is $ssh user@host

Really?

Are you using this in a script? Have you tried it from the command line? If from the command line, you should be able to just type 'ssh -vvv user@host'


[http://www.openbsd.org/cgi-bin/man.cgi?query=ssh&sektion=1](http://www.openbsd.org/cgi-bin/man.cgi?query=ssh&sektion=1)

---

### Post by SeaKing on 2011-12-29
:idea: The Output:
```
OpenSSH_5.8p1 Debian-7ubuntu1, OpenSSL 1.0.0e 6 Sep 2011
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.83 [192.168.1.83] port 22.
debug1: Connection established.
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/seaking/.ssh/id_rsa" as a RSA1 public key
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
debug1: identity file /home/b1n3ry/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-4096
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-4096
debug1: identity file /home/b1n3ry/.ssh/id_rsa-cert type -1
debug1: identity file /home/b1n3ry/.ssh/id_dsa type -1
debug1: identity file /home/b1n3ry/.ssh/id_dsa-cert type -1
debug1: identity file /home/b1n3ry/.ssh/id_ecdsa type -1
debug1: identity file /home/b1n3ry/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu7
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu7 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.8p1 Debian-7ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "192.168.1.83" from file "/home/b1n3ry/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /home/b1n3ry/.ssh/known_hosts:2
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa,ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-dss-cert-v00@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-dss
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
debug2: dh_gen_key: priv key bits set: 124/256
debug2: bits set: 509/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Server host key: RSA 16:ee:c5:40:28:7b:58:51:48:19:06:6c:98:db:1a:46
debug3: load_hostkeys: loading entries for host "192.168.1.83" from file "/home/b1n3ry/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /home/b1n3ry/.ssh/known_hosts:2
debug3: load_hostkeys: loaded 1 keys
debug1: Host '192.168.1.83' is known and matches the RSA host key.
debug1: Found key in /home/b1n3ry/.ssh/known_hosts:2
debug2: bits set: 505/1024
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
debug2: key: /home/b1n3ry/.ssh/id_rsa (0x7f116701b010)
debug2: key: /home/b1n3ry/.ssh/id_dsa ((nil))
debug2: key: /home/b1n3ry/.ssh/id_ecdsa ((nil))
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/b1n3ry/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Server accepts key: pkalg ssh-rsa blen 535
debug2: input_userauth_pk_ok: fp c9:e1:ea:9b:29:a0:60:95:2d:fe:f8:51:a8:22:4a:00
debug3: sign_and_send_pubkey: RSA c9:e1:ea:9b:29:a0:60:95:2d:fe:f8:51:a8:22:4a:00
Agent admitted failure to sign using the key.
debug1: Trying private key: /home/b1n3ry/.ssh/id_dsa
debug3: no such identity: /home/b1n3ry/.ssh/id_dsa
debug1: Trying private key: /home/b1n3ry/.ssh/id_ecdsa
debug3: no such identity: /home/b1n3ry/.ssh/id_ecdsa
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).

```

---

### Post by jchung on 2011-12-29
> **SeaKing said:**
> :idea: The Output:
```
OpenSSH_5.8p1 Debian-7ubuntu1, OpenSSL 1.0.0e 6 Sep 2011
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.83 [192.168.1.83] port 22.
debug1: Connection established.
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/seaking/.ssh/id_rsa" as a RSA1 public key
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
debug1: identity file /home/b1n3ry/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-4096
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-4096
debug1: identity file /home/b1n3ry/.ssh/id_rsa-cert type -1
debug1: identity file /home/b1n3ry/.ssh/id_dsa type -1
debug1: identity file /home/b1n3ry/.ssh/id_dsa-cert type -1
debug1: identity file /home/b1n3ry/.ssh/id_ecdsa type -1
debug1: identity file /home/b1n3ry/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu7
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu7 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.8p1 Debian-7ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "192.168.1.83" from file "/home/b1n3ry/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /home/b1n3ry/.ssh/known_hosts:2
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa,ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-dss-cert-v00@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-dss
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
debug2: dh_gen_key: priv key bits set: 124/256
debug2: bits set: 509/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Server host key: RSA 16:ee:c5:40:28:7b:58:51:48:19:06:6c:98:db:1a:46
debug3: load_hostkeys: loading entries for host "192.168.1.83" from file "/home/b1n3ry/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /home/b1n3ry/.ssh/known_hosts:2
debug3: load_hostkeys: loaded 1 keys
debug1: Host '192.168.1.83' is known and matches the RSA host key.
debug1: Found key in /home/b1n3ry/.ssh/known_hosts:2
debug2: bits set: 505/1024
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
debug2: key: /home/b1n3ry/.ssh/id_rsa (0x7f116701b010)
debug2: key: /home/b1n3ry/.ssh/id_dsa ((nil))
debug2: key: /home/b1n3ry/.ssh/id_ecdsa ((nil))
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/b1n3ry/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Server accepts key: pkalg ssh-rsa blen 535
debug2: input_userauth_pk_ok: fp c9:e1:ea:9b:29:a0:60:95:2d:fe:f8:51:a8:22:4a:00
debug3: sign_and_send_pubkey: RSA c9:e1:ea:9b:29:a0:60:95:2d:fe:f8:51:a8:22:4a:00
Agent admitted failure to sign using the key.
debug1: Trying private key: /home/b1n3ry/.ssh/id_dsa
debug3: no such identity: /home/b1n3ry/.ssh/id_dsa
debug1: Trying private key: /home/b1n3ry/.ssh/id_ecdsa
debug3: no such identity: /home/b1n3ry/.ssh/id_ecdsa
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).

```

Hmm... weird... is 'b1n3ry' on the server or on your local system? I take it 'seaking' is on your local system?

Its weird that your SSH session would be trying to offer up a key form 'b1n3ry'. 

Which account are you using to SSH?

What is the configuration of your ssh_config? (not sshd_config).

---

### Post by SeaKing on 2011-12-29
all b1n3ry

ssh_conf host and client are the same
```

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

### Post by jchung on 2011-12-29
Are you logged into your local machine as seaking or as b1n3ry?

Can you show the environment variables? 

either just "set" or just "env" from the command line. Or settings in your .profile, .bashrc, .cshrc, etc...

---

### Post by SeaKing on 2011-12-29
Client: b1n3ry
Host: test

login from client to host via

$ ssh test@192.168.1.83

---

### Post by jchung on 2011-12-29
Hmmm... would be interesting to see your environment variables. I'm still unsure as to why there is a reference to 'seaking' in the verbose output of ssh.

Otherwise... have you tried with a smaller key? 2048 bits instead of 4096 ?

---

### Post by CharlesA on 2011-12-29
Double check the permissions on the authorized_keys file. They should be 600.

I ran into the same problem on a CentOS box and it turned out that authorized_keys had the wrong permissions.

Also, you'd need the authorized_keys file (with the public key added) in /home/test/.ssh/, if it is not there already.

---

### Post by SeaKing on 2011-12-30
> **CharlesA said:**
> Double check the permissions on the authorized_keys file. They should be 600.

I ran into the same problem on a CentOS box and it turned out that authorized_keys had the wrong permissions.

Also, you'd need the authorized_keys file (with the public key added) in /home/test/.ssh/, if it is not there already.

I've done all of this serveral time and with 2 different VM's

second VM all I've done

```

~$ ssh-keygen -t rsa
Enter file in which to save the key (/home/b1n3ry/.ssh/id_rsa): 
/home/b1n3ry/.ssh/id_rsa already exists.
Overwrite (y/n)? y
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/b1n3ry/.ssh/id_rsa.
Your public key has been saved in /home/b1n3ry/.ssh/id_rsa.pub.
The key fingerprint is:
df:63:65:93:20:a7:a6:26:1d:6a:33:70:13:6b:e9:21 b1n3ry@nobody
The key's randomart image is:
+--[ RSA 2048]----+
|                 |
|                 |
|      .   . o    |
|       +   + . . |
|    E B S o   =  |
|     * = = . o . |
|      B + . +    |
|     . =   . .   |
|                 |
+-----------------+
b1n3ry@nobody:~$ ssh-copy-id -i .ssh/id_rsa.pub minecraft@192.168.1.84
The authenticity of host '192.168.1.84 (192.168.1.84)' can't be established.
RSA key fingerprint is 37:1f:6a:29:14:95:57:62:f7:da:78:ae:80:ee:b5:9f.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.1.84' (RSA) to the list of known hosts.
minecraft@192.168.1.84's password: 
Now try logging into the machine, with "ssh 'minecraft@192.168.1.84'", and check in:

  ~/.ssh/authorized_keys

to make sure we haven't added extra keys that you weren't expecting.

b1n3ry@nobody:~$ ssh minecraft@192.168.1.84
Agent admitted failure to sign using the key.
minecraft@192.168.1.84's password: 
Linux sql-server-mc 2.6.32-33-generic-pae #70-Ubuntu SMP Thu Jul 7 22:51:12 UTC 2011 i686 GNU/Linux
Ubuntu 10.04.3 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/
Last login: Fri Dec 30 13:34:27 2011

minecraft@sql-server-mc:~$ chmod 700 .ssh/
minecraft@sql-server-mc:~$ cd .ssh/
minecraft@sql-server-mc:~/.ssh$ chmod 600 authorized_keys 
minecraft@sql-server-mc:~$ sudo nano /etc/ssh/sshd_config 
[sudo] password for minecraft: 
minecraft@sql-server-mc:~$ sudo service ssh reload
minecraft@sql-server-mc:~$ exit
Abgemeldet
Connection to 192.168.1.84 closed.
b1n3ry@nobody:~$ ssh minecraft@192.168.1.84
Agent admitted failure to sign using the key.
minecraft@192.168.1.84's password: 

```

sshd_:config is the same as in Post 1 but I let **PasswordAuthentication yes**

---

### Post by spynappels on 2011-12-30
Hi SeaKing,

Can you run ```
ssh-add
``` on the client computer to see if that works? rebooting the client computer should have the same effect.

---

### Post by hawkmage on 2011-12-30
There was a bug in earlier version of the gnome-keyring service that would cause these symptoms and give the message "Agent admitted failure to sign using the key" but that reported as fixed about a year and a half ago.  The workaround was to run the command that "spynappels" gave: ssh-add.  This should update the gmome-keyring or any other key manager agent you may be using.

---

### Post by SeaKing on 2011-12-30
> **spynappels said:**
> Hi SeaKing,

Can you run ```
ssh-add
``` on the client computer to see if that works? rebooting the client computer should have the same effect.

Finally IT WORKS :D Great!

Just a last question, where do I have to put the public key in if I want to use this for root access. /root/.ssh/?

---

### Post by spynappels on 2011-12-30
> **SeaKing said:**
> Finally IT WORKS :D Great!

Just a last question, where do I have to put the public key in if I want to use this for root access. /root/.ssh/?

Yes, although that is not enabled by default in Ubuntu and forum policy prevents us from supporting that explicitly. Sudo also works!

---

### Post by SeaKing on 2011-12-30
on my rented server I have only a root account and the group admin does not exist. If I create the group admin and make my user member of it, does it work as well?

---

### Post by spynappels on 2011-12-30
> **SeaKing said:**
> on my rented server I have only a root account and the group admin does not exist. If I create the group admin and make my user member of it, does it work as well?

In that case, as you have been given a root account, then your original plan should work, add your public key to root's .ssh/authorized_keys file.

---

