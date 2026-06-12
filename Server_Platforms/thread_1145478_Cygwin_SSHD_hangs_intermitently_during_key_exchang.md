---
title: "Cygwin SSHD hangs intermitently during key exchange authentication"
date: 2009-05-01
forum: Server Platforms
---

### Post by Deepu84 on 2009-05-01
Hi,

When I try to log into the Cygwin SSHD server, it intermitently locks
up and I have to kill the connection and try again. I have a scheduled
task running which connects to the server every 10 minutes to
synchronize files and this causes problems over time.

Client
--------
C:\Program Files\Unison>ssh -v Chloe@dumbopc ls
OpenSSH_5.1p1, OpenSSL 0.9.8j 07 Jan 2009
debug1: Connecting to dumbopc [192.168.16.99] port 22.
debug1: Connection established.
debug1: identity file /cygdrive/c/Documents and Settings/slim/.ssh/identity type
 -1
debug1: identity file /cygdrive/c/Documents and Settings/slim/.ssh/id_rsa type -
1
debug1: identity file /cygdrive/c/Documents and Settings/slim/.ssh/id_dsa type -
1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1
debug1: match: OpenSSH_5.1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'dumbopc' is known and matches the RSA host key.
debug1: Found key in /cygdrive/c/Documents and Settings/slim/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password,keyboard-interacti
ve
debug1: Next authentication method: publickey
debug1: Trying private key: /cygdrive/c/Documents and Settings/slim/.ssh/identit
y
debug1: Trying private key: /cygdrive/c/Documents and Settings/slim/.ssh/id_rsa
debug1: read PEM private key done: type RSA
debug1: Authentication succeeded (publickey).
debug1: channel 0: new [client-session]
debug1: Requesting [EMAIL="no-more-sessions@openssh.com"]no-more-sessions@openssh.com[/EMAIL]
debug1: Entering interactive session.
[hangs here]


Server
---------
$ /usr/sbin/sshd -d -e
debug1: sshd version OpenSSH_5.1p1
debug1: read PEM private key done: type RSA
debug1: private host key: #0 type 1 RSA
debug1: read PEM private key done: type DSA
debug1: private host key: #1 type 2 DSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-d'
debug1: rexec_argv[2]='-e'
debug1: Bind to port 22 on 0.0.0.0.
Server listening on 0.0.0.0 port 22.
debug1: fd 4 clearing O_NONBLOCK
debug1: Server will not fork when running in debugging mode.
debug1: rexec start in 4 out 4 newsock 4 pipe -1 sock 7
debug1: sshd version OpenSSH_5.1p1
debug1: read PEM private key done: type RSA
debug1: private host key: #0 type 1 RSA
debug1: read PEM private key done: type DSA
debug1: private host key: #1 type 2 DSA
debug1: inetd sockets after dupping: 3, 3
Connection from 192.168.16.103 port 4421
debug1: Client protocol version 2.0; client software version OpenSSH_5.1
debug1: match: OpenSSH_5.1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1
debug1: list_hostkey_types: ssh-rsa,ssh-dss
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST received
debug1: SSH2_MSG_KEX_DH_GEX_GROUP sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_INIT
debug1: SSH2_MSG_KEX_DH_GEX_REPLY sent
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: KEX done
debug1: userauth-request for user Chloe service ssh-connection method none
debug1: attempt 0 failures 0
Failed none for Chloe from 192.168.16.103 port 4421 ssh2
debug1: userauth-request for user Chloe service ssh-connection method publickey
debug1: attempt 1 failures 0
debug1: temporarily_use_uid: 1004/513 (e=1004/513)
debug1: trying public key file /home/Chloe/.ssh/authorized_keys
debug1: fd 4 clearing O_NONBLOCK
debug1: matching key found: file /home/Chloe/.ssh/authorized_keys, line 2
Found matching RSA key: 43:b1:df:5c:66:e6:ae:18:30:72:40:af:3e:0a:9d:e5
debug1: restore_uid: 1004/513
debug1: ssh_rsa_verify: signature correct
Accepted publickey for Chloe from 192.168.16.103 port 4421 ssh2
debug1: monitor_child_preauth: Chloe has been authenticated by privileged proces
s
debug1: Entering interactive session for SSH2.
debug1: server_init_dispatch_20
[just hangs here]



Key Exchange Scenario
-----------------------------------
I don't know anything about key exchanges, but notice the server
received the 1st key exchange KEXINIT, the client sent a 2nd key
exchange (GEX_REQUEST) and the server doesn't recognize it nor
respond.

Server
---------
$ /usr/sbin/sshd -ddde
debug2: load_server_config: filename /etc/sshd_config
debug2: load_server_config: done config len = 213
debug2: parse_server_config: config /etc/sshd_config len 213
debug3: /etc/sshd_config:13 setting Port 22
debug3: /etc/sshd_config:21 setting Protocol 2
debug3: /etc/sshd_config:42 setting StrictModes no
debug3: /etc/sshd_config:98 setting UsePrivilegeSeparation yes
debug3: /etc/sshd_config:113 setting Subsystem sftp     /usr/sbin/sftp-server
debug1: sshd version OpenSSH_5.1p1
debug3: Not a RSA1 key file /etc/ssh_host_rsa_key.
debug1: read PEM private key done: type RSA
debug1: private host key: #0 type 1 RSA
debug3: Not a RSA1 key file /etc/ssh_host_dsa_key.
debug1: read PEM private key done: type DSA
debug1: private host key: #1 type 2 DSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-ddde'
debug2: fd 3 setting O_NONBLOCK
debug1: Bind to port 22 on 0.0.0.0.
Server listening on 0.0.0.0 port 22.
debug1: fd 4 clearing O_NONBLOCK
debug1: Server will not fork when running in debugging mode.
debug3: send_rexec_state: entering fd = 7 config len 213
debug3: ssh_msg_send: type 0
debug3: send_rexec_state: done
debug1: rexec start in 4 out 4 newsock 4 pipe -1 sock 7
debug3: recv_rexec_state: entering fd = 5
debug3: ssh_msg_recv entering
debug3: recv_rexec_state: done
debug2: parse_server_config: config rexec len 213
debug3: rexec:13 setting Port 22
debug3: rexec:21 setting Protocol 2
debug3: rexec:42 setting StrictModes no
debug3: rexec:98 setting UsePrivilegeSeparation yes
debug3: rexec:113 setting Subsystem sftp        /usr/sbin/sftp-server
debug1: sshd version OpenSSH_5.1p1
debug3: Not a RSA1 key file /etc/ssh_host_rsa_key.
debug1: read PEM private key done: type RSA
debug1: private host key: #0 type 1 RSA
debug3: Not a RSA1 key file /etc/ssh_host_dsa_key.
debug1: read PEM private key done: type DSA
debug1: private host key: #1 type 2 DSA
debug1: inetd sockets after dupping: 3, 3
Connection from 192.168.16.103 port 1266
debug1: Client protocol version 2.0; client software version OpenSSH_5.1
debug1: match: OpenSSH_5.1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1
debug2: fd 3 setting O_NONBLOCK
debug2: Network child is on pid 5236
debug1: list_hostkey_types: ssh-rsa,ssh-dss
debug3: preauth child monitor started
debug1: SSH2_MSG_KEXINIT sent
debug3: mm_request_receive entering


Client
---------
C:\Program Files\Unison>ssh -v Chloe@dumbopc ls
OpenSSH_5.1p1, OpenSSL 0.9.8j 07 Jan 2009
debug1: Connecting to dumbopc [192.168.16.99] port 22.
debug1: Connection established.
debug1: identity file /cygdrive/c/Documents and Settings/slim/.ssh/identity type
 -1
debug1: identity file /cygdrive/c/Documents and Settings/slim/.ssh/id_rsa type -
1
debug1: identity file /cygdrive/c/Documents and Settings/slim/.ssh/id_dsa type -
1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1
debug1: match: OpenSSH_5.1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP



$ ps -ef
     UID     PID    PPID TTY     STIME COMMAND
   Chloe    3916       1   0    Apr 30 /usr/bin/bash
  SYSTEM    2832       1   ?  22:30:12 /usr/sbin/sshd
  SYSTEM    3328       1   ?  23:00:12 /usr/sbin/sshd
  SYSTEM     712       1   ?  23:10:12 /usr/sbin/sshd
  SYSTEM    4252       1   ?  23:20:12 /usr/sbin/sshd
  SYSTEM    4528       1   ?  23:30:12 /usr/sbin/sshd
  SYSTEM    6044       1   ?  23:40:12 /usr/sbin/sshd
  SYSTEM    5084       1   ?  00:10:15 /usr/sbin/sshd
  SYSTEM    6020       1   ?  00:10:21 /usr/sbin/sshd
  SYSTEM    4048       1   ?  00:20:12 /usr/sbin/sshd
  SYSTEM    4300       1   ?  00:30:12 /usr/sbin/sshd
  SYSTEM    5124       1   ?  01:40:12 /usr/sbin/sshd
  SYSTEM    4368       1   ?  01:50:13 /usr/sbin/sshd
  SYSTEM    5628       1   ?  01:58:02 /usr/sbin/sshd
  SYSTEM    5564       1   ?  02:00:04 /usr/sbin/sshd
  SYSTEM    4996       1   ?  02:00:13 /usr/sbin/sshd
  SYSTEM    2840       1   ?  02:10:13 /usr/sbin/sshd
   Chloe    5524    3916   0  02:25:41 /usr/bin/ps

---

