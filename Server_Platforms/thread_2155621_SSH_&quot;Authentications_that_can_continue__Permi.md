---
title: "SSH &quot;Authentications that can continue:  Permission denied, please try again.&quot;"
date: 2013-06-18
forum: Server Platforms
---

### Post by StarScript on 2013-06-18
Hi,

I'm trying to set up a basic SSH for my NAS.

When I try to log in on my mac when I enter the password I keep getting 
```
[FONT=Menlo]debug3: packet_send2: adding 64 (len 53 padlen 11 extra_pad 64)[/FONT][FONT=Menlo]debug2: we sent a password packet, wait for reply[/FONT]
[FONT=Menlo]debug1: Authentications that can continue: [/FONT]
[FONT=Menlo]Permission denied, please try again.[/FONT]



```

The Debug shows this when I log in

```
[FONT=Menlo]OpenSSH_6.0p1, OSSLShim 0.9.8r 8 Dec 2011[/FONT][FONT=Menlo]debug1: Reading configuration data /etc/ssh_config[/FONT]
[FONT=Menlo]debug1: /etc/ssh_config line 20: Applying options for *[/FONT]
[FONT=Menlo]debug1: /etc/ssh_config line 102: Applying options for *[/FONT]
[FONT=Menlo]debug2: ssh_connect: needpriv 0[/FONT]
[FONT=Menlo]debug1: Connecting to Ubuntu-Nas [192.168.1.124] port 22.[/FONT]
[FONT=Menlo]debug1: Connection established.[/FONT]
[FONT=Menlo]debug3: Incorrect RSA1 identifier[/FONT]
[FONT=Menlo]debug3: Could not load "/Users/crawford/.ssh/id_rsa" as a RSA1 public key[/FONT]
[FONT=Menlo]debug1: identity file /Users/crawford/.ssh/id_rsa type 1[/FONT]
[FONT=Menlo]debug1: identity file /Users/crawford/.ssh/id_rsa-cert type -1[/FONT]
[FONT=Menlo]debug1: identity file /Users/crawford/.ssh/id_dsa type -1[/FONT]
[FONT=Menlo]debug1: identity file /Users/crawford/.ssh/id_dsa-cert type -1[/FONT]
[FONT=Menlo]debug1: Remote protocol version 2.0, remote software version OpenSSH_5.9p1 Debian-5ubuntu1.1[/FONT]
[FONT=Menlo]debug1: match: OpenSSH_5.9p1 Debian-5ubuntu1.1 pat OpenSSH_5*[/FONT]
[FONT=Menlo]debug1: Enabling compatibility mode for protocol 2.0[/FONT]
[FONT=Menlo]debug1: Local version string SSH-2.0-OpenSSH_6.0[/FONT]
[FONT=Menlo]debug2: fd 3 setting O_NONBLOCK[/FONT]
[FONT=Menlo]debug3: load_hostkeys: loading entries for host "ubuntu-nas" from file "/Users/crawford/.ssh/known_hosts"[/FONT]
[FONT=Menlo]debug3: load_hostkeys: found key type RSA in file /Users/crawford/.ssh/known_hosts:2[/FONT]
[FONT=Menlo]debug3: load_hostkeys: loaded 1 keys[/FONT]
[FONT=Menlo]debug3: order_hostkeyalgs: prefer hostkeyalgs: ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa[/FONT]
[FONT=Menlo]debug1: SSH2_MSG_KEXINIT sent[/FONT]
[FONT=Menlo]debug1: SSH2_MSG_KEXINIT received[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa,ssh-dss-cert-v01@openssh.com,ssh-dss-cert-v00@openssh.com,ssh-dss[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: [/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: [/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: first_kex_follows 0 [/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: reserved 0 [/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: none,zlib@openssh.com[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: none,zlib@openssh.com[/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: [/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: [/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: first_kex_follows 0 [/FONT]
[FONT=Menlo]debug2: kex_parse_kexinit: reserved 0 [/FONT]
[FONT=Menlo]debug2: mac_setup: found hmac-md5[/FONT]
[FONT=Menlo]debug1: kex: server->client aes128-ctr hmac-md5 none[/FONT]
[FONT=Menlo]debug2: mac_setup: found hmac-md5[/FONT]
[FONT=Menlo]debug1: kex: client->server aes128-ctr hmac-md5 none[/FONT]
[FONT=Menlo]debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent[/FONT]
[FONT=Menlo]debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP[/FONT]
[FONT=Menlo]debug2: dh_gen_key: priv key bits set: 128/256[/FONT]
[FONT=Menlo]debug2: bits set: 491/1024[/FONT]
[FONT=Menlo]debug1: SSH2_MSG_KEX_DH_GEX_INIT sent[/FONT]
[FONT=Menlo]debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY[/FONT]
[FONT=Menlo]debug1: Server host key: RSA 7e:39:ab:fd:2e:cf:33:39:dd:f9:1f:cf:2b:a2:81:4b[/FONT]
[FONT=Menlo]debug3: load_hostkeys: loading entries for host "ubuntu-nas" from file "/Users/crawford/.ssh/known_hosts"[/FONT]
[FONT=Menlo]debug3: load_hostkeys: found key type RSA in file /Users/crawford/.ssh/known_hosts:2[/FONT]
[FONT=Menlo]debug3: load_hostkeys: loaded 1 keys[/FONT]
[FONT=Menlo]debug3: load_hostkeys: loading entries for host "192.168.1.124" from file "/Users/crawford/.ssh/known_hosts"[/FONT]
[FONT=Menlo]debug3: load_hostkeys: found key type RSA in file /Users/crawford/.ssh/known_hosts:2[/FONT]
[FONT=Menlo]debug3: load_hostkeys: loaded 1 keys[/FONT]
[FONT=Menlo]debug1: Host 'ubuntu-nas' is known and matches the RSA host key.[/FONT]
[FONT=Menlo]debug1: Found key in /Users/crawford/.ssh/known_hosts:2[/FONT]
[FONT=Menlo]debug2: bits set: 510/1024[/FONT]
[FONT=Menlo]debug1: ssh_rsa_verify: signature correct[/FONT]
[FONT=Menlo]debug2: kex_derive_keys[/FONT]
[FONT=Menlo]debug2: set_newkeys: mode 1[/FONT]
[FONT=Menlo]debug1: SSH2_MSG_NEWKEYS sent[/FONT]
[FONT=Menlo]debug1: expecting SSH2_MSG_NEWKEYS[/FONT]
[FONT=Menlo]debug2: set_newkeys: mode 0[/FONT]
[FONT=Menlo]debug1: SSH2_MSG_NEWKEYS received[/FONT]
[FONT=Menlo]debug1: Roaming not allowed by server[/FONT]
[FONT=Menlo]debug1: SSH2_MSG_SERVICE_REQUEST sent[/FONT]
[FONT=Menlo]debug2: service_accept: ssh-userauth[/FONT]
[FONT=Menlo]debug1: SSH2_MSG_SERVICE_ACCEPT received[/FONT]
[FONT=Menlo]debug2: key: /Users/crawford/.ssh/id_rsa (0x7f8e11e006e0)[/FONT]
[FONT=Menlo]debug2: key: /Users/crawford/.ssh/id_dsa (0x0)[/FONT]
[FONT=Menlo]debug1: Authentications that can continue: [/FONT]
[FONT=Menlo]debug3: start over, passed a different list publickey,keyboard-interactive,password[/FONT]
[FONT=Menlo]debug3: preferred publickey,keyboard-interactive,password[/FONT]
[FONT=Menlo]debug3: authmethod_lookup publickey[/FONT]
[FONT=Menlo]debug3: remaining preferred: keyboard-interactive,password[/FONT]
[FONT=Menlo]debug3: authmethod_is_enabled publickey[/FONT]
[FONT=Menlo]debug1: Next authentication method: publickey[/FONT]
[FONT=Menlo]debug1: Offering RSA public key: /Users/crawford/.ssh/id_rsa[/FONT]
[FONT=Menlo]debug3: send_pubkey_test[/FONT]
[FONT=Menlo]debug2: we sent a publickey packet, wait for reply[/FONT]
[FONT=Menlo]debug1: Authentications that can continue: [/FONT]
[FONT=Menlo]debug1: Trying private key: /Users/crawford/.ssh/id_dsa[/FONT]
[FONT=Menlo]debug3: no such identity: /Users/crawford/.ssh/id_dsa[/FONT]
[FONT=Menlo]debug2: we did not send a packet, disable method[/FONT]
[FONT=Menlo]debug3: authmethod_lookup keyboard-interactive[/FONT]
[FONT=Menlo]debug3: remaining preferred: password[/FONT]
[FONT=Menlo]debug3: authmethod_is_enabled keyboard-interactive[/FONT]
[FONT=Menlo]debug1: Next authentication method: keyboard-interactive[/FONT]
[FONT=Menlo]debug2: userauth_kbdint[/FONT]
[FONT=Menlo]debug2: we sent a keyboard-interactive packet, wait for reply[/FONT]
[FONT=Menlo]debug1: Authentications that can continue: [/FONT]
[FONT=Menlo]debug3: userauth_kbdint: disable: no info_req_seen[/FONT]
[FONT=Menlo]debug2: we did not send a packet, disable method[/FONT]
[FONT=Menlo]debug3: authmethod_lookup password[/FONT]
[FONT=Menlo]debug3: remaining preferred: [/FONT]
[FONT=Menlo]debug3: authmethod_is_enabled password[/FONT]
[FONT=Menlo]debug1: Next authentication method: password[/FONT]
```

I have my ssh_config set up as this:```


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
#   ForwardAgent yes
#   ForwardX11 yes
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication yes
#   RSAAuthentication no
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
#  IdentityFile ~/.ssh/id_dsa
#  Port 22
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
#    SendEnv LANG LC_*
#    HashKnownHosts yes
#    GSSAPIAuthentication no
#    GSSAPIDelegateCredentials no

```

And finally sshd_config as shown:```
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
PermitRootLogin yes
StrictModes yes


RSAAuthentication no
PubkeyAuthentication no
#AuthorizedKeysFile    %h/.ssh/authorized_keys


# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication yes
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
UseLogin yes


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

Can some one point out where I have gone wrong in my configuration? 
I would like just to use the user login for the password rather that use public and private keys, the server is only connected to the LAN 

Many Thanks

---

### Post by CharlesA on 2013-06-18
> **StarScript said:**
> Hi,

And finally sshd_config as shown:```
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
PermitRootLogin yes
StrictModes yes


RSAAuthentication no
**[COLOR="#FF0000"]PubkeyAuthentication no[/COLOR]**
#AuthorizedKeysFile    %h/.ssh/authorized_keys


# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication yes
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
**[COLOR="#FF0000"]PasswordAuthentication no[/COLOR]**


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
UseLogin yes


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

Can some one point out where I have gone wrong in my configuration? 
I would like just to use the user login for the password rather that use public and private keys, the server is only connected to the LAN 

Many Thanks

You have no authentication methods available.

Change PasswordAuthentication no to PasswordAuthentication yes and restart ssh, then try to connect.

```
sudo service ssh restart
```

---

