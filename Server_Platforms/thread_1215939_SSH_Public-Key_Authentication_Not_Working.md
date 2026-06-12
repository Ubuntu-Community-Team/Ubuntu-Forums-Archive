---
title: "SSH Public-Key Authentication Not Working"
date: 2009-07-17
forum: Server Platforms
---

### Post by DanYoSon on 2009-07-17
I am working a basic file server to use at work to share files and need to be able to access it remotely. SSH is working fine with a password but as soon as i try to use public-key it fails and bumps me to password. 

I followed this tutorial for setting it up [https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html) to set it up.

here is some info i have seen being requested in other posts

Output of ssh daniel@192.168.2.150 -vvv

> OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.2.150 [192.168.2.150] port 22.
debug1: Connection established.
debug1: identity file /home/daniel/.ssh/identity type -1
debug1: identity file /home/daniel/.ssh/id_rsa type -1
debug3: Not a RSA1 key file /home/daniel/.ssh/id_dsa.
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
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/daniel/.ssh/id_dsa type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
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
debug2: dh_gen_key: priv key bits set: 125/256
debug2: bits set: 522/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/daniel/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug1: Host '192.168.2.150' is known and matches the RSA host key.
debug1: Found key in /home/daniel/.ssh/known_hosts:1
debug2: bits set: 478/1024
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
debug2: key: /home/daniel/.ssh/id_dsa (0xb9542be8)
debug2: key: /home/daniel/.ssh/identity ((nil))
debug2: key: /home/daniel/.ssh/id_rsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/daniel/.ssh/id_dsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/daniel/.ssh/identity
debug3: no such identity: /home/daniel/.ssh/identity
debug1: Trying private key: /home/daniel/.ssh/id_rsa
debug3: no such identity: /home/daniel/.ssh/id_rsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
let me know if any more info is needed
i am new to this so any info would be greatly appreciated.
thanks

---

### Post by ktrnka on 2009-07-18
I had a problem like this quite a while ago and the way I solved it was I renamed my authorized_keys to authorized_keys2. If that does not work, I would suggest using rsa keys. To do so:

```
ssh-keygen -t rsa -b 4096
```

When it asks for a passphrase just hit enter as before.

I prefer to copy my keys manually instead of the ssh-copy-id.

```
scp ~/.ssh/id_rsa.pub username@remotehost:
```

ssh/login to your remote server and then run 

```
cat id_rsa.pub >> .ssh/authorized_keys
```

then remove the key you copied.

```
rm id_rsa.pub
```


That should be it.

Let me know how it goes

---

### Post by DanYoSon on 2009-07-18
I first tryed changing the name of authorized_keys and that did not effect it then i set up rsa keys useing your instructions and this did not change it either i am beginning to think that there is a problem with the ssh-keygen is that possible.

the debug has changed a bit:

```
daniel@daniel:~$ ssh daniel@192.168.2.150 -vvv
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.2.150 [192.168.2.150] port 22.
debug1: Connection established.
debug1: identity file /home/daniel/.ssh/identity type -1
debug3: Not a RSA1 key file /home/daniel/.ssh/id_rsa.
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
debug1: identity file /home/daniel/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-4096
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-4096
debug1: identity file /home/daniel/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
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
debug2: dh_gen_key: priv key bits set: 122/256
debug2: bits set: 499/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/daniel/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug1: Host '192.168.2.150' is known and matches the RSA host key.
debug1: Found key in /home/daniel/.ssh/known_hosts:1
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
debug2: key: /home/daniel/.ssh/id_rsa (0xb8273ab8)
debug2: key: /home/daniel/.ssh/identity ((nil))
debug2: key: /home/daniel/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/daniel/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/daniel/.ssh/identity
debug3: no such identity: /home/daniel/.ssh/identity
debug1: Trying private key: /home/daniel/.ssh/id_dsa
debug3: no such identity: /home/daniel/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
daniel@192.168.2.150's password: 
debug3: packet_send2: adding 64 (len 59 padlen 5 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 1
debug3: tty_make_modes: ospeed 38400
debug3: tty_make_modes: ispeed 38400
debug1: Sending environment.
debug3: Ignored env ORBIT_SOCKETDIR
debug3: Ignored env SSH_AGENT_PID
debug3: Ignored env GPG_AGENT_INFO
debug3: Ignored env TERM
debug3: Ignored env SHELL
debug3: Ignored env XDG_SESSION_COOKIE
debug3: Ignored env GTK_RC_FILES
debug3: Ignored env WINDOWID
debug3: Ignored env GTK_MODULES
debug3: Ignored env USER
debug3: Ignored env LS_COLORS
debug3: Ignored env GNOME_KEYRING_SOCKET
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env SESSION_MANAGER
debug3: Ignored env USERNAME
debug3: Ignored env DESKTOP_SESSION
debug3: Ignored env PATH
debug3: Ignored env GDM_XSERVER_LOCATION
debug3: Ignored env PWD
debug1: Sending env LANG = en_CA.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env GNOME_KEYRING_PID
debug3: Ignored env GDM_LANG
debug3: Ignored env GDMSESSION
debug3: Ignored env HISTCONTROL
debug3: Ignored env SHLVL
debug3: Ignored env HOME
debug3: Ignored env GNOME_DESKTOP_SESSION_ID
debug3: Ignored env LOGNAME
debug3: Ignored env XDG_DATA_DIRS
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS
debug3: Ignored env LESSOPEN
debug3: Ignored env WINDOWPATH
debug3: Ignored env DISPLAY
debug3: Ignored env LESSCLOSE
debug3: Ignored env XAUTHORITY
debug3: Ignored env COLORTERM
debug3: Ignored env _
debug2: channel 0: request shell confirm 1
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel_input_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_confirm: type 99 id 0
debug2: shell request accepted on channel 0

```any other ideas??

---

### Post by ktrnka on 2009-07-18
Alright then please attach your /etc/ssh/sshd_config file and we will see if it is something in there.

One thing to try until I reply back is try doing all of this on the remote server and connect to localhost.

So ssh into 192.168.2.150 as daniel and enter your password. Once there: ```
ssh-keygen -t rsa -b 4096
```

If it prompts to overwrite make sure you do.

Then backup the current authorized_keys to authorized_keys.backup

```
mv ~/.ssh/authorized_keys ~/.ssh/authorized_keys.backup
```

Then we will cat the id_rsa.pub into a new authorized_keys file

```
cat ~/.ssh/id_rsa.pub > ~/.ssh/authroized_keys
```

Once that is done ssh to localhost.

```
ssh localhost
```

If that doesn't work then you have a problem with your sshd_conf file. If it does work you could try to gen the key on the remote server and then copy it back to your machine. Let me know if it does or does not work and we will proceed from there.

---

### Post by ArchCast on 2009-07-18
Which files are in your remote machine's ~/home/.ssh directory?  Also, did you do a md5sum on the id_dsa.pub and id_dsa files on your server and remote machine to make sure that they match?

---

### Post by DanYoSon on 2009-07-18
Ok sshing localhost from the remote server works. but when i go to transfer the key to my laptop i get this 

```
daniel@SERVER:~/.ssh$ scp id_rsa daniel@192.168.2.5:
ssh: connect to host 192.168.2.5 port 22: Connection refused
lost connection

```is it possible that a firewall on my laptop is causing a problem???

here are the config files 
laptop
```

# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults f$
# users, and the values can be changed in per-user configuration fil$
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehe$
# list of available options, their meanings and defaults, please see$
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
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes$
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no
```Remote Server

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
AuthorizedKeysFile      %h/.ssh/authorized_keys

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
```@ArchCast the only file that was in the remote machines ~/.ssh directory was authorized_keys. also no i have not done a md5sum. how would i go about doing that. i am still learning.

thanks hope this info helps

---

### Post by ktrnka on 2009-07-19
If you are trying to transfer the key back to you, you can use sftp or scp. To scp both public and private keys back to your laptop, open a new terminal from your laptop and run:

```
scp daniel@192.168.2.150:/home/daniel/.ssh/id_rsa* .
```

You can also get it via sftp with:

```
sftp daniel@192.168.2.150
```

at the > change directory to .ssh and then run

```
get id_rsa*
```

Your ssh conf files look ok.


So to clear this up:

The id_rsa keys must be in your current user's /home/YOURusername/.ssh/ on your laptop

You must have an id_rsa and an id_rsa.pub

The ONLY key needs to be copied to the 192.168.2.150 machine is the id_rsa.pub from your laptop's /home/YOURusername/.ssh/id_rsa.pub 

That file then needs to be put into authorized_keys file on the remote machine with:
(while ssh'd into the 192.168.2.150 machine)
```
cat id_rsa.pub >> ~/.ssh/authorized_keys
```

I have a feeling that you may be getting the keys mixed up.

---

### Post by ktrnka on 2009-07-19
Mini tutorial --> Tailored for DanYoSon

Starting fresh from your laptop:

```
ssh-keygen -t rsa -b 4096
``` (Creates 4MB RSA key)

Hit enter twice for blank passphrases (You didn't set a passphrase for your keys did you?)

If it prompts to overwrite, hit y then enter.

Then (The method I prefer is manually copying it over) copy ONLY the id_rsa.pub key over to the remote machine with:

```
scp ~/.ssh/id_rsa.pub daniel@192.168.2.150:
``` (Don't forget the colon at the end)

Then ssh into the remote machine

```
ssh daniel@192.168.2.150
```

Enter your password then cat the id_rsa.pub key on the 192.168.2.150 machine into /home/daniel/.ssh/authorized_keys

At the prompt:
```
cat id_rsa.pub > /home/daniel/.ssh/authorized_keys
``` (One > overwrites the current file/creates a new one after cat. Two >> appends to the end of the file)

The remove the id_rsa.pub from /home/daniel/ on the 192.168.2.150 machine. (Since you're done with it now) (and security reasons)

Now the keys have been properly setup. Test it by opening a new terminal on your laptop and execute:

```
ssh daniel@192.168.2.150
```

Good Luck

---

### Post by DanYoSon on 2009-07-19
ok i followed your tutorial and i am still getting an error but i think we are getting somewhere because it as far as i can tell is recognizing the keys. 

here is the new debug output

```
daniel@daniel:~$ ssh daniel@192.168.2.150 -vv
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.2.150 [192.168.2.150] port 22.
debug1: Connection established.
debug1: identity file /home/daniel/.ssh/identity type -1
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug2: key_type_from_name: unknown key type '-----END'
debug1: identity file /home/daniel/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-4096
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-4096
debug1: identity file /home/daniel/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
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
debug2: dh_gen_key: priv key bits set: 137/256
debug2: bits set: 511/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.2.150' is known and matches the RSA host key.
debug1: Found key in /home/daniel/.ssh/known_hosts:1
debug2: bits set: 538/1024
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
debug2: key: /home/daniel/.ssh/id_rsa (0xb936eab8)
debug2: key: /home/daniel/.ssh/identity ((nil))
debug2: key: /home/daniel/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: /home/daniel/.ssh/id_rsa
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/daniel/.ssh/identity
debug1: Trying private key: /home/daniel/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
```

i also have been doing some more crawling of the forums and found this [bug]("https://bugs.launchpad.net/ubuntu/%2Bsource/openssh/%2Bbug/201786") it looks similar and there are some workarounds but they are not clear to me what i am to do. 

another thing is that i cannot ssh localhost on my laptop it says connection refused

thanks for you ongoing patience with me on this.

---

### Post by jerome1232 on 2009-07-19
The easiest method is to generate the keys on the client then transfer the public key to the server.

I notice in the log it tried three keys and none of them authenticated, so it sounds like the public key isn't in ~/.ssh/authorized_keys on the server to me.

A couple of things to check.

Ensure that the server has the public key in ~/.ssh/authorized_keys (that's what the cat id_rsa.pub > ~/.ssh/authorized_keys step does)

and b ensure the client has the private key in ~/.ssh/id_rsa

If those two things are true you should be golden. I personally keep passphrases on my keys for security reasons (if someone get's my private key they will have to brute force the passphrase on it) Leaving the public key laying around is **not** a security issue, nothing useful can be done with it by an attacker.

---

### Post by DanYoSon on 2009-07-19
the files are in the correct places and right now for testing purposes i am not useing a passphrase it is only on an internal network. when it goes online i will have a passphrase. 

do you have any comments on that bug thread it is a bit old but it might be a good thing for me to try but i dont quite understand what they are doing 

thanks

---

### Post by ktrnka on 2009-07-21
Just read about the bug. The bug appears to be caused by seahorse.

The Fix:

```
sudo nano /etc/X11/Xsession.d/60seahorse
```

Then unset SSH_AUTH_SOCK like so:

```
SSH_AUTH_SOCK=0
```

---

### Post by theDaveTheRave on 2009-07-22
Hello all.

I have added an SSH to a "server" that I use at work, this is now being moved to a new location.

I need to ensure that the logons are secure etc (the local logon passwords are fairly strong (I think so anyway, combination of Upper and Lower case letters intermingled with numbers etc).

Anyway, I (and my colleagues) normally log onto this terminal using Putty from a windows (Vista) terminal.

If I get a request for one of the other users to have access from their pc I believe I can simply copy over the public key that I generated, but where do I copy the file to?

Also, can I use the same public key for all the user accounts on the system? I have a general user on the system and an admin, mostly we just need to make sure that the backup logs and certain other stuff is working OK so there will not be a requirement to log in as an admin.

Basically what I want it this.

single public key that can be copied to each terminal for anyone who needs access to the "server", where do I copy this key to on a windows system?

Each user on the "server" has their own password, so each time someone logs in they can decide to log in as either the "basic username" or "admin" depending on what they need to do.

Result: Access is dependant on the public key, and thee users password.

How do I confirm that this is working?

Currently I followed the instruction here [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) but I didn't copy the key onto my windows machine but could still log on - that isn't what I wanted / expected.

Thanks for the help

David

---

### Post by jerome1232 on 2009-07-22
The public keys get's placed on the server, under ~/.ssh/authorized_keys.

The Private key gets placed on the client computer. I would make one set of keys for every user, and password protect the keys.

Putty has a tool called puttygen which can import openssh keys and convert them to putty's format so it can understand them.

I hope this helps a bit.

---

### Post by DanYoSon on 2009-07-22
in the Xsession.d folder there is no 60seahorse file should i create it or is it named different here is a list of all the files in the folder

```
daniel@daniel:/etc/X11/Xsession.d$ ls -al
total 68
drwxr-xr-x 2 root root 4096 2009-07-17 08:08 .
drwxr-xr-x 9 root root 4096 2009-07-20 08:14 ..
-rw-r--r-- 1 root root 1878 2008-06-24 22:05 20x11-common_process-args
-rw-r--r-- 1 root root  899 2008-06-24 22:05 30x11-common_xresources
-rw-r--r-- 1 root root  187 2008-06-24 22:05 40x11-common_xsessionrc
-rw-r--r-- 1 root root 1561 2008-06-24 22:05 50x11-common_determine-startup
-rw-r--r-- 1 root root  197 2009-04-02 18:03 52libcanberra-gtk-module_add-to-gtk-modules
-rw-r--r-- 1 root root  361 2009-04-08 17:41 55gnome-session_gnomerc
-rw-r--r-- 1 root root  179 2009-04-14 06:45 60seahorse-plugins
-rw-r--r-- 1 root root  151 2009-03-18 00:24 60x11-common_localhost
-rw-r--r-- 1 root root   80 2008-10-08 10:45 60xdg-user-dirs-update
-rw-r--r-- 1 root root  329 2009-04-08 20:11 70pulseaudio
-rw-r--r-- 1 root root  381 2009-01-27 09:39 75dbus_dbus-launch
-rw-r--r-- 1 root root 2307 2008-01-08 05:41 80im-switch
-rw-r--r-- 1 root root  274 2009-03-27 04:27 90consolekit
-rw-r--r-- 1 root root  642 2008-08-05 19:37 90x11-common_ssh-agent
-rw-r--r-- 1 root root  166 2008-06-24 22:05 99x11-common_start
```

thanks

---

### Post by theDaveTheRave on 2009-07-22
> **jerome1232 said:**
> 
Putty has a tool called puttygen which can import openssh keys and convert them to putty's format so it can understand them

does putty do this automatically when you first log into the remote machine?

I can confirm for a fact that I haven't copied anyything onto the windows machine, I do in fact have a copy of the public key on my usb drive but never copied it too the windows machine, which was quite happy let me log in via putty?

I'm obviously missing something, but if this is supposed to be "Secure SHell" I think I'd like to know what "insecure" was like!

David

---

### Post by tsumaru on 2009-07-22
i think by default (at least openssh) if you fail to log in with a key it reverts to password auth. 

You mentioned your key is on your usb drive, does putty know its there? if so it might be using it by default.

---

### Post by theDaveTheRave on 2009-07-22
> **tsumaru said:**
> i think by default (at least openssh) if you fail to log in with a key it reverts to password auth. 

That is what has happened then....

[quote
You mentioned your key is on your usb drive, does putty know its there? if so it might be using it by default.[/QUOTE]

Not unless vista has the ability to read a key that isn't plugged into the USB drive - which would make me switch back to vista as that would be a great benefit, not having to take my key out of my pocket :cool;

[and not it isn't on blue tooth either ;) ]

David

---

### Post by tsumaru on 2009-07-22
My advice, 

Generate public and private keys (using the post on the previous page)

in your users home directory on the remote server "/home/<your user>" 

```
cd .ssh
echo "" > authorized_keys
chmod u=rw,g=,o= authorized_keys
```

Assuming you made an rsa key, copy the contents of id_rsa.pub into the newly created authorized_keys file

i am not 100% sure on how to use putty to convert to a compatible key but on linux, you would make sure id_rsa is in your desktop's .ssh folder and make sure its chmodded correctly:

```
chmod u=rw,g=,o= id_rsa
```

Once this is all done simply try to ssh to the remote server and it should let you in without asking for a password (if you used a pass phrase on the key then it will ask you for that instead of a password)

Hope this helps, if not just let me know :)

---

### Post by jerome1232 on 2009-07-22
Putty won't use openssh keys by default, you would have to open puttygen, import the private key, then save it as a putty private key, then when you start a session in putty there is an option to use a key for authentication.

edit: added some screenshots of putty and puttygen

---

### Post by theDaveTheRave on 2009-07-22
Jerome and Tsumaru.

I think your advice will get things sorted out.

I guess I need to download the putty key generator..... I'll report back sometime tomorrow on my experience.

David

---

### Post by ktrnka on 2009-07-22
WHOA WHOA WHOA this thread just got jacked! WTH?!

---

