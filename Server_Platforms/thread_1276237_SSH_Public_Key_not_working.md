---
title: "SSH Public Key not working"
date: 2009-09-26
forum: Server Platforms
---

### Post by coolgk on 2009-09-26
[SIZE=5][COLOR=Red]**SOLVED, SEE THIS**[/COLOR][/SIZE] 
[B][SIZE=4]http://ubuntuforums.org/showthread.php?t=1214231[/SIZE]
[/B] 

Hello,

I need some help with my SSH passwordless login. 

I am very new to setting up a server, I did my research, googled eveything I can think of but I just cant get my public key working on the server I am trying to set up.

Server: Ubuntu Server 9.04

I have my public RSA key generated from Mac OS X which works fine with two different other servers (work, shared hosting server) but it does not work with the server I am trying to build. Since my key works on other servers, I guess it's not a client side problem.

Since my rsa key does not work, I have also _ssh-keygen -t dsa_ a new DSA key and both rsa and dsa keys are appended into server:~/.ssh/authorized_keys. Both keys have no passphrase.

When I try to login, it still prompts for password. (If I have an active login session, no password prompt for the second login, same user)

Thanks alot for helping[COLOR=DarkGreen][B].


[COLOR=Blue]cat /etc/ssh/sshd_config[/COLOR]

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 12134
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

[COLOR=Red]RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile    %h/.ssh/authorized_keys[/COLOR]

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

UsePAM yes


[COLOR=Blue]ls -la[/COLOR]

drwx------ 2 dan dan 4096 2009-09-27 11:48 .ssh[/B][/COLOR]

[COLOR=Blue]**ls -la .ssh **[/COLOR]

[COLOR=DarkGreen]**-rw------- 1 dan dan 1086 2009-09-27 11:48 authorized_keys**[/COLOR]


[B][COLOR=DarkGreen][COLOR=Blue]ssh -vvv dan@192.168.1.148 -p 12134

[/COLOR]ssh -vvv dan@192.168.1.148 -p 12134
OpenSSH_5.1p1, OpenSSL 0.9.7l 28 Sep 2006
debug1: Reading configuration data /etc/ssh_config
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.148 [192.168.1.148] port 12134.
debug1: Connection established.
debug1: identity file /Users/dan/.ssh/identity type -1
debug3: Not a RSA1 key file /Users/dan/.ssh/id_rsa.
debug2: [COLOR=Red]key_type_from_name: unknown key type[/COLOR] '-----BEGIN'
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
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: [COLOR=Red]identity file /Users/dan/.ssh/id_rsa type 1[/COLOR]
debug3: [COLOR=Red]Not a RSA1 key file /Users/dan/.ssh/id_dsa.[/COLOR]
debug2: key_type_from_name: unknown key type '-----BEGIN'
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
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1:[COLOR=Red] identity file /Users/dan/.ssh/id_dsa type 2[/COLOR]
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
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
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 128/256
debug2: bits set: 502/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: put_host_port: [192.168.1.148]:12134
debug3: put_host_port: [192.168.1.148]:12134
debug3: check_host_in_hostfile: filename /Users/dan/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 7
debug3: check_host_in_hostfile: filename /Users/dan/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 7
debug1: Host '[192.168.1.148]:12134' is known and matches the RSA host key.
debug1: Found key in /Users/dan/.ssh/known_hosts:7
debug2: bits set: 514/1024
debug1: [COLOR=Red]ssh_rsa_verify: signature correct[/COLOR]
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /Users/dan/.ssh/identity (0x0)
debug2: key: /Users/dan/.ssh/id_rsa (0x107ed0)
debug2: key: /Users/dan/.ssh/id_dsa (0x107ee0)
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /Users/dan/.ssh/identity
debug3: no such identity: /Users/dan/.ssh/identity
debug1: Offering public key: /Users/dan/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Offering public key: /Users/dan/.ssh/id_dsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug2:[COLOR=Red] we did not send a packet, disable method[/COLOR]
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password

[/COLOR][/B]

---

### Post by Bachstelze on 2009-09-26
1. A key with no passphrase is a **VERY BAD** idea. It's like saying "hey, guys, steal my key, then you can login to my servers al you want!".

2. Your SSH output indicates that the formatting of your key is wrong. Maybe it got altered during transfer?

---

### Post by BkkBonanza on 2009-09-27
I'm not an expert on this but I do have a couple servers set up for passwordless login using keys. It has generally worked well the first time I tried. I checked my key files here and noticed that they are not in the format that seems to be implied by your debug messages. That is, your debug message is saying "not a RSA1 key", and giving messages about ----BEGIN and ----END. But my key file has no BEGIN/END lines and is just a single line with the public key data. 

This seems to indicate that maybe you have supplied incorrect files for your server to use. The server should have your public key not the private one. The private one should only be on your client machine and even then tightly controlled. At least in my case here only the private key has the BEGIN/END lines with data on lines between. I would double check what key you put on the server and make sure it is the public one.

---

### Post by coolgk on 2009-09-27
> **BkkBonaza said:**
> I'm not an expert on this but I do have a couple servers set up for passwordless login using keys. It has generally worked well the first time I tried. I checked my key files here and noticed that they are not in the format that seems to be implied by your debug messages. That is, your debug message is saying "not a RSA1 key", and giving messages about ----BEGIN and ----END. But my key file has no BEGIN/END lines and is just a single line with the public key data. 

This seems to indicate that maybe you have supplied incorrect files for your server to use. The server should have your public key not the private one. The private one should only be on your client machine and even then tightly controlled. At least in my case here only the private key has the BEGIN/END lines with data on lines between. I would double check what key you put on the server and make sure it is the public one.

Thanks for your reply.  

I did copied the public keys onto the server, authorized_keys only contains id_dsa.pub, id_rsa.pub from my client machine. 

I just tried to connect to my other servers, the debug messages showed the same ---BEGIN, ---END error in log but I could successfully log in without entering password.

It just doesnt work on my new server :(

---

