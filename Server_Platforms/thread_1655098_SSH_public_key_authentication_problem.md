---
title: "SSH public key authentication problem"
date: 2010-12-29
forum: Server Platforms
---

### Post by niels_linux_forum on 2010-12-29
Hey everybody,

I'm having a very annoying problem setting up my SSH server using public key authentication to login in.

This my setup :

I have a macbook and a ubuntu server running.

I first tried connecting to my macbook from my ubuntu server using public key authentication.
And that worked out great.

But now I'm trying to set it up the other way around, that's actually the way I want it to run. 
And that's where the problem starts.

When I enter the password to read the public key, the server is always complains that I'm using the wrong password.

I tried using an empty password and a very simple password : "test".
I used this command to generate my key :

 - ssh-keygen -t rsa -b 2048 -C "name"

And in both cases I get the same error : "bad passphrase given, try again..."
I checked the permissions on my key files, authorized_keys and .ssh directory on both sides.

these are the settings of my sshd_config file : 
```
### Networking options ###
#standard port
Port 22
# Restrict to listen only ipv4 inet = IPv4, inet6 = IPv6 any = both
AddressFamily inet

# Listen only to this interface
ListenAddress 192.168.1.50

# Only use protocol 2
Protocol 2

# Disable XForwarding
X11Forwarding no

# Disable TCPKeepAlive and use ClientAliveInterval instead to prevent TCP Spoofing attacks
TCPKeepAlive no
ClientAliveInterval 600
ClientAliveCountMax 3

### Networking options ###

### Key Configurations ###

# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key

#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Use public key authentication
PubkeyAuthentication yes
AuthorizedKeysFile      %h/.ssh/authorized_keys2

# Disable black listed key usage (update your keys!)
PermitBlacklistedKeys no

#### Key Configuration ####

#### Authentication ####

# Whitelist allowed users
# AllowUsers user1 user2

# Two minutes to enter your key passphrase
LoginGraceTime 120

# No root login
PermitRootLogin yes

# Force permissions checks on keyfiles and directories
StrictModes yes

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes

# similar for protocol version 2
HostbasedAuthentication no

# Don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Disable challenge and response auth. Unessisary when using keys
ChallengeResponseAuthentication yes

# Disable the use of passwords completly, only use public/private keys
PasswordAuthentication yes

# Using keys, no need for PAM. Also allows SSHD to be run as a non-root user
UsePAM no

# Don't use login(1)
UseLogin no

#### Authentication ####

#### Misc ####

# Logging
SyslogFacility AUTH
LogLevel DEBUG3

# Print the last time the user logged in
PrintLastLog yes
PrintMotd yes

MaxAuthTries 4

MaxStartups 10:30:60

# Display login banner
Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

#### Misc ####

```

And this is the output I got when using ssh -vv .....

```

....
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Next authentication method: publickey
debug1: Offering public key: /Users/niels/.ssh/id_rsa
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Offering public key: test_rsa_2.pub
debug2: we sent a publickey packet, wait for reply
debug1: Server accepts key: pkalg ssh-rsa blen 277
debug2: input_userauth_pk_ok: fp e3:0c:7f:b2:c0:6d:62:5c:00:34:7e:36:a7:0b:6b:ea
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
debug2: bad passphrase given, try again...
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
debug2: bad passphrase given, try again...
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
debug2: bad passphrase given, try again...
debug2: we did not send a packet, disable method
debug1: Next authentication method: keyboard-interactive
debug2: userauth_kbdint
debug2: we sent a keyboard-interactive packet, wait for reply
....

```



Does anybody know how I can solve this problem ?

---

### Post by tynin on 2010-12-29
What does your /var/log/auth.log say when you are attempting this? It might give us a better picture.

---

### Post by niels_linux_forum on 2010-12-29
This is in the auth.log for sshd :

I specified DEBUG3 as logging level, but I captured the log only after I tried to log in with the public key.

```
Dec 29 14:57:48 ubuntu server sshd[12687]: debug1: do_cleanup
Dec 29 14:57:50 ubuntu server sshd[6542]: debug3: fd 4 is not O_NONBLOCK
Dec 29 14:57:50 ubuntu server sshd[6542]: debug1: Forked child 12694.
Dec 29 14:57:50 ubuntu server sshd[6542]: debug3: send_rexec_state: entering fd = 7 config len 834
Dec 29 14:57:50 ubuntu server sshd[6542]: debug3: ssh_msg_send: type 0
Dec 29 14:57:50 ubuntu server sshd[6542]: debug3: send_rexec_state: done
Dec 29 14:57:50 ubuntu server sshd[12694]: debug1: rexec start in 4 out 4 newsock 4 pipe 6 sock 7
Dec 29 14:57:50 ubuntu server sshd[12694]: debug1: inetd sockets after dupping: 3, 3
Dec 29 14:57:50 ubuntu server sshd[12694]: Connection from 94.226.16.213 port 59925
Dec 29 14:57:50 ubuntu server sshd[12694]: debug1: Client protocol version 2.0; client software version OpenSSH_5.2
Dec 29 14:57:50 ubuntu server sshd[12694]: debug1: match: OpenSSH_5.2 pat OpenSSH*
Dec 29 14:57:50 ubuntu server sshd[12694]: debug1: Enabling compatibility mode for protocol 2.0
Dec 29 14:57:50 ubuntu server sshd[12694]: debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
Dec 29 14:57:50 ubuntu server sshd[12694]: debug2: fd 3 setting O_NONBLOCK
Dec 29 14:57:50 ubuntu server sshd[12694]: debug2: Network child is on pid 12695
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: preauth child monitor started
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_request_receive entering
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: monitor_read: checking request 0
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_answer_moduli: got parameters: 1024 1024 8192
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_request_send entering: type 1
Dec 29 14:57:50 ubuntu server sshd[12694]: debug2: monitor_read: 0 used once, disabling now
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_request_receive entering
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: monitor_read: checking request 5
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_answer_sign
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_answer_sign: signature 0x7fd35bee7e40(271)
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_request_send entering: type 6
Dec 29 14:57:50 ubuntu server sshd[12694]: debug2: monitor_read: 5 used once, disabling now
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_request_receive entering
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: monitor_read: checking request 7
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_answer_pwnamallow
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: Trying to reverse map address 94.226.16.213.
Dec 29 14:57:50 ubuntu server sshd[12694]: debug2: parse_server_config: config reprocess config len 834
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: auth_shadow_acctexpired: today 14972 sp_expire -1 days left -14973
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: account expiration disabled
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_answer_pwnamallow: sending MONITOR_ANS_PWNAM: 1
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_request_send entering: type 8
Dec 29 14:57:50 ubuntu server sshd[12694]: debug2: monitor_read: 7 used once, disabling now
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_request_receive entering
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: monitor_read: checking request 3
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_answer_authserv: service=ssh-connection, style=, role=
Dec 29 14:57:50 ubuntu server sshd[12694]: debug2: monitor_read: 3 used once, disabling now
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_request_receive entering
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: monitor_read: checking request 9
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_request_send entering: type 10
Dec 29 14:57:50 ubuntu server sshd[12694]: debug2: monitor_read: 9 used once, disabling now
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_request_receive entering
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: monitor_read: checking request 11
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_answer_authpassword: sending result 0
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_request_send entering: type 12
Dec 29 14:57:50 ubuntu server sshd[12694]: Failed none for niels from 94.226.16.213 port 59925 ssh2
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_request_receive entering
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: monitor_read: checking request 21
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_answer_keyallowed entering
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_answer_keyallowed: key_from_blob: 0x7fd35bee6ac0
Dec 29 14:57:50 ubuntu server sshd[12694]: debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
Dec 29 14:57:50 ubuntu server sshd[12694]: debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
Dec 29 14:57:50 ubuntu server sshd[12694]: debug1: temporarily_use_uid: 1000/1000 (e=0/0)
Dec 29 14:57:50 ubuntu server sshd[12694]: debug1: trying public key file /home/niels/.ssh/authorized_keys2
Dec 29 14:57:50 ubuntu server sshd[12694]: debug1: fd 4 clearing O_NONBLOCK
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: secure_filename: checking '/home/niels/.ssh'
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: secure_filename: checking '/home/niels'
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: secure_filename: terminating check at '/home/niels'
Dec 29 14:57:50 ubuntu server sshd[12694]: debug1: restore_uid: 0/0
Dec 29 14:57:50 ubuntu server sshd[12694]: debug2: key not found
Dec 29 14:57:50 ubuntu server sshd[12694]: debug1: temporarily_use_uid: 1000/1000 (e=0/0)
Dec 29 14:57:50 ubuntu server sshd[12694]: debug1: trying public key file /home/niels/.ssh/authorized_keys2
Dec 29 14:57:50 ubuntu server sshd[12694]: debug1: fd 4 clearing O_NONBLOCK
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: secure_filename: checking '/home/niels/.ssh'
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: secure_filename: checking '/home/niels'
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: secure_filename: terminating check at '/home/niels'
Dec 29 14:57:50 ubuntu server sshd[12694]: debug1: restore_uid: 0/0
Dec 29 14:57:50 ubuntu server sshd[12694]: debug2: key not found
Dec 29 14:57:50 ubuntu server sshd[12694]: Failed publickey for niels from 94.226.16.213 port 59925 ssh2
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_answer_keyallowed: key 0x7fd35bee6ac0 is not allowed
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_request_send entering: type 22
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_request_receive entering
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: monitor_read: checking request 21
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_answer_keyallowed entering
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_answer_keyallowed: key_from_blob: 0x7fd35bee6a80
Dec 29 14:57:50 ubuntu server sshd[12694]: debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
Dec 29 14:57:50 ubuntu server sshd[12694]: debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
Dec 29 14:57:50 ubuntu server sshd[12694]: debug1: temporarily_use_uid: 1000/1000 (e=0/0)
Dec 29 14:57:50 ubuntu server sshd[12694]: debug1: trying public key file /home/niels/.ssh/authorized_keys2
Dec 29 14:57:50 ubuntu server sshd[12694]: debug1: fd 4 clearing O_NONBLOCK
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: secure_filename: checking '/home/niels/.ssh'
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: secure_filename: checking '/home/niels'
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: secure_filename: terminating check at '/home/niels'
Dec 29 14:57:50 ubuntu server sshd[12694]: debug1: matching key found: file /home/niels/.ssh/authorized_keys2, line 2
Dec 29 14:57:50 ubuntu server sshd[12694]: Found matching RSA key: e3:0c:7f:b2:c0:6d:62:5c:00:34:7e:36:a7:0b:6b:ea
Dec 29 14:57:50 ubuntu server sshd[12694]: debug1: restore_uid: 0/0
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_answer_keyallowed: key 0x7fd35bee6a80 is allowed
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_request_send entering: type 22
Dec 29 14:57:50 ubuntu server sshd[12694]: debug3: mm_request_receive entering
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 80 bytes for a total of 3554399
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 4144 bytes for a total of 3558543
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1376 bytes for a total of 3559919
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1632 bytes for a total of 3561551
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 368 bytes for a total of 3561919
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 4144 bytes for a total of 3566063
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 2592 bytes for a total of 3568655
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1984 bytes for a total of 3570639
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1616 bytes for a total of 3572255
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 864 bytes for a total of 3573119
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1072 bytes for a total of 3574191
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1040 bytes for a total of 3575231
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1104 bytes for a total of 3576335
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1104 bytes for a total of 3577439
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1136 bytes for a total of 3578575
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1056 bytes for a total of 3579631
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1584 bytes for a total of 3581215
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 3582399
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 688 bytes for a total of 3583087
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1104 bytes for a total of 3584191
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1088 bytes for a total of 3585279
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 3586463
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1104 bytes for a total of 3587567
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 3588751
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 976 bytes for a total of 3589727
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1120 bytes for a total of 3590847
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1040 bytes for a total of 3591887
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1328 bytes for a total of 3593215
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 3594399
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1424 bytes for a total of 3595823
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 3597007
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 3598191
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 3599375
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1056 bytes for a total of 3600431
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 3601615
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 3602799
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1072 bytes for a total of 3603871
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 3605055
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 3606239
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 3607423
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 912 bytes for a total of 3608335
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1072 bytes for a total of 3609407
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 3610591
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 3611743
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 3612927
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 3614111
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1072 bytes for a total of 3615183
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 3616335
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1104 bytes for a total of 3617439
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 3618591
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 3619871
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 3621023
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1072 bytes for a total of 3622095
Dec 29 14:57:59 ubuntu server sshd[4928]: debug2: channel 0: rcvd adjust 50816
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1296 bytes for a total of 3623391
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1968 bytes for a total of 3625359
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1328 bytes for a total of 3626687
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 3627855
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 3629007
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1104 bytes for a total of 3630111
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 3631263
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1584 bytes for a total of 3632847
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 3634063
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1136 bytes for a total of 3635199
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1072 bytes for a total of 3636271
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1136 bytes for a total of 3637407
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1056 bytes for a total of 3638463
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1088 bytes for a total of 3639551
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 3640719
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1040 bytes for a total of 3641759
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 3642943
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1056 bytes for a total of 3643999
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 3645279
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 3646527
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1072 bytes for a total of 3647599
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 3648767
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1104 bytes for a total of 3649871
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1120 bytes for a total of 3650991
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 928 bytes for a total of 3651919
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 896 bytes for a total of 3652815
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 3654095
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1088 bytes for a total of 3655183
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1120 bytes for a total of 3656303
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1120 bytes for a total of 3657423
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 992 bytes for a total of 3658415
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1392 bytes for a total of 3659807
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 3660959
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1088 bytes for a total of 3662047
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 3663215
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 3664367
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1072 bytes for a total of 3665439
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1136 bytes for a total of 3666575
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1104 bytes for a total of 3667679
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 3668847
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 3669999
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1200 bytes for a total of 3671199
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1120 bytes for a total of 3672319
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 3673471
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1088 bytes for a total of 3674559
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1392 bytes for a total of 3675951
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 3677215
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1072 bytes for a total of 3678287
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 3679455
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 3680639
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 3681887
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 624 bytes for a total of 3682511
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1104 bytes for a total of 3683615
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1104 bytes for a total of 3684719
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1120 bytes for a total of 3685839
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1024 bytes for a total of 3686863
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 3688047
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 3689199
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1104 bytes for a total of 3690303
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1136 bytes for a total of 3691439
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3692671
Dec 29 14:57:59 ubuntu server sshd[4928]: debug2: channel 0: rcvd adjust 51194
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3693903
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1968 bytes for a total of 3695871
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1552 bytes for a total of 3697423
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 3698591
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 3699935
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1136 bytes for a total of 3701071
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1088 bytes for a total of 3702159
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 3703375
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1024 bytes for a total of 3704399
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 3705615
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1136 bytes for a total of 3706751
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1088 bytes for a total of 3707839
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1024 bytes for a total of 3708863
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1328 bytes for a total of 3710191
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 3711359
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1136 bytes for a total of 3712495
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1120 bytes for a total of 3713615
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1136 bytes for a total of 3714751
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1088 bytes for a total of 3715839
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1520 bytes for a total of 3717359
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1296 bytes for a total of 3718655
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 3719935
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 848 bytes for a total of 3720783
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1056 bytes for a total of 3721839
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 3722991
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 3724271
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1056 bytes for a total of 3725327
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1136 bytes for a total of 3726463
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1104 bytes for a total of 3727567
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 3728719
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1120 bytes for a total of 3729839
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1056 bytes for a total of 3730895
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 3732143
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 3733423
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1504 bytes for a total of 3734927
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 3736207
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 3737375
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 3738543
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 3739711
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 3740879
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1056 bytes for a total of 3741935
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1200 bytes for a total of 3743135
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 3744383
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1296 bytes for a total of 3745679
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 3746927
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 3748111
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 3749263
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1584 bytes for a total of 3750847
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1024 bytes for a total of 3751871
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1424 bytes for a total of 3753295
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 3754559
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3755791
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 3756959
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 3758111
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 3759327
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 3760575
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1200 bytes for a total of 3761775
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1376 bytes for a total of 3763151
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1312 bytes for a total of 3764463
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 3765807
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1520 bytes for a total of 3767327
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1728 bytes for a total of 3769055
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1520 bytes for a total of 3770575
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 3771839
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1536 bytes for a total of 3773375
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3774607
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1008 bytes for a total of 3775615
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3776847
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3778079
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3779311
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3780543
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3781775
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3783007
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1440 bytes for a total of 3784447
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1440 bytes for a total of 3785887
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1440 bytes for a total of 3787327
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1440 bytes for a total of 3788767
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 672 bytes for a total of 3789439
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 3790591
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1200 bytes for a total of 3791791
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 3793055
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 3794207
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 3795375
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 3796623
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1200 bytes for a total of 3797823
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1120 bytes for a total of 3798943
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 2016 bytes for a total of 3800959
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1856 bytes for a total of 3802815
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1584 bytes for a total of 3804399
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 3805679
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1088 bytes for a total of 3806767
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1312 bytes for a total of 3808079
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 3809327
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1120 bytes for a total of 3810447
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 3811663
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 3812927
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 3814175
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 3815327
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 3816575
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 3817839
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1360 bytes for a total of 3819199
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1744 bytes for a total of 3820943
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1632 bytes for a total of 3822575
Dec 29 14:57:59 ubuntu server sshd[4928]: debug2: channel 0: rcvd adjust 54722
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1376 bytes for a total of 3823951
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 2112 bytes for a total of 3826063
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1552 bytes for a total of 3827615
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 3828959
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1440 bytes for a total of 3830399
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3831631
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3832863
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3834095
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3835327
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3836559
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3837791
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3839023
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3840255
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3841487
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 3842831
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 2096 bytes for a total of 3844927
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1664 bytes for a total of 3846591
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1552 bytes for a total of 3848143
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 3849487
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3850719
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3851951
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3853183
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3854415
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3855647
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3856879
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1440 bytes for a total of 3858319
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3859551
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3860783
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3862015
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1664 bytes for a total of 3863679
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1552 bytes for a total of 3865231
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1440 bytes for a total of 3866671
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1120 bytes for a total of 3867791
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3869023
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3870255
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3871487
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3872719
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3873951
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1120 bytes for a total of 3875071
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3876303
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3877535
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3878767
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1440 bytes for a total of 3880207
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1552 bytes for a total of 3881759
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1776 bytes for a total of 3883535
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1440 bytes for a total of 3884975
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 3886319
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3887551
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3888783
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3890015
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3891247
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3892479
Dec 29 14:57:59 ubuntu server sshd[4928]: debug2: channel 0: rcvd adjust 55118
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 3893823
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 2096 bytes for a total of 3895919
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 3897263
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 3898607
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3899839
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3901071
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1440 bytes for a total of 3902511
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1664 bytes for a total of 3904175
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1440 bytes for a total of 3905615
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 3906959
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3908191
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3909423
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3910655
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3911887
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3913119
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3914351
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 3915695
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 3917039
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1120 bytes for a total of 3918159
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3919391
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1552 bytes for a total of 3920943
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1664 bytes for a total of 3922607
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1664 bytes for a total of 3924271
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 3925615
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 3926959
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3928191
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3929423
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3930655
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3931887
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3933119
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3934351
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3935583
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1440 bytes for a total of 3937023
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1440 bytes for a total of 3938463
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1776 bytes for a total of 3940239
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1552 bytes for a total of 3941791
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 3943135
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3944367
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3945599
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3946831
Dec 29 14:57:59 ubuntu server sshd[4928]: debug2: channel 0: rcvd adjust 55300
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 3948175
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 2096 bytes for a total of 3950271
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 3951615
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3952847
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3954079
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3955311
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3956543
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3957775
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1440 bytes for a total of 3959215
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3960447
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1552 bytes for a total of 3961999
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1440 bytes for a total of 3963439
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3964671
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3965903
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3967135
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3968367
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3969599
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3970831
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3972063
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 3973407
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1328 bytes for a total of 3974735
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1120 bytes for a total of 3975855
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3977087
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3978319
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3979551
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1552 bytes for a total of 3981103
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1776 bytes for a total of 3982879
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1776 bytes for a total of 3984655
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1200 bytes for a total of 3985855
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 3987071
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 3988415
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 3989663
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1136 bytes for a total of 3990799
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3992031
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1200 bytes for a total of 3993231
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 3994399
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3995631
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 3996863
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1568 bytes for a total of 3998431
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1568 bytes for a total of 3999999
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1680 bytes for a total of 4001679
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 4002895
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 4004239
Dec 29 14:57:59 ubuntu server sshd[4928]: debug2: channel 0: rcvd adjust 55571
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 4005583
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 2112 bytes for a total of 4007695
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 4009039
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4010287
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4011535
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4012783
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4014031
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 4015375
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1632 bytes for a total of 4017007
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1648 bytes for a total of 4018655
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1376 bytes for a total of 4020031
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1360 bytes for a total of 4021391
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1296 bytes for a total of 4022687
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 4023871
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 4025023
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1104 bytes for a total of 4026127
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4027359
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 2032 bytes for a total of 4029391
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1680 bytes for a total of 4031071
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1392 bytes for a total of 4032463
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1296 bytes for a total of 4033759
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 4034975
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1408 bytes for a total of 4036383
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1808 bytes for a total of 4038191
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1712 bytes for a total of 4039903
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4041167
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1296 bytes for a total of 4042463
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 4043647
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 4044831
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4046111
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 4047327
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 4048479
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1296 bytes for a total of 4049775
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 4050927
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 992 bytes for a total of 4051919
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1504 bytes for a total of 4053423
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1808 bytes for a total of 4055231
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1632 bytes for a total of 4056863
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1376 bytes for a total of 4058239
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4059503
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1136 bytes for a total of 4060639
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 4061855
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4063087
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4064255
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 992 bytes for a total of 4065247
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4066511
Dec 29 14:57:59 ubuntu server sshd[4928]: debug2: channel 0: rcvd adjust 56060
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4067743
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 2544 bytes for a total of 4070287
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1904 bytes for a total of 4072191
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1568 bytes for a total of 4073759
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 4075103
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4076351
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4077599
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4078847
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4080095
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4081343
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4082591
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4083839
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4085087
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4086335
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4087583
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1568 bytes for a total of 4089151
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1680 bytes for a total of 4090831
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1568 bytes for a total of 4092399
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1568 bytes for a total of 4093967
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 4095311
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4096559
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4097807
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4099055
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4100303
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4101551
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4102799
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4104047
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1024 bytes for a total of 4105071
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 4106415
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1664 bytes for a total of 4108079
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1616 bytes for a total of 4109695
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1200 bytes for a total of 4110895
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1552 bytes for a total of 4112447
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4113695
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 992 bytes for a total of 4114687
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1072 bytes for a total of 4115759
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1104 bytes for a total of 4116863
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4118031
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4119279
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1424 bytes for a total of 4120703
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4121935
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4123167
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4124399
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1600 bytes for a total of 4125999
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1680 bytes for a total of 4127679
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1488 bytes for a total of 4129167
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1328 bytes for a total of 4130495
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4131775
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 4132991
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1200 bytes for a total of 4134191
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4135423
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4136671
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 4137887
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4139135
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1200 bytes for a total of 4140335
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4141503
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1312 bytes for a total of 4142815
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1312 bytes for a total of 4144127
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1728 bytes for a total of 4145855
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1568 bytes for a total of 4147423
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1392 bytes for a total of 4148815
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 4150159
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4151391
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 4152607
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4153855
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4155103
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4156351
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4157599
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4158831
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4160079
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4161327
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1680 bytes for a total of 4163007
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1680 bytes for a total of 4164687
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1568 bytes for a total of 4166255
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4167503
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 4168847
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 4170063
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4171343
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 4172559
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4173727
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4174975
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 4176159
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4177407
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4178655
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1488 bytes for a total of 4180143
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1792 bytes for a total of 4181935
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1552 bytes for a total of 4183487
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1024 bytes for a total of 4184511
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4185759
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4187007
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4188255
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4189503
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4190751
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4191999
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1200 bytes for a total of 4193199
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4194463
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4195695
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1408 bytes for a total of 4197103
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1696 bytes for a total of 4198799
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1648 bytes for a total of 4200447
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1296 bytes for a total of 4201743
Dec 29 14:57:59 ubuntu server sshd[4928]: debug2: channel 0: rcvd adjust 54124
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1456 bytes for a total of 4203199
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 2384 bytes for a total of 4205583
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1456 bytes for a total of 4207039
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1296 bytes for a total of 4208335
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1200 bytes for a total of 4209535
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 4210719
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4211967
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1792 bytes for a total of 4213759
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1680 bytes for a total of 4215439
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1680 bytes for a total of 4217119
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1792 bytes for a total of 4218911
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1296 bytes for a total of 4220207
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4221471
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4222703
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1072 bytes for a total of 4223775
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4225023
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1200 bytes for a total of 4226223
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4227471
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1200 bytes for a total of 4228671
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4229919
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 4231135
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1392 bytes for a total of 4232527
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1584 bytes for a total of 4234111
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1744 bytes for a total of 4235855
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4237103
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4238367
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1296 bytes for a total of 4239663
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4240927
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4242159
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4243327
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4244591
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 4245775
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4247023
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 4248207
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4249439
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4250607
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1680 bytes for a total of 4252287
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1616 bytes for a total of 4253903
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1584 bytes for a total of 4255487
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1312 bytes for a total of 4256799
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4258063
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1296 bytes for a total of 4259359
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4260623
Dec 29 14:57:59 ubuntu server sshd[4928]: debug2: channel 0: rcvd adjust 56545
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4261887
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 2176 bytes for a total of 4264063
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1376 bytes for a total of 4265439
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1328 bytes for a total of 4266767
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4268047
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1136 bytes for a total of 4269183
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1200 bytes for a total of 4270383
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1664 bytes for a total of 4272047
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1424 bytes for a total of 4273471
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 4274687
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1328 bytes for a total of 4276015
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 4277231
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4278511
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1312 bytes for a total of 4279823
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1200 bytes for a total of 4281023
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 4282207
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1200 bytes for a total of 4283407
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4284639
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4285871
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 4287215
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1664 bytes for a total of 4288879
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1664 bytes for a total of 4290543
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1504 bytes for a total of 4292047
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4293311
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1328 bytes for a total of 4294639
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4295919
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4297151
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 4298303
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4299567
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1056 bytes for a total of 4300623
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 4301807
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1120 bytes for a total of 4302927
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 4304143
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1584 bytes for a total of 4305727
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1888 bytes for a total of 4307615
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1488 bytes for a total of 4309103
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4310367
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1312 bytes for a total of 4311679
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1296 bytes for a total of 4312975
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4314143
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 4315327
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4316607
Dec 29 14:57:59 ubuntu server sshd[4928]: debug2: channel 0: rcvd adjust 56055
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4317871
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 2208 bytes for a total of 4320079
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1456 bytes for a total of 4321535
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1456 bytes for a total of 4322991
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1424 bytes for a total of 4324415
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1824 bytes for a total of 4326239
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1408 bytes for a total of 4327647
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1136 bytes for a total of 4328783
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4330047
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 4331231
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4332479
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 4333695
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 4334879
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1200 bytes for a total of 4336079
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4337311
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 4338527
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1104 bytes for a total of 4339631
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 4340847
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1648 bytes for a total of 4342495
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1648 bytes for a total of 4344143
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1328 bytes for a total of 4345471
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 4346687
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 4347903
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1328 bytes for a total of 4349231
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1120 bytes for a total of 4350351
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4351583
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4352815
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4354047
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4355279
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4356511
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1664 bytes for a total of 4358175
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1664 bytes for a total of 4359839
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1552 bytes for a total of 4361391
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 4362735
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4363967
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4365199
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4366431
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4367663
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4368895
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4370127
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4371359
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4372591
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4373823
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1456 bytes for a total of 4375279
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1872 bytes for a total of 4377151
Dec 29 14:57:59 ubuntu server sshd[4928]: debug2: channel 0: rcvd adjust 55393
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1664 bytes for a total of 4378815
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 2096 bytes for a total of 4380911
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1328 bytes for a total of 4382239
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4383471
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4384719
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4385967
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4387231
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1136 bytes for a total of 4388367
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4389615
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 4390799
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1424 bytes for a total of 4392223
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1696 bytes for a total of 4393919
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1456 bytes for a total of 4395375
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1296 bytes for a total of 4396671
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1856 bytes for a total of 4398527
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1408 bytes for a total of 4399935
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4401199
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1200 bytes for a total of 4402399
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1296 bytes for a total of 4403695
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 4404911
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4406191
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 4407343
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 4408559
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1776 bytes for a total of 4410335
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1632 bytes for a total of 4411967
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1472 bytes for a total of 4413439
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1328 bytes for a total of 4414767
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4416047
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4417279
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4418543
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1056 bytes for a total of 4419599
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 944 bytes for a total of 4420543
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4421791
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 4423007
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 736 bytes for a total of 4423743
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1136 bytes for a total of 4424879
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1520 bytes for a total of 4426399
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1664 bytes for a total of 4428063
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1648 bytes for a total of 4429711
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1312 bytes for a total of 4431023
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4432287
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 4433503
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1504 bytes for a total of 4435007
Dec 29 14:57:59 ubuntu server sshd[4928]: debug2: channel 0: rcvd adjust 55579
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1440 bytes for a total of 4436447
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 2144 bytes for a total of 4438591
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1408 bytes for a total of 4439999
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4441279
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4442527
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1728 bytes for a total of 4444255
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1712 bytes for a total of 4445967
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1408 bytes for a total of 4447375
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1360 bytes for a total of 4448735
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4449999
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4451167
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4452399
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1120 bytes for a total of 4453519
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4454783
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4456031
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4457199
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1088 bytes for a total of 4458287
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1040 bytes for a total of 4459327
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1120 bytes for a total of 4460447
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4461679
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1440 bytes for a total of 4463119
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1536 bytes for a total of 4464655
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1648 bytes for a total of 4466303
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1376 bytes for a total of 4467679
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1456 bytes for a total of 4469135
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1312 bytes for a total of 4470447
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1200 bytes for a total of 4471647
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1296 bytes for a total of 4472943
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4474207
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1120 bytes for a total of 4475327
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1312 bytes for a total of 4476639
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 4477791
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4479039
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4480319
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 4481471
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1328 bytes for a total of 4482799
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1808 bytes for a total of 4484607
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1632 bytes for a total of 4486239
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 4487583
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4488815
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1440 bytes for a total of 4490255
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4491487
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1440 bytes for a total of 4492927
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4494159
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4495391
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4496623
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4497855
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 4499199
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1552 bytes for a total of 4500751
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1664 bytes for a total of 4502415
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1440 bytes for a total of 4503855
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 4505199
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4506431
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4507663
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4508943
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4510191
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1104 bytes for a total of 4511295
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 944 bytes for a total of 4512239
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4513471
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1184 bytes for a total of 4514655
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4515903
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1120 bytes for a total of 4517023
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4518271
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1568 bytes for a total of 4519839
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1776 bytes for a total of 4521615
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1440 bytes for a total of 4523055
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 4524399
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4525631
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4526863
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4528095
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4529327
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4530559
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1120 bytes for a total of 4531679
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4532911
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4534143
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1120 bytes for a total of 4535263
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1136 bytes for a total of 4536399
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1552 bytes for a total of 4537951
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1664 bytes for a total of 4539615
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1456 bytes for a total of 4541071
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4542303
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 4543647
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4544879
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4546111
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4547343
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 4548687
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4549919
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4551151
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4552383
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4553615
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1472 bytes for a total of 4555087
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1792 bytes for a total of 4556879
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1584 bytes for a total of 4558463
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4559727
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1488 bytes for a total of 4561215
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 4562559
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4563807
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4565055
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4566303
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 4567455
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1136 bytes for a total of 4568591
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 4569807
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4571087
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 4572303
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4573471
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1024 bytes for a total of 4574495
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1648 bytes for a total of 4576143
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1376 bytes for a total of 4577519
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1392 bytes for a total of 4578911
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1328 bytes for a total of 4580239
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1744 bytes for a total of 4581983
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1520 bytes for a total of 4583503
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1216 bytes for a total of 4584719
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1344 bytes for a total of 4586063
Dec 29 14:57:59 ubuntu server sshd[4928]: debug2: channel 0: rcvd adjust 54833
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1392 bytes for a total of 4587455
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 2080 bytes for a total of 4589535
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1776 bytes for a total of 4591311
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1840 bytes for a total of 4593151
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1392 bytes for a total of 4594543
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1392 bytes for a total of 4595935
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4597215
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4598479
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 4599631
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4600911
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4602079
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4603359
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4604527
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 4605679
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1392 bytes for a total of 4607071
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4608351
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4609519
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1712 bytes for a total of 4611231
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1616 bytes for a total of 4612847
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1376 bytes for a total of 4614223
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1392 bytes for a total of 4615615
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4616895
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4618159
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4619327
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4620607
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4621775
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4622943
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4624223
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 4625375
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4626543
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4627823
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4628991
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1488 bytes for a total of 4630479
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4631759
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4632927
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4634191
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4635471
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4636751
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4637919
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 4639071
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1392 bytes for a total of 4640463
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1616 bytes for a total of 4642079
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1728 bytes for a total of 4643807
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4645087
Dec 29 14:57:59 ubuntu server sshd[4928]: debug2: channel 0: rcvd adjust 55545
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1392 bytes for a total of 4646479
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 2176 bytes for a total of 4648655
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1392 bytes for a total of 4650047
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4651311
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4652591
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4653759
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1056 bytes for a total of 4654815
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4656079
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4657247
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1392 bytes for a total of 4658639
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4659807
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1376 bytes for a total of 4661183
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1840 bytes for a total of 4663023
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1616 bytes for a total of 4664639
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1392 bytes for a total of 4666031
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1376 bytes for a total of 4667407
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4668687
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4669967
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4671135
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4672399
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4673679
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1952 bytes for a total of 4675631
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1840 bytes for a total of 4677471
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1392 bytes for a total of 4678863
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4680143
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4681423
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1600 bytes for a total of 4683023
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1504 bytes for a total of 4684527
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4685807
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4687087
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1600 bytes for a total of 4688687
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4689967
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4691199
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4692431
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4693695
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 4694847
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 944 bytes for a total of 4695791
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4697055
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1056 bytes for a total of 4698111
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 4699263
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4700431
Dec 29 14:57:59 ubuntu server sshd[4928]: debug2: channel 0: rcvd adjust 56471
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1376 bytes for a total of 4701807
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 2704 bytes for a total of 4704511
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1936 bytes for a total of 4706447
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1392 bytes for a total of 4707839
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4709103
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4710383
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4711647
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4712815
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4714079
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4715247
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4716511
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4717791
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4718959
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4720127
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1488 bytes for a total of 4721615
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1600 bytes for a total of 4723215
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1952 bytes for a total of 4725167
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1488 bytes for a total of 4726655
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4727935
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4729215
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4730495
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4731775
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4732943
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 816 bytes for a total of 4733759
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4734927
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 944 bytes for a total of 4735871
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4737039
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1392 bytes for a total of 4738431
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1728 bytes for a total of 4740159
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1600 bytes for a total of 4741759
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1504 bytes for a total of 4743263
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1392 bytes for a total of 4744655
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4745935
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4747215
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4748383
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4749663
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4750927
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 4752079
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 4753231
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4754511
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4755679
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1376 bytes for a total of 4757055
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1504 bytes for a total of 4758559
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1840 bytes for a total of 4760399
Dec 29 14:57:59 ubuntu server sshd[4928]: debug2: channel 0: rcvd adjust 54826
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1568 bytes for a total of 4761967
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 2160 bytes for a total of 4764127
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1424 bytes for a total of 4765551
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1328 bytes for a total of 4766879
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1952 bytes for a total of 4768831
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1248 bytes for a total of 4770079
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4771359
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1232 bytes for a total of 4772591
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4773855
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4775119
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4776287
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1824 bytes for a total of 4778111
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1376 bytes for a total of 4779487
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1504 bytes for a total of 4780991
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4782255
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4783535
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4784815
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4786095
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 4787247
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4788527
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4789695
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1056 bytes for a total of 4790751
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4792031
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4793199
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1616 bytes for a total of 4794815
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1616 bytes for a total of 4796431
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1616 bytes for a total of 4798047
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1376 bytes for a total of 4799423
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1504 bytes for a total of 4800927
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4802207
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4803487
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4804751
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4806031
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4807311
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4808479
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 4809631
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4810911
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4812191
Dec 29 14:57:59 ubuntu server sshd[4928]: debug2: channel 0: rcvd adjust 54918
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1504 bytes for a total of 4813695
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 2496 bytes for a total of 4816191
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1504 bytes for a total of 4817695
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1616 bytes for a total of 4819311
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1376 bytes for a total of 4820687
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4821967
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4823247
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4824415
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4825695
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4826975
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4828143
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4829311
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4830591
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4831855
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1616 bytes for a total of 4833471
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1616 bytes for a total of 4835087
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1392 bytes for a total of 4836479
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1376 bytes for a total of 4837855
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1392 bytes for a total of 4839247
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4840527
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4841791
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4842959
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4844239
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4845407
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4846687
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 4847839
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4849119
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4850287
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1600 bytes for a total of 4851887
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1712 bytes for a total of 4853599
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1616 bytes for a total of 4855215
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4856495
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4857663
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4858943
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4860223
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1392 bytes for a total of 4861615
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4862895
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4864063
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4865343
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1152 bytes for a total of 4866495
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4867775
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1616 bytes for a total of 4869391
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1712 bytes for a total of 4871103
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1504 bytes for a total of 4872607
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1392 bytes for a total of 4873999
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4875279
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4876543
Dec 29 14:57:59 ubuntu server sshd[4928]: debug2: channel 0: rcvd adjust 55819
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4877823
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 2048 bytes for a total of 4879871
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1376 bytes for a total of 4881247
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1280 bytes for a total of 4882527
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1264 bytes for a total of 4883791
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4884959
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1376 bytes for a total of 4886335
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1616 bytes for a total of 4887951
Dec 29 14:57:59 ubuntu server sshd[4928]: debug3: Wrote 1168 bytes for a total of 4889119
```

---

### Post by niels_linux_forum on 2010-12-30
I solved the problem by rebooting my system.
Apparently my mac was running an ssh-agent who was catching the password, so the server never saw the password. 
So it failed authentication.

---

