---
title: "OpenSSH - Permission denied (publickey) - newbie"
date: 2008-07-26
forum: Server Platforms
---

### Post by jmmL on 2008-07-26
I'm attempting to get some practice in running a small home server before i actually get my hands on the hardware. So i'm using virtualbox to run a standard install of xubuntu 8.04.1, and Linux Mint as my host OS.

I've installed the open-ssh server on both machines, and yesterday it was going well: i was able to SSH into the host from the guest and transfer files via scp. However, when i switched on today, i couldn't get xubuntu to ssh into mint. I kept on getting the error "Permission denied (publickey)".

Here is my attempt at ssh-ing in:
```

jamie@xubuntu-server:~$ ssh -v jamie@192.168.0.2
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.0.2 [192.168.0.2] port 22.
debug1: Connection established.
debug1: identity file /home/jamie/.ssh/identity type -1
debug1: identity file /home/jamie/.ssh/id_rsa type 1
debug1: identity file /home/jamie/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.0.2' is known and matches the RSA host key.
debug1: Found key in /home/jamie/.ssh/known_hosts:2
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/jamie/.ssh/identity
debug1: Offering public key: /home/jamie/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/jamie/.ssh/id_dsa
debug1: No more authentication methods to try.
Permission denied (publickey).
jamie@xubuntu-server:~$ ssh -vvv jamie@192.168.0.2
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.0.2 [192.168.0.2] port 22.
debug1: Connection established.
debug1: identity file /home/jamie/.ssh/identity type -1
debug3: Not a RSA1 key file /home/jamie/.ssh/id_rsa.
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
debug1: identity file /home/jamie/.ssh/id_rsa type 1
debug1: identity file /home/jamie/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
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
debug2: dh_gen_key: priv key bits set: 127/256
debug2: bits set: 520/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/jamie/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 2
debug1: Host '192.168.0.2' is known and matches the RSA host key.
debug1: Found key in /home/jamie/.ssh/known_hosts:2
debug2: bits set: 517/1024
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
debug2: key: /home/jamie/.ssh/identity ((nil))
debug2: key: /home/jamie/.ssh/id_rsa (0xb7f3c610)
debug2: key: /home/jamie/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/jamie/.ssh/identity
debug3: no such identity: /home/jamie/.ssh/identity
debug1: Offering public key: /home/jamie/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/jamie/.ssh/id_dsa
debug3: no such identity: /home/jamie/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).

```

and here's the contents of /etc/ssh/sshd_config :
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
#PasswordAuthentication no

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

```

I created public keys for both machines using
```
ssh-keygen -t rsa
```

and then
```
cd ~/.ssh
cp id_rsa.pub authorized_keys
```

Both machines can SSH into themselves no-problem, and I haven't tried ssh-ing into a machine outside of the local network (because i don't have such a machine to try on).

It's just odd that i wouldn't be able to do it today when i could to it yesterday! Any help would be fantastic!

---

### Post by kevdog on 2008-07-26
Have you tried on the client deleting the known_hosts file?

---

### Post by jmmL on 2008-07-26
I've re-installed all the openssh stuff in hope of recreating yesterday's success. I think deleted known_hosts along with everything else in ~/.ssh.

Just to be sure, I deleted known_hosts from the client (which i've oddly called xubuntu-server), and here is the output:
```

jamie@xubuntu-server:~$ ssh jamie@192.168.0.2
The authenticity of host '192.168.0.2 (192.168.0.2)' can't be established.
RSA key fingerprint is e8:cd:f2:c2:5b:9e:c2:80:a1:e7:79:52:19:8e:41:7e.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.0.2' (RSA) to the list of known hosts.
Permission denied (publickey).

```

Still no luck :(

---

### Post by Jozza The Wick on 2008-08-10
Ummm I don't know if you've already done this, but the Advanced SSH Howto ([https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH))  has this comment:

If you're sure you've correctly configured sshd_config, appended your public key to authorized_keys, and have your private key in the .ssh directory, and still getting this error: 

Permission denied (publickey).

Chances are, your /home/user and ~/.ssh/authorized_keys permissions are too open by OpenSSH standards. You can get rid of this problem by issuing the following commands: 
$ chmod go-w ~/
$ chmod 700 ~/.ssh
$ chmod 600 ~/.ssh/authorized_keys

Am in the process of trying to set up key-based logins too - good luck with it!

---

### Post by aldrino on 2012-01-13
I had the same problem, this works to me yeeeeaah!

> **kevdog said:**
> Have you tried on the client deleting the known_hosts file?

---

