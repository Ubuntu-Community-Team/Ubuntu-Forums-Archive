---
title: "sshd is refusing keys"
date: 2007-02-22
forum: Server Platforms
---

### Post by amrypma on 2007-02-22
Hello evryone,

I have an ssh deamon who won't accept public key authentication. I have two computers and a server. 

computer 2 <--> server    works just fine, both ways.
computer 1 -----> server.   works
computer 1 -----> computer2 works.

However..
computer 2 ----->computer 1 doesn't work.
server -----> computer 1 also doesn't work.

I can't logon to computer 1  using my keys. it keeps requesting a password. I cant figure out what is wrong. 

Both ssh deamon configurations on computer1 and 2 are identical.
Both sets of keys are Identical, ownership and permissions included.
Both ssh client configurations are identical.

Can any one help?

```

amrypma@tortuga:~/.ssh$ ls -l
total 24
-rw------- 1 amrypma amrypma 1745 2007-02-22 20:21 authorized_keys
-rw------- 1 amrypma amrypma  358 2007-02-22 20:21 config
-rw------- 1 amrypma amrypma  736 2007-02-22 20:12 id_dsa
-rw------- 1 amrypma amrypma  619 2007-02-22 20:12 id_dsa.pub
-rw------- 1 amrypma amrypma 4261 2007-02-22 21:14 known_hosts

```

the ssh config, identical on all mashines
```

Host *
        Protocol 2
        ForwardX11=yes
        ForwardAgent=yes
        Compression=yes
        IdentityFile=$HOME/.ssh/id_dsa

```

/etc/ssh/ssh_config identical on computer1 and 2
```

#       $OpenBSD: ssh_config,v 1.21 2005/12/06 22:38:27 reyk Exp $

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
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes


```

/etc/ssh/sshd_config, identical on computer 1 and 2
```

amrypma@tortuga:~/.ssh$ cat /etc/ssh/sshd_config 
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
amrypma@tortuga:~/.ssh$ cat /etc/ssh/sshd_config 
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
KeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes


```

```

OpenSSH_4.3p2 Debian-5ubuntu1, OpenSSL 0.9.8b 04 May 2006
debug1: Reading configuration data /home/amrypma/.ssh/config
debug1: Applying options for *
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.123.1 [192.168.123.1] port 22.
debug1: Connection established.
debug1: identity file $HOME/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-5ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-5ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: zlib@openssh.com,zlib,none
debug2: kex_parse_kexinit: zlib@openssh.com,zlib,none
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_init: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 zlib@openssh.com
debug2: mac_init: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 zlib@openssh.com
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 114/256
debug2: bits set: 512/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/amrypma/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 12
debug1: Host '192.168.123.1' is known and matches the RSA host key.
debug1: Found key in /home/amrypma/.ssh/known_hosts:12
debug2: bits set: 511/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/amrypma/.ssh/id_dsa (0x809df28)
debug2: key: $HOME/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/amrypma/.ssh/id_dsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: $HOME/.ssh/id_dsa
debug3: no such identity: $HOME/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
amrypma@192.168.123.1's password: 
```

Can anyone help?

---

### Post by thenebcouk on 2007-02-26
Hi there, by the look of it your id_dsa doesn't exist or isn't readable. Obviously I won't ask you to post that here.

---

### Post by amrypma on 2007-03-14
That I would certianly not. But I'll have a look at it today.

---

### Post by amrypma on 2007-03-14
This is still mystifing me.

the mashine is still refusing keys.

I can use keys perfectly everywhere working just as they should except when connecting to `computer 1` . 

And I'm using the same keys with the same permissions. 

thus all these file are identical everywhere with the same permissions.

/etc/ssh/sshd_config
/etc/default/ssh
~/.ssh/authorized_keys
~/.ssh/id_dsa
~/.ssh/id_dsa.pub

I must be missing something utterly stupid here becaus I`m running out of places to look.

---

### Post by jbird123 on 2007-03-30
Are you running any other kind of access control/authentication protocol on computer 1?

I had a similar problem setting up password-less ssh access to the student-accessible servers on our campus. Our school infrastructure runs kerberos and AFS. When we log in via password-based ssh, the server takes the password string it receives and passes it to kerberos, which acquires tickets. It then uses these tickets to mount our home directories, which are stored on AFS.

The problem with publickey authentication is that you never send over your password string. Without this string, the school ssh server could not acquire tickets, mount our home directories, and read our ~/.ssh/id_rsa* and ~/.ssh/authorized_keys files. The ssh server simply assumed that these files did not exist.

The workaround involved installing a kerberos client and going GSSAPI authentication and not publickey.

Maybe you are running a similar system? Mabe computer 1 uses LDAP or Active Directory to provide access to your home directory files?

---

### Post by Mr. C. on 2007-03-30
Replace IdentityFile=$HOME/.ssh/id_dsa with IdentityFile=~/.ssh/id_dsa .

MrC

---

### Post by amrypma on 2007-04-02
Well I hate to admit it, but it was the permissions.

Desided to start fresh and it worked like a charm. Took a look at the difference between the new and old acount and there it was plain as day..

new:
drwxr-xr-x  3 amrypma amrypma   4096 2007-04-02 15:34 .ssh

old:
drwx------   3 amrypma amrypma       4096 2007-03-14 12:54 .ssh

All the permissions are the same.

Thanks,

Auke

---

